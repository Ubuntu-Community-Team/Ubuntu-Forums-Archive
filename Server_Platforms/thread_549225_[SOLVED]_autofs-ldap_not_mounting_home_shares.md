---
title: "[SOLVED] autofs-ldap not mounting home shares"
date: 2007-09-12
forum: Server Platforms
---

### Post by Krusty Ruffle on 2007-09-12
Background: I'm building a server to take care of central login information, etc in my home. I have to maintain a mixed windows/linux environment. So far I have LDAP taking care of logon information with samba for the windows machines. I am able to join the windows machines to the domain and logons work fine there, (though the Default User profile is not being used, but that is a different issue). On Linux machines, I am able to use the LDAP server to get logon information, but I cannot get it to automount the home directories.

I have followed the [autofs-LDAP page at help.ubuntu.com]("https://help.ubuntu.com/community/AutofsLDAP") but I see the following problems, all of which are on the client machine:

during boot up I get: 
> Starting automounter: loading autofs4 kernel module, no automount maps defined.

If I do ```
sudo /etc/init.d/autofs reload
``` I get:
> Reloading automounter: checking for changes ... 
Started automounter: /home

and with  ```
cat /var/log/syslog | grep auto
``` I get:
> automount[6371]: lookup(ldap): query failed for (objectclass=nisObject): No such object
automount[6371]: lookup(ldap): query failed for (objectclass=automount): No such object
automount[6371]: failed to load map, exiting

```
ldapsearch -x
``` from the same machine gives me, (this is trimmed down and names have been editted etc..):
> # extended LDIF
#
# LDAPv3
# base <> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# mydomain.name
dn: dc=mydomain,dc=name
objectClass: top
objectClass: dcObject
objectClass: organization
o: Fake Company Name
dc: mydomain

# admin, mydomain.name
dn: cn=admin,dc=mydomain,dc=name
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator

<=-SNIP-=>

# firstname, Users, mydomain.name
dn: uid=firstname,ou=Users,dc=mydomain,dc=name
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: sambaSamAccount
objectClass: inetLocalMailRecipient
cn: firstname
sn: firstname
givenName: firstname
uid: firstname
uidNumber: 1000
gidNumber: 513
homeDirectory: /home/firstname
loginShell: /bin/bash
gecos: firstname lastname
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
displayName: firstname lastname
sambaSID: S-1-5-21-682434482-3196215736-3921645463-3000
sambaLogonScript: logon.bat
sambaPrimaryGroupSID: S-1-5-21-682434482-3196215736-3921645463-513
sambaHomeDrive: Y:
mailLocalAddress: firstname.lastname
mail: [email]firstname.lastname@mydomain.name[/email]
sambaAcctFlags: [U]
sambaPwdLastSet: 1189385161
sambaPwdMustChange: 1193273161

<-=SNIP=->

# admin, mydomain.name
dn: ou=admin,dc=mydomain,dc=name
ou: admin
objectClass: top
objectClass: organizationalUnit

# automount, admin, mydomain.name
dn: ou=automount,ou=admin,dc=mydomain,dc=name
ou: automount
objectClass: top
objectClass: organizationalUnit

# auto.master, automount, admin, mydomain.name
dn: ou=auto.master,ou=automount,ou=admin,dc=mydomain,dc=name
ou: auto.master
objectClass: top
objectClass: automountMap

# /home, auto.master, automount, admin, mydomain.name
dn: cn=/home,ou=auto.master,ou=automount,ou=admin,dc=mydomain,dc=name
cn: /home
objectClass: top
objectClass: automount
automountInformation: ldap:ou=auto.home,ou=automount,ou=
 admin,dc=example,dc=com --timeout=60 --ghost

# firstname, auto.home, automount, admin, mydomain.name
dn: cn=firstname,ou=auto.home,ou=automount,ou=admin,dc=mydomain,dc=name
cn: firstname
objectClass: top
objectClass: automount
automountInformation: -fstype=nfs,rw,hard,intr,nodev,exec,nosuid,rsize=8192,ws
 ize=8192 nfs.mydomain.name:/home/firstname

I've been searching the net for several days trying to resolve this, any help is greatly appreciated...

---

### Post by Krusty Ruffle on 2007-09-13
Okay, I figured this out.
First I added the home directories to the /etc/exports file, then I backed up the ldap database with ```
ldapsearch -x >> ldap.ldif
``` Then I wiped out the entire database with ```
sudo rm /var/lib/ldap/*db
``` Restarted the server with:```
sudo /etc/init.d/slapd restart
```Edited the ldap.ldif file I had just created to take out the automount related stuff I posted in the preivious post and added the following, (using the propper domain/user names, etc...):```
# auto.master, mydomain.name
dn: ou=auto.master,dc=mydomain,dc=name
objectClass: top
objectClass: automountMap
ou: auto.master

# /home, auto.master, mydomain.name
dn: cn=/home,ou=auto.master,dc=mydomain,dc=name
objectClass: automount
cn: /home
automountInformation: ldap ldap.mydomain.name:ou=auto.home,dc=mydomain,dc=name

# auto.home, mydomain.name
dn: ou=auto.home,dc=mydomain,dc=name
objectClass: top
objectClass: automountMap
ou: auto.home

# loginname, auto.home, mydomain.name
dn: cn=loginname,ou=auto.home,dc=mydomain,dc=name
objectClass: automount
cn: loginname
automountInformation: -fstype=nfs,hard,intr,nodev,nosuid nfs.mydomain.name:/home/loginname
```And used ldapadd to import the .ldap.ldif file and now it works!!

