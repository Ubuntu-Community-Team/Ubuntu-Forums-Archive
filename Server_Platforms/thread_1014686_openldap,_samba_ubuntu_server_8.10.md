---
title: "openldap, samba ubuntu server 8.10"
date: 2008-12-18
forum: Server Platforms
---

### Post by ntenzpunishment on 2008-12-18
Hi there,

I know there are topics about openldap, samba etc but didnt find the answers im looking for. I used this guide: OpenLDAP + Samba Domain Controller, [http://www.howtoforge.org/openldap-samba-domain-controller-ubuntu7.10-p3](http://www.howtoforge.org/openldap-samba-domain-controller-ubuntu7.10-p3) On Ubuntu 7.10, but unfortunatly there are some differences because im running ubuntu server 8.10

First of all this is not accurate:

# We need to configure OpenLDAP now.
dpkg-reconfigure slapd

# Answer the on-screen prompts with:

No
DNS domain name: example.local
Name of your organization: example.local
Admin password: 12345
Confirm password: 12345
OK
BDB
No
Yes
No

The menu is not in the same order (so i choose default)

Second: I dont have the slapd.conf so I cant add the schema but I did try this guide: [https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

root@dc01-ubuntu:~# slaptest -f schema_convert.conf -F /tmp/ldif_output
/etc/ldap/schema/samba.schema: line 496 objectclass: AttributeType not found: "displayName"
slaptest: bad configuration directory!


root@dc01-ubuntu:~# ls -lrt /etc/ldap/schema/
total 184
-rw-r--r-- 1 root root  3591 2008-10-25 02:36 README
-rw-r--r-- 1 root root  3393 2008-10-25 02:36 openldap.ldif
-rw-r--r-- 1 root root  6889 2008-10-25 02:36 nis.ldif
-rw-r--r-- 1 root root  1343 2008-10-25 02:36 misc.ldif
-rw-r--r-- 1 root root  3571 2008-10-25 02:36 inetorgperson.ldif
-rw-r--r-- 1 root root 14030 2008-10-25 02:36 cosine.schema
-rw-r--r-- 1 root root 12089 2008-10-25 02:36 cosine.ldif
-rw-r--r-- 1 root root 20346 2008-10-25 02:36 core.schema
-rw-r--r-- 1 root root 21175 2008-10-25 02:36 core.ldif
-rw-r--r-- 1 root root  2084 2008-10-25 02:36 corba.schema
-rw-r--r-- 1 root root  2180 2008-10-25 02:36 collective.schema
-rw-r--r-- 1 root root  4678 2008-10-25 02:36 ppolicy.schema
-rw-r--r-- 1 root root  1602 2008-10-25 02:36 openldap.schema
-rw-r--r-- 1 root root  7723 2008-10-25 02:36 nis.schema
-rw-r--r-- 1 root root  5996 2008-10-25 02:36 nadf.schema
-rw-r--r-- 1 root root  2471 2008-10-25 02:36 misc.schema
-rw-r--r-- 1 root root  3295 2008-10-25 02:36 java.schema
-rw-r--r-- 1 root root  6360 2008-10-25 02:36 inetorgperson.schema
-rw-r--r-- 1 root root  3378 2008-10-25 02:36 dyngroup.schema
-rw-r--r-- 1 root root 10474 2008-10-25 02:36 duaconf.schema
-rw-r--r-- 1 root root 20221 2008-12-17 22:09 samba.schema


So what I learnt is that because of above I get the following error:
root@dc01-ubuntu:~# smbldap-populate -u 30000 -g 30000
Populating LDAP directory for domain DOMSMB (S-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx)
(using builtin directory structure)

entry dc=example,dc=local already exist.
entry ou=Users,dc=example,dc=local already exist.
entry ou=Groups,dc=example,dc=local already exist.
entry ou=Computers,dc=example,dc=local already exist.
entry ou=Idmap,dc=example,dc=local already exist.
adding new entry: uid=root,ou=Users,dc=example,dc=local
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 58.
adding new entry: uid=nobody,ou=Users,dc=example,dc=local
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 89.
adding new entry: cn=Domain Admins,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 101.
adding new entry: cn=Domain Users,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 112.
adding new entry: cn=Domain Guests,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 123.
adding new entry: cn=Domain Computers,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 134.
adding new entry: cn=Administrators,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 179.
adding new entry: cn=Account Operators,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 201.
adding new entry: cn=Print Operators,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 212.
adding new entry: cn=Backup Operators,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 223.
adding new entry: cn=Replicators,ou=Groups,dc=example,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 234.
adding new entry: sambaDomainName=DOMSMB,dc=example,dc=local
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 499, <GEN1> line 242.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist


Would someone please help me out - would be greatly appreciated. I dont want to install 7.10 and ignore security issues etc.

---

### Post by BrunSOFT on 2008-12-23
i have same problems. How fix it?

---

### Post by ntenzpunishment on 2008-12-23
I have no idea - but sure hope someone does :-)

---

### Post by BrunSOFT on 2008-12-23
I hope to, but "Hope die last" =(

---

### Post by francois.mdlh on 2009-01-14
This is a HUGE problem with Ubuntu right now (or OpenLDAP, not sure which), and is preventing this great OS from becoming a serious contender in the Enterprise marketplace. Companies are moving toward the cloud more and more, and things like Google Apps, Single Sign On and online collaboration are the way of the future. 

The Ubuntu docs are severely out of date, and it is almost impossible to find all the information you need to get things working correctly. Frustrating to say the least.

As much as I HATE M$ and Windows, Server 2003 is now my only option! How can Ubuntu leave a BASIC need such as LDAP broken and useless??

epic fail.

If there is some magical guide somewhere that actually gets OpenLDAP set up correctly, please point it out and I'll retract above statements.

---

### Post by druhboruch on 2009-01-14
The server guide has been updated for intrepid:

[https://help.ubuntu.com/8.10/serverguide/C/network-authentication.html](https://help.ubuntu.com/8.10/serverguide/C/network-authentication.html)

:)

---

### Post by johnybgood11 on 2009-01-15
Hi there,

Well I got stuck in the same place... When your tutorial begins the slap.d.conf part just leave it on hold and move on to this one:

[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation)

You have to pay a bit attention 'cause you've already done some steps. After that just go back to the previous tutorial!

If I find time I'll creat a new one to reflect all of this.

Thanks in advance
João Ribeiro

---

### Post by ryanfx on 2009-01-16
> **johnybgood11 said:**
> Hi there,

Well I got stuck in the same place... When your tutorial begins the slap.d.conf part just leave it on hold and move on to this one:

[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation)

You have to pay a bit attention 'cause you've already done some steps. After that just go back to the previous tutorial!

If I find time I'll creat a new one to reflect all of this.

Thanks in advance
João Ribeiro

I tried this guide however I am getting an error when running the ldapadd command for the new schema -

ldap_bind: Server is unwilling to perform (53)
	additional info: unauthenticated bind (DN with no password) disallowed

Any ideas??

---

### Post by ryanfx on 2009-01-16
to answer my own question I found two errors with their documentation...

```

ldapadd -x -D cn=admin,cn=config -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}misc.ldif

```

was the line they provided however you need a -W flat before the -f to read 

```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}misc.ldif

```

this will prompt you for the administrator password for the ldap server

you also need to change the {12\}misc.ldif at the end to {12\}samba.ldif - misc doesn't exist!!!!

```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}samba.ldif

```

---

### Post by johnybgood11 on 2009-01-16
> **ryanfx said:**
> to answer my own question I found two errors with their documentation...

```

ldapadd -x -D cn=admin,cn=config -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}misc.ldif

```

was the line they provided however you need a -W flat before the -f to read 

```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}misc.ldif

```
this will prompt you for the administrator password for the ldap server

you also need to change the {12\}misc.ldif at the end to {12\}samba.ldif - misc doesn't exist!!!!

```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}samba.ldif

```



I forgot to mention that, I'm sorry... All is working now?

The only thing I couldn't configure was the sharing folders and definitions for windows clients authentication. So all my users are connected to domain but loggin locally!

Did you solve this? Or your domain is only for linux access?

---

### Post by ryanfx on 2009-01-16
double post

---

### Post by ryanfx on 2009-01-16
> **johnybgood11 said:**
> I forgot to mention that, I'm sorry... All is working now?

The only thing I couldn't configure was the sharing folders and definitions for windows clients authentication. So all my users are connected to domain but loggin locally!

Did you solve this? Or your domain is only for linux access?

I am stuck on another step now - when I run 

```
sudo smbldap-populate
```

I receive the error 

```

entry dc=elegant,dc=local already exist. 
adding new entry: ou=People,dc=elegant,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 12.
....
Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist

```

did you experience this?

Also, would you mind posting the output of your samba configuration script? 

```
 sudo perl /usr/share/doc/smbldap-tools/configure.pl 
```

---

### Post by johnybgood11 on 2009-01-16
> **ryanfx said:**
> I am stuck on another step now - when I run 

```
sudo smbldap-populate
```

I receive the error 

```

entry dc=elegant,dc=local already exist. 
adding new entry: ou=People,dc=elegant,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 12.
....
Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist

```

did you experience this?

Also, would you mind posting the output of your samba configuration script? 

```
 sudo perl /usr/share/doc/smbldap-tools/configure.pl 
```

Unfortunatly, I can't right now. I've done this for a client and I don't have vpn connection with me.

Have you configured Samba? I came across that it's been quite a while i think it had to do with smbpasswd. Hve you tried this:

smbpasswd -w 12345

Thanks

---

### Post by ryanfx on 2009-01-16
```

root@esiserver:/home/steve# sudo smbpasswd -w 12345
ERROR: 'ldap admin dn' not defined! Please check your smb.conf

```

perhaps I am missing something.

in this guide
[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

Did it state to configure this stuff anywhere?  I'm not new to linux but I am to samba / ldap.

or maybe I used bad names in my configure script?

---

### Post by johnybgood11 on 2009-01-16
> **ryanfx said:**
> ```

root@esiserver:/home/steve# sudo smbpasswd -w 12345
ERROR: 'ldap admin dn' not defined! Please check your smb.conf

```

perhaps I am missing something.

in this guide
[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

Did it state to configure this stuff anywhere?  I'm not new to linux but I am to samba / ldap.

or maybe I used bad names in my configure script?


Yes, I went through hell to get this done... There is almost none documentation about this issue and I promise to wirte a paper as soon as possible.

Anyway, you have to configure samba. In the link you provided there's an example. But I followed this:

[http://www.howtoforge.org/openldap-samba-domain-controller-ubuntu7.10-p2](http://www.howtoforge.org/openldap-samba-domain-controller-ubuntu7.10-p2)

Please pay attention at step 5: samb config.

After that, you should be able to set the password and proceed. Anyway, what is the porpuse of this ldap config? Windows clients based access?

---

### Post by ryanfx on 2009-01-16
yes - 

I eventually got it configured correctly, moved onto a few more steps down and ran into another error.. I just canned the whole thing at that point :lol:

I want to authenticate some windoze clients I have at home and have roaming profiles but I'm just going to avoid ldap for now... way more trouble than it's worth.

Thanks for the help anyway.

---

### Post by johnybgood11 on 2009-01-17
> **ryanfx said:**
> yes - 

I eventually got it configured correctly, moved onto a few more steps down and ran into another error.. I just canned the whole thing at that point :lol:

I want to authenticate some windoze clients I have at home and have roaming profiles but I'm just going to avoid ldap for now... way more trouble than it's worth.

Thanks for the help anyway.

May I ask which solution did you choose?? Well I got stuck on the roaming profile bits.

Hope you find your way.

João Ribeiro

---

### Post by crazycucumber on 2009-02-04
wondering if anyone has had time to test / rewrite the documentation to configure a Samba openLDAP DC on server 8.10 
The 7.10 Documentation is great except for the LDAP differences. 

I really would like to get this done , but come unstuck at the LDAP config and Samba/Ldap config.

---

### Post by johnybgood11 on 2009-02-04
Please reed this thread carefully from the first post... You'll find your answer here.

Basically you have to combine two tutrials... Please try to follow this post and if any doubt arises please contact me.

Thanks
João Ribeiro


> **crazycucumber said:**
> wondering if anyone has had time to test / rewrite the documentation to configure a Samba openLDAP DC on server 8.10 
The 7.10 Documentation is great except for the LDAP differences. 

I really would like to get this done , but come unstuck at the LDAP config and Samba/Ldap config.

---

### Post by Stretsh on 2009-02-22
> **ryanfx said:**
> ```

root@esiserver:/home/steve# sudo smbpasswd -w 12345
ERROR: 'ldap admin dn' not defined! Please check your smb.conf

```

perhaps I am missing something.

in this guide
[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

Did it state to configure this stuff anywhere?  I'm not new to linux but I am to samba / ldap.

or maybe I used bad names in my configure script?
I've got the same problem now. I can see the 'ldap admin dn' in my smbconf, so I wonder why he can't find it.
```
# LDAP Settings
   passdb backend = ldapsam:ldap://192.168.0.3
   ldap suffix = dc=aboma,dc=local
   ldap user suffix = ou=People
   ldap group suffix = ou=Groups
   ldap machine suffix = ou=Computers
   ldap idmap suffix = dc=aboma,dc=local
   **ldap admin dn = cn=admin,dc=aboma,dc=local**
#  ldap ssl = start tls
   ldap passwd sync = yes

   add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"

```
Am I missing something?

Edit: Never mind, I moved the LDAP Settings right below the 
#   passdb backend = tdbsam
restarted Samba and it worked

---

### Post by halgar on 2009-02-24
If my situation was OpenLDAP on 8.04.2 server with 8.04.2 servers as authentication clients, would I use the 8.10 documentation?  I am not using Samba.  I do plan to use NFS for a common /home.

thanks,
halgar

---

### Post by nroussi on 2009-02-27
> **johnybgood11 said:**
> Hi there,

Well I got stuck in the same place... When your tutorial begins the slap.d.conf part just leave it on hold and move on to this one:

[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation)

You have to pay a bit attention 'cause you've already done some steps. After that just go back to the previous tutorial!

If I find time I'll creat a new one to reflect all of this.

Thanks in advance
João Ribeiro

So have you found time to create a new guide? Because I am following [this guide]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html") to the letter but I get stuck.
It would be nice to have a complete guide on how to setup a domain controller with at least one version of Ubuntu.

---

### Post by promodus on 2009-02-28
Maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=843082](http://ubuntuforums.org/showthread.php?t=843082)

---

### Post by manuel78 on 2009-03-13
> **ryanfx said:**
>  
```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}misc.ldif

```


you also need to change the {12\}misc.ldif at the end to {12\}samba.ldif - misc doesn't exist!!!!
 

that's not right, pay attention!

The {12\}misc.ldif has another number in front of it,  you find it typing  "sudo ls /tmp/ldif_output/cn\=config/cn=schema" at the prompt.

p.s. i followed the official samba and ldap guide on the ubuntu site.

---

### Post by rdxdude on 2009-04-06
Hey guys thanks for the help but i am getting stuck when running this command to configure the smbldap stuff sudo perl /usr/share/doc/smbldap-tools/configure.pl.  I am getting stuck after a few questions.  I have no idea what some of the config is asking of me and i tried googling to understand some of it but really couldn't make it out.  If any one could help me that would be really appreciated.  I am kind of a newbie at this so any help would be awesome thanks.

---

### Post by patmenier on 2009-09-27
Same problem here solved by moving 

include /etc/ldap/schema/samba.schema 

**at the end of the include lines**.

---

### Post by whoop on 2009-11-07
Is it the same as this tutorial? :
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

All documentation is outdated, it needs to be up to date and complete, please **vote**:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