Note: I did have to enable the rootdn and rootpw in /ets/ldap/slapd.conf to get past some authentication errors before I could do re-enter the information into the database, then I had to fix all of the user passwords and stuff, but that was all stuff I already learned how to do before I could even get this far....

---

### Post by masum_habib on 2008-06-03
Hi Guys,

Thanks for the post. It helped me a lot.

But just one more thing to make clear:

```
#/home, auto.master, mydomain.name
dn: cn=/home,ou=auto.master,dc=mydomain,dc=name
objectClass: automount
cn: /home
[B]automountInformation: ldap ldap.mydomain.name:ou=auto.home,dc=mydomain,dc=name
[/B]

```

The bold faced line above actually should be:

```
automountInformation: ldap**://**ldap.mydomain.name**/**ou=auto.home,dc=mydomain,dc=name

```

Where ldap.mydomain.name is your LDAP server and it may be a static IP address such as:

```
automountInformation: ldap://192.168.20.2/ou=auto.home,dc=mydomain,dc=name

```


Please don't forget the **ldap://**whatevre-may-be**/** part, otherwise your configuration may not work every where such as Scientific Linux 5 which was my case.

It works fine both in SL 5 and Kubuntu Hardy. Thanks again for the post.

--Masum Habib
URL [http://teacher.buet.ac.bd/masum_habib](http://teacher.buet.ac.bd/masum_habib)

---

### Post by WeyOh on 2008-06-03
Hi,

I'm trying to mount home directories and having the auto.home and auto.master in the ldap tree. I can login as a ldap user and I am able to mount manually the home folder. When I login a home directory is created in the location I set in the ldap tree under the user. What I am wondering is where can I look for information as to what is wrong? As in is there any log that might be able to provide information as to what is wrong? Thanks for your help!

---

### Post by masum_habib on 2008-06-04
Hi WeyOh,
I am not an expert or something in Linux but I learn something that I want to share. The following command on Kubuntu, which is one of my workstations, helped me a lot:

```
sudo /etc/init.d/autofs status
```

It tells me the following

```
Configured Mount Points:
------------------------
/usr/sbin/automount --timout=300 /vhome ldap://192.168.93.199/ou=auto,vhome,dc=domain,dc=com

Active Mount Points:
----------------------
/usr/sbin/automount --pid-file=/var/run/autofs/_vhome.pid --timount=300 /vhome ldap://192.168.93.199/ou=auto.home,dc=domain,dc=com

```

where 192.168.93.199 is my LDAP server, /vhome is the directory where my LDAP users' home directory are mounted.

Please note that I faced a problem with mounting the home directories on /home because (I guess) my /home was on a separate partition.

--Masum Habib

---

### Post by WeyOh on 2008-06-06
Thanks for your reply, I had a look and effectively I don't have my mount point in the configured mount point list. I don't know what to do. I followed everything that was said above. As I said earlier I can login perfectly but I am running into trouble when I have to mount the directory. Any suggestions? Any data that I could post to give you guys an idea of the problem? Thanks!

---

### Post by WeyOh on 2008-06-07
Ok, so after a lot of playing I came accross something weird, when I do:
```
sh -x /etc/init.d/autofs start
```
After some configuration settings I get this
```
/etc/init.d/autofs: 122: Syntax error: "(" unexpected

```
Which corresponds to
```
function getschemes()
{
	SOURCES=`grep ^automount: /etc/nsswitch.conf | \
		 sed -e 's/^.*://' -e 's/\[.*\]/ /g'`

	if [ `echo $SOURCES | awk '{print NF}'` -gt 0 ]
	then
		echo ${SOURCES}
	else
		echo files
	fi
}
```
I have no clue what to do now. Any ideas?

---

### Post by jeepers58 on 2008-07-06
> **WeyOh said:**
> Ok, so after a lot of playing I came accross something weird, when I do:
```
sh -x /etc/init.d/autofs start
```
After some configuration settings I get this
```
/etc/init.d/autofs: 122: Syntax error: "(" unexpected

```
Which corresponds to
```
function getschemes()
{
	SOURCES=`grep ^automount: /etc/nsswitch.conf | \
		 sed -e 's/^.*://' -e 's/\[.*\]/ /g'`

	if [ `echo $SOURCES | awk '{print NF}'` -gt 0 ]
	then
		echo ${SOURCES}
	else
		echo files
	fi
}
```
I have no clue what to do now. Any ideas?

Hi, while I am still having problems with mounting an auto.direct map. I do have a answer for the problem above. The problem is a syntax error when defining the functions in the shell script. The author of the shell script uses 

   function getschemes () 

I think that is a perl syntax, it ain't shell. The correct syntax is 

   getschemes () 

there were 15 functions called like this in the shell script by my count. You will need to edit the script and correct the syntax error for each funcion. I would recommend you make a copy of the original script before you start editing in case you get confused and need to start over from the beginning. 

If you know a little bit about vi this should do it from the ex command line

:%s/^function //

I am still having issues with the auto.direct map, but this should cure the error you were describing.

-mike

---

