---
title: "OpenLDAP Server Setup in Ubuntu 12.04 LTS"
date: 2012-05-07
forum: Server Platforms
---

### Post by ryazkhan on 2012-05-07
Hi folks, 

The new LTS version is very impressive, it equipped with all latest and greatest open source stuff ! I find that configuring any thing like samba,ldap etc.. has been made even simpler than 10.04 LTS. Ubuntu official documentation are little confusing as they always are, so don't totally relay on them and expect to have working setup, it might work or might not, anyway it did not worked for me but was main source of my references in configuring my OpenLDAP Server and setting it up for authentication. The procedure has been tested few times in virtual environment for the sake of accuracy and functionality. Currently its available on my website, I have not got enough time to write it here, I will update the thread whenever I got some extra time to spare.

[http://www.ryazkhan.net/articles/ldap12](http://www.ryazkhan.net/articles/ldap12)

---

### Post by LHammonds on 2012-05-07
Thanks for making and sharing this tutorial.

LHammonds

---

### Post by ryazkhan on 2012-05-07
> **LHammonds said:**
> Thanks for making and sharing this tutorial.

LHammonds
My pleasure ! Hope it was helpful

---

### Post by ryazkhan on 2012-05-08
Here is the tutorial as promised, its always [[COLOR="Blue"]available here[/COLOR]]("http://www.ryazkhan.net/articles/ldap12")

With the assumption that Ubuntu 12.04 LTS Server is already installed, it should work with any other version with some changes if any. No assurance that it will work for your setup, worked for me so I am sharing it

I have used dc=testlab,dc=dev as my domain, cn=admin,dc=testlab,dc=dev as my ldap admin user, and test as my password throughout this guide, please feel free to change it to your liking 
Update all packages and install updates if any
> apt-get update && apt-get upgrade -y
The base DN or suffix of ldap tree will be populated/created based on the domain name specified in /etc/hosts file, in my case it is testlab.dev	
Lets proceed with install and install following required packages
> sudo apt-get install slapd ldap-utils -y
the password would test like I mentioned in the beginning
Now lets add some logging level for ldap
nano log.ldif and paste the following in it then save the file and exit out
> 
dn: cn=config
changetype: modify
add: olcLogLevel
olcLogLevel: stats

Add the above ldif file to ldap database
> sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f log.ldif
Done, at this point we have working OpneLDAP server
Now let set it up so we can actually use it, here we are going to use it for user authentication
Install libnss-ldap package
> sudo apt-get install libnss-ldap -y
There would few questions here, answer them like following
> 
ldap://127.0.0.1
dc=testlab,dc=dev
3
Yes
No
cn=admin,dc=testlab,dc=dev
test

If you make a mistake you can try again using
> sudo dpkg-reconfigure ldap-auth-config
Now configure the LDAP profile for NSS
> sudo auth-client-config -t nss -p lac_ldapThere should not be any error, if you have some error(s) go back and check your config
Finally tell system to use ldap for authentication, the option should be selected already hit space bar to select it if its not already, do not uncheck Unix authentication
> sudo pam-auth-update
That is it, we have configured our ldap server successfully and is ready to authenticate user
Now lets add some indices to ldap database to ease the lookup
> nano indices.ldif and paste the following
> 
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uid eq,pres,sub

Now add the above ldif data
> sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f indices.ldif
Verify new indices
> sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config '(olcDatabase={1}hdb)' olcDbIndex
You should see all above indices !
Let add some objects under our ldap tree using ldif file, for testing purposes I am going to add only one OU and only one user
> nano base.ldif
and paste the following to it, save it and exit out of it
> 
dn: ou=Users,dc=testlab,dc=dev
objectClass: organizationalUnit
ou: Users

dn: uid=rkhan,ou=Users,dc=testlab,dc=dev
objectClass: organizationalPerson
objectClass: person
objectClass: top
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: rkhan
sn: Khan
givenName: Ryaz
cn: Ryaz Khan
displayName: Ryaz Khan
uidNumber: 10000
gidNumber: 10000
userPassword: test
gecos: Ryaz Khan
loginShell: /bin/bash
homeDirectory: /profiles/rkhan
mail: [email]ryaz.khan@live.com[/email]
telephoneNumber: 000-000-0000
st: NY
manager: uid=rkhan,ou=Users,dc=testlab,dc=dev
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
title: System Administrator

Now add the above ldif data to ldap database
> ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif and again password is test
Great !	
Now we have one user in our ldap database, so lets try the search indices we created earlier
> 
ldapsearch -x -LLL -b dc=testlab,dc=dev 'uid=rkhan' uid uidNumber displayName
ldapsearch -x -LLL -b dc=testlab,dc=dev 'uid=*kh*' uid uidNumber displayName
ldapsearch -x -LLL -b dc=testlab,dc=dev 'uid=*an' uid uidNumber displayName
ldapsearch -x -LLL -b dc=testlab,dc=dev 'uid=rk*' uid uidNumber displayName

All above queries should retrieve user rkhan from ldap database
Great !
Now let test our ldap authentication
> ssh rkhan@localhost
I was able to login to the system as rkhan with ldap credentials so should you, rkhan might be welcomed with error about home path not found etc.. that is because you probably have not created /profile/rkhan, it would not be created automatically ! 

Have a fun playing with LDAP monster, feel free to [[COLOR="Blue"]ask me[/COLOR]]("http://www.ryazkhan.net") any question(s)

I apologies for any typo, I might have one or more ;)
References
[[COLOR="Blue"]LDAP - Ubuntu Official Documentation[/COLOR]]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html")

---

### Post by quad3d@work on 2012-05-08
The only problem I had with the official doc is replication stuff just flatout doesn't work.

Do you have any idea what's wrong with the written docs?

---

### Post by ryazkhan on 2012-05-08
> **quad3d@work said:**
> The only problem I had with the official doc is replication stuff just flatout doesn't work.

Do you have any idea what's wrong with the written docs?

I have not tried that part (replication), go to samba part and you will know what's wrong, it might work for you

---

### Post by Doug S on 2012-05-08
It would be great if you could make launchpad bug reports for issues with the Ubuntu offical server guide. Or better still join the documentation contibutors team and you will be able to edit yourself and submit merge proposals.
 
I don't use OpenLDAP, but I do know that section was reviewed and edited for the 12.04 release.

---

### Post by ryazkhan on 2012-05-08
> **Doug S said:**
> It would be great if you could make launchpad bug reports for issues with the Ubuntu offical server guide. Or better still join the documentation contibutors team and you will be able to edit yourself and submit merge proposals.
 
I don't use OpenLDAP, but I do know that section was reviewed and edited for the 12.04 release.
Yes it was and LDAP part is not bad, its samba part, it has one link to not existing script, and the samba schema (tar ball) has bug in it as well, some of smbldap-tools perl scripts contains some deprecated codes.

---

### Post by Doug S on 2012-05-08
I see that the samba ldap section and the samba chapter did not get reviewed/edited in the 12.04 cycle. In the end, the time was up but there was still lots to do.
 
It would be much appreciated if you could enter a launchpad bug, so that your important observations and suggestions don't get lost.
 
@quad3dwork: also, for your issues with the replication parts.

---

### Post by quad3d@work on 2012-05-08
Never used Launchpad before. [Hope I did it right]("https://answers.launchpad.net/ubuntu/+question/196545").

---

### Post by quad3d@work on 2012-05-15
Is objectClass "olcPPolicyConfig" missing in ppolicy.schema?

Loaded ppolicy schema and trying to do cn=config overlay and it's complaining.

```
# ldapadd -x -D cn=admin,dc=example,dc=com -W -f add_overlay_pwpolicy.ldif 
```> Enter LDAP Password: 
adding new entry "olcOverlay=ppolicy,olcDatabase={1}hdb,cn=config"
ldap_add: Invalid syntax (21)
        additional info: objectClass: value #1 invalid per syntax```
# cat add_overlay_pwpolicy.ldif
```> dn: olcOverlay=ppolicy,olcDatabase={1}hdb,cn=config
objectClass: olcOverlayConfig
objectClass: olcPPolicyConfig
olcOverlay: ppolicy
olcPPolicyDefault: cn=default,ou=policies,dc=example,dc=com
olcPPolicyHashCleartext: TRUEI have phpLDAPadmin installed as well and do not see it under objectClass when I browsed. Anyone here have success getting PPolicy to work?

---

### Post by ryazkhan on 2012-05-16
> **quad3d@work said:**
> Is objectClass "olcPPolicyConfig" missing in ppolicy.schema?

Loaded ppolicy schema and trying to do cn=config overlay and it's complaining.

```
# ldapadd -x -D cn=admin,dc=example,dc=com -W -f add_overlay_pwpolicy.ldif 
``````
# cat add_overlay_pwpolicy.ldif
```I have phpLDAPadmin installed as well and do not see it under objectClass when I browsed. Anyone here have success getting PPolicy to work?


How are you adding it ? Are you using the ldif file located in /etc/ldap/schema directory ? Or you making fresh ldif out of the ppolicy schema located under /etc/ldap/schema directory ?

I have added the schema successfully by creating new ldif file and then cleaning that ldif file.

So here is what I did, create schema.conf file
> nano schema.conf
and past the following in schema.conf file
> include /etc/ldap/schema/ppolicy.schema

create temporary dirctory
> mkdir out
then issue the following command to make ldif file for ppolicy schema
> slapcat -f schema.conf -F out -n0 -H ldap:///cn={0}ppolicy,cn=schema,cn=config -l cn=ppolicy.ldif

now edit the ppolicy ldif file
> nano cn\=ppolicy.ldif
remove
> dn: cn={0}ppolicy,cn=schema,cn=config
objectClass: olcSchemaConfig
cn: {0}ppolicy

with
> dn: cn=ppolicy,cn=schema,cn=config
objectClass: olcSchemaConfig
cn: ppolicy

and remove following lines, they are located at the bottom of cn=ppolicy.ldif file
> structuralObjectClass: olcSchemaConfig
entryUUID: be6ff7ee-33bd-1031-873f-7b37ded38df5
creatorsName: cn=config
createTimestamp: 20120516161257Z
entryCSN: 20120516161257.063306Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20120516161257Z

save the file and add the cleaned ldif ppolicy schema to ldap
> sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f cn\=ppolicy.ldif
Hope you will be happy !

---

### Post by quad3d@work on 2012-05-17
Ryaz,

Thanks. I did all that.

The problem was olcModuleLoad didn't load ppolicy into cn=module{0}. So cn=config DB didn't inherent all the objectClass(es) from ppolicy - hence "olcPPolicyConfig" was missing.

Just add the following to cn=config:
```
dn: cn=module{0},cn=config
changetype: modify
add: olcModuleLoad
olcModuleLoad: ppolicy
```So the steps: 1) load schema 2) load module 3) add overlay layer.

---

### Post by ranger12 on 2012-05-21
?

---

### Post by ranger12 on 2012-05-21
?

---

### Post by quad3d@work on 2012-05-21
Did you modify /etc/hosts on line "127.0.0.1" with your FQDN prior to install?

---

### Post by ranger12 on 2012-05-22
?

---

### Post by ranger12 on 2012-05-22
?

---

### Post by ranger12 on 2012-05-22
I deleted my previous posts since I have gotten it to work. I don't think it was a problem with my /etc/hosts file. I believe it was errors in the entries I put into the ldap database. I do have 1 question and it borderlines on being a stupid question. I assume libnss-ldap is installed on the client and not server? Some tutorials give the impression it is on the server and some on the client. I would think of course it needs to be on the client since that is of course where you want to log in from. I did try installing on the client and it seemed to slow things down as far as loading lightdm.

Later:
Okay I think I just answered my own stupid question. I uninstalled the libnss-ldap package off the workstation client and rebooted. I opened a terminal and was able to ssh with my ldap credentials as well as other ldap user accounts I added. I am going to try and discover how to make it work with lightdm - all I get when I type in the user's password in the "Login" box is "Invalid Password - Please try again"

---

### Post by ranger12 on 2012-05-25
So has any of you gentlemen tried the ldapscripts package? The wrapper scripts work pretty well and certainly makes life alot easier working with the database.

---

### Post by ryazkhan on 2012-05-29
> **ranger12 said:**
> So has any of you gentlemen tried the ldapscripts package? The wrapper scripts work pretty well and certainly makes life alot easier working with the database.

Yes I have they are pretty good !

---

### Post by teloris on 2012-06-28
hi,

i try to follow these great tuts but unfortunately i got some errors when doing this :

> **ryazkhan said:**
> 
Verify new indices
```
 sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config '(olcDatabase={1}hdb)' olcDbIndex
```You should see all above indices !

got this error :
```
ldap_search_ext: Bad search filter (-7)
```> **ryazkhan said:**
> 
Now add the above ldif data to ldap database
 ```
 ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif                      
```
got this error :
```
ldap_bind: Invalid credentials (49)
```any idea ? anyone ?

---

### Post by LHammonds on 2012-06-29
The original URL changed.  Here is the current link: [OpenLDAP Server Setup]("http://www.ryazkhan.net/?show=ldap12")

And a list of his other [How-To]("http://www.ryazkhan.net/?show=howtos") articles.

LHammonds

---

### Post by ryazkhan on 2012-07-20
> **ryazkhan said:**
> Here is the tutorial as promised, its always [[COLOR="Blue"]available here[/COLOR]]("http://www.ryazkhan.net/articles/ldap12")

With the assumption that Ubuntu 12.04 LTS Server is already installed, it should work with any other version with some changes if any. No assurance that it will work for your setup, worked for me so I am sharing it

I have used dc=testlab,dc=dev as my domain, cn=admin,dc=testlab,dc=dev as my ldap admin user, and test as my password throughout this guide, please feel free to change it to your liking 
Update all packages and install updates if any

The base DN or suffix of ldap tree will be populated/created based on the domain name specified in /etc/hosts file, in my case it is testlab.dev	
Lets proceed with install and install following required packages

the password would test like I mentioned in the beginning
Now lets add some logging level for ldap
nano log.ldif and paste the following in it then save the file and exit out

Add the above ldif file to ldap database

Done, at this point we have working OpneLDAP server
Now let set it up so we can actually use it, here we are going to use it for user authentication
Install libnss-ldap package

There would few questions here, answer them like following

If you make a mistake you can try again using

Now configure the LDAP profile for NSS
There should not be any error, if you have some error(s) go back and check your config
Finally tell system to use ldap for authentication, the option should be selected already hit space bar to select it if its not already, do not uncheck Unix authentication

That is it, we have configured our ldap server successfully and is ready to authenticate user
Now lets add some indices to ldap database to ease the lookup
 and paste the following

Now add the above ldif data

Verify new indices

You should see all above indices !
Let add some objects under our ldap tree using ldif file, for testing purposes I am going to add only one OU and only one user

and paste the following to it, save it and exit out of it

Now add the above ldif data to ldap database
 and again password is test
Great !	
Now we have one user in our ldap database, so lets try the search indices we created earlier

All above queries should retrieve user rkhan from ldap database
Great !
Now let test our ldap authentication

I was able to login to the system as rkhan with ldap credentials so should you, rkhan might be welcomed with error about home path not found etc.. that is because you probably have not created /profile/rkhan, it would not be created automatically ! 

Have a fun playing with LDAP monster, feel free to [[COLOR="Blue"]ask me[/COLOR]]("http://www.ryazkhan.net") any question(s)

I apologies for any typo, I might have one or more ;)
References
[[COLOR="Blue"]LDAP - Ubuntu Official Documentation[/COLOR]]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html")

The link to the original article given in here is broken now, the new link is 
[[COLOR="Blue"]this[/COLOR]]("http://www.ryazkhan.net/?show=ldap12") 

Also the contact link is 
[[COLOR="Blue"]this[/COLOR]]("http://www.ryazkhan.net/?show=contact")

---

### Post by ryazkhan on 2012-07-20
> **LHammonds said:**
> The original URL changed.  Here is the current link: [OpenLDAP Server Setup]("http://www.ryazkhan.net/?show=ldap12")

And a list of his other [How-To]("http://www.ryazkhan.net/?show=howtos") articles.

LHammonds

Thank you for the correction LHammonds

---

### Post by gsedej on 2012-07-23
Hello.
I tried to install LDAP server in VirtualBox (Ubuntu 12.04 32bit) following this tutorial.
I get error while I want to add admin.

I get error:
```
$ ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif
ldap_bind: Invalid credentials (49)

```

The input files (.ldif) are the same.

here are configuration files:
hosts
```
127.0.0.1	localhost
127.0.1.1	VB
10.0.2.15	ldap.testlab.dev ldap
```

ldap.conf
```
host 10.0.2.15
base dc=testlab,dc=dev
uri ldap://10.0.2.15/
rootbinddn cn=admin,dc=testlab,dc=dev
ldap_version 3
bind_policy soft
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,colord,daemon,games,gnats,hplip,irc,kernoops,libuuid,lightdm,list,lp,mail,man,messagebus,news,ntp,openldap,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,sync,sys,syslog,usbmux,uucp,whoopsie,www-data
```

nsswitch:
```
passwd: files ldap
group: files ldap
shadow: files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup: nis
```

ldapscripts.conf
```
SERVER=localhost
SUFFIX="dc=example,dc=com" # Global suffix
GSUFFIX="ou=Groups"        # Groups ou (just under $SUFFIX)
USUFFIX="ou=Users"         # Users ou (just under $SUFFIX)
MSUFFIX="ou=Machines"      # Machines ou (just under $SUFFIX)
SASLAUTH=""
BINDDN='cn=admin,dc=example,dc=com'
BINDPWDFILE="/etc/ldapscripts/ldapscripts.passwd"
GIDSTART="10000" # Group ID
UIDSTART="10000" # User ID
MIDSTART="20000" # Machine ID
GCLASS="posixGroup"   # Leave "posixGroup" here if not sure !
CREATEHOMES="no"      # Create home directories and set rights ?
PASSWORDGEN="pwgen"
RECORDPASSWORDS="no"
PASSWORDFILE="/var/log/ldapscripts_passwd.log"
LOGFILE="/var/log/ldapscripts.log"
TMPDIR="/tmp"
LDAPSEARCHBIN="/usr/bin/ldapsearch"
LDAPADDBIN="/usr/bin/ldapadd"
LDAPDELETEBIN="/usr/bin/ldapdelete"
LDAPMODIFYBIN="/usr/bin/ldapmodify"
LDAPMODRDNBIN="/usr/bin/ldapmodrdn"
LDAPPASSWDBIN="/usr/bin/ldappasswd"
GETENTPWCMD=""
GETENTGRCMD=""
GTEMPLATE=""
UTEMPLATE=""
MTEMPLATE=""
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:5a:0b:7c  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5a:b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

```

---

### Post by ryazkhan on 2012-07-23
> **gsedej said:**
> Hello.
I tried to install LDAP server in VirtualBox (Ubuntu 12.04 32bit) following this tutorial.
I get error while I want to add admin.

I get error:
```
$ ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif
ldap_bind: Invalid credentials (49)

```

The input files (.ldif) are the same.

here are configuration files:
hosts
```
127.0.0.1	localhost
127.0.1.1	VB
10.0.2.15	ldap.testlab.dev ldap
```

ldap.conf
```
host 10.0.2.15
base dc=testlab,dc=dev
uri ldap://10.0.2.15/
rootbinddn cn=admin,dc=testlab,dc=dev
ldap_version 3
bind_policy soft
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,colord,daemon,games,gnats,hplip,irc,kernoops,libuuid,lightdm,list,lp,mail,man,messagebus,news,ntp,openldap,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,sync,sys,syslog,usbmux,uucp,whoopsie,www-data
```

nsswitch:
```
passwd: files ldap
group: files ldap
shadow: files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup: nis
```

ldapscripts.conf
```
SERVER=localhost
SUFFIX="dc=example,dc=com" # Global suffix
GSUFFIX="ou=Groups"        # Groups ou (just under $SUFFIX)
USUFFIX="ou=Users"         # Users ou (just under $SUFFIX)
MSUFFIX="ou=Machines"      # Machines ou (just under $SUFFIX)
SASLAUTH=""
BINDDN='cn=admin,dc=example,dc=com'
BINDPWDFILE="/etc/ldapscripts/ldapscripts.passwd"
GIDSTART="10000" # Group ID
UIDSTART="10000" # User ID
MIDSTART="20000" # Machine ID
GCLASS="posixGroup"   # Leave "posixGroup" here if not sure !
CREATEHOMES="no"      # Create home directories and set rights ?
PASSWORDGEN="pwgen"
RECORDPASSWORDS="no"
PASSWORDFILE="/var/log/ldapscripts_passwd.log"
LOGFILE="/var/log/ldapscripts.log"
TMPDIR="/tmp"
LDAPSEARCHBIN="/usr/bin/ldapsearch"
LDAPADDBIN="/usr/bin/ldapadd"
LDAPDELETEBIN="/usr/bin/ldapdelete"
LDAPMODIFYBIN="/usr/bin/ldapmodify"
LDAPMODRDNBIN="/usr/bin/ldapmodrdn"
LDAPPASSWDBIN="/usr/bin/ldappasswd"
GETENTPWCMD=""
GETENTGRCMD=""
GTEMPLATE=""
UTEMPLATE=""
MTEMPLATE=""
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:5a:0b:7c  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5a:b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

```

Check your ldapscript.conf again, you have > BINDDN='cn=admin,dc=example,dc=com'

It should be > BINDDN='cn=admin,dc=testlab,dc=dev'

Also run > sudo dpkg-reconfigure ldap-auth-config to double check you configs, what is > 127.0.1.1	VB entry for ? can remove/comment it out ?

Please post the outcomes 

Thank you

---

### Post by gsedej on 2012-07-23
127.0.1.1 is computer name (VB (VirtualBox) in my case. I didn't change it.

> entry for ? can remove/comment it out ?
Can you explain this?

Changed BINDDN, and run reconfigure. It asked me for "Local crypt to use when changing passwords:" and I answered "clear" (no crypt). It still doesn't work.

---

### Post by ryazkhan on 2012-07-23
> **gsedej said:**
> 127.0.1.1 is computer name (VB (VirtualBox) in my case. I didn't change it.


Can you explain this?

Changed BINDDN, and run reconfigure. It asked me for "Local crypt to use when changing passwords:" and I answered "clear" (no crypt). It still doesn't work.

sorry I mean entry for 127.0.1.1 can be removed since you already have the fqdn name with 10.0.2.15 ip address.
You dont need to select crypt as clear text, I always select whatever the default is [md5]. So something to try run the > sudo dpkg-reconfigure ldap-auth-configagain and accept md5 for hash. Verify the ldap admin password stored in /etc/ldap.secret file, I have done this howto other days and did not ran into any issue. Can you please include the steps you done so I will try to duplicate the issue 

Thank you

---

### Post by ryazkhan on 2012-07-23
> **ryazkhan said:**
> Hi folks, 

The new LTS version is very impressive, it equipped with all latest and greatest open source stuff ! I find that configuring any thing like samba,ldap etc.. has been made even simpler than 10.04 LTS. Ubuntu official documentation are little confusing as they always are, so don't totally relay on them and expect to have working setup, it might work or might not, anyway it did not worked for me but was main source of my references in configuring my OpenLDAP Server and setting it up for authentication. The procedure has been tested few times in virtual environment for the sake of accuracy and functionality. Currently its available on my website, I have not got enough time to write it here, I will update the thread whenever I got some extra time to spare.

[http://www.ryazkhan.net/articles/ldap12](http://www.ryazkhan.net/articles/ldap12)

The above page on my website has been moved to [[COLOR="Blue"]here[/COLOR]]("http://www.ryazkhan.net/?show=ldap12")

---

### Post by gsedej on 2012-07-23
I selected md5.
/etc/ldap.secret has "test" in it.

I still get invalid credentials error.

What i did?
```

sudo dpkg-reconfigure ldap-auth-config
LDAP configuration? -> yes
ok
LDAP server Uniform Resource Identifier: ldap://10.0.2.15
Distinguished name of the search base: dc=testlab,dc=dev
LDAP version: 3
Ok
Make local root Database admin: YES
Does the LDAP database require login? no
LDAP account for root:  cn=admin,dc=testlab,dc=dev
Please enter the password to...
OK
Local crypt to use when changing passwords: MD5

```

If i comment "127.0.1.1 VB", it takes some time after ldapadd command, but still returns credentials (49) error.

---

### Post by ryazkhan on 2012-07-23
> **gsedej said:**
> I selected md5.
/etc/ldap.secret has "test" in it.

I still get invalid credentials error.

What i did?
```

sudo dpkg-reconfigure ldap-auth-config
LDAP configuration? -> yes
ok
LDAP server Uniform Resource Identifier: ldap://10.0.2.15
Distinguished name of the search base: dc=testlab,dc=dev
LDAP version: 3
Ok
Make local root Database admin: YES
Does the LDAP database require login? no
LDAP account for root:  cn=admin,dc=testlab,dc=dev
Please enter the password to...
OK
Local crypt to use when changing passwords: MD5

```

If i comment "127.0.1.1 VB", it takes some time after ldapadd command, but still returns credentials (49) error.

Replace all values for 10.0.2.15 in ldap.conf file with 127.0.0.1

Run the dpkg-reconfigure again and type 127.0.0.1 instead 10.0.2.15

Then give it try and post the outcomes

---

### Post by gsedej on 2012-07-24
I retried all procedure again on real computer and I still get same error. The must be something wrong with hosts, because everyhing else is "hard copy" from your tutorial.

---

### Post by ryazkhan on 2012-07-24
> **gsedej said:**
> I retried all procedure again on real computer and I still get same error. The must be something wrong with hosts, because everyhing else is "hard copy" from your tutorial.

Can you look in logs to see what is happening ? 
> tail -f /var/log/syslog
Now try to make connection from another console 

Thx

---

### Post by gsedej on 2012-07-24
```
Jul 24 13:41:50 gasper-VB kernel: [72522.540046] type=1400 audit(1343130110.713:37): apparmor="DENIED" operation="open" parent=3642 profile="/usr/sbin/slapd" name="/etc/pkcs11/modules/" pid=3666 comm="slapd" requested_mask="r" denied_mask="r" fsuid=115 ouid=0
Jul 24 13:41:50 gasper-VB slapd[3667]: slapd starting
Jul 24 13:43:57 gasper-VB kernel: [72649.642164] atkbd serio0: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jul 24 13:44:45 gasper-VB sudo: pam_ldap: error trying to bind (Invalid credentials)

```

It looked like apparmor, so I unistalled and rebooted.

After reboot the was the only mention of ldap in syslog:
```
Jul 24 13:53:04 gasper-VB slapd[748]: @(#) $OpenLDAP: slapd  (Apr  5 2012 16:19:27) $#012#011buildd@roseapple:/build/buildd/openldap-2.4
```

When I put ldapadd nothing happens in syslog. (but i still get credentials error)

---

### Post by ryazkhan on 2012-07-24
> **gsedej said:**
> ```
Jul 24 13:41:50 gasper-VB kernel: [72522.540046] type=1400 audit(1343130110.713:37): apparmor="DENIED" operation="open" parent=3642 profile="/usr/sbin/slapd" name="/etc/pkcs11/modules/" pid=3666 comm="slapd" requested_mask="r" denied_mask="r" fsuid=115 ouid=0
Jul 24 13:41:50 gasper-VB slapd[3667]: slapd starting
Jul 24 13:43:57 gasper-VB kernel: [72649.642164] atkbd serio0: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jul 24 13:44:45 gasper-VB sudo: pam_ldap: error trying to bind (Invalid credentials)

```

It looked like apparmor, so I unistalled and rebooted.

After reboot the was the only mention of ldap in syslog:
```
Jul 24 13:53:04 gasper-VB slapd[748]: @(#) $OpenLDAP: slapd  (Apr  5 2012 16:19:27) $#012#011buildd@roseapple:/build/buildd/openldap-2.4
```

When I put ldapadd nothing happens in syslog. (but i still get credentials error)

I just completed the setup using [ [COLOR="Blue"]this[/COLOR] ]("http://www.ryazkhan.net/?show=ldap12") and it went without any error, however the one you been following did not went error free so I will look into again when I get chance, in the main while complete the setup from the link provided above 

Thank you

---

### Post by gsedej on 2012-07-25
Still no luck:
I did the whole thing again after purgin all packages. I set hosts file to my virtualbox IP i got, because if I localhost I get problems in console (hostname)

I checked all output and this is the only suspicous:
```
update-rc.d: warning: libnss-ldap start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)
```

Anyway here is whole procedure (terminal commands and output):
[http://pastebin.com/tcBH3ERw]("http://pastebin.com/tcBH3ERw")
(don't mind slovenian language)

And hrere is syslog:
[http://pastebin.com/YUwfNGp6]("http://pastebin.com/YUwfNGp6")

---

### Post by ryazkhan on 2012-07-25
> **gsedej said:**
> Still no luck:
I did the whole thing again after purgin all packages. I set hosts file to my virtualbox IP i got, because if I localhost I get problems in console (hostname)

I checked all output and this is the only suspicous:
```
update-rc.d: warning: libnss-ldap start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)
```

Anyway here is whole procedure (terminal commands and output):
[http://pastebin.com/tcBH3ERw]("http://pastebin.com/tcBH3ERw")
(don't mind slovenian language)

And hrere is syslog:
[http://pastebin.com/YUwfNGp6]("http://pastebin.com/YUwfNGp6")

Can you please start from scratch, I mean fresh build since you are working in VM anyway.

Thx, LSB warning is for USB and wont cause anything

---

### Post by ryazkhan on 2012-07-25
> **ryazkhan said:**
> Can you please start from scratch, I mean fresh build since you are working in VM anyway.

Thx, LSB warning is for USB and wont cause anything

Folks, 

Some of you are having issue and having invalid credential error when you try to add base.ldif file

You are only getting this because you forgot to set the /etc/hosts file correctly in the start and ldap ended up configuring wrong domain name. 
Whatever you specify the domain name in /etc/hosts would be your new DN and if you don't specify any then your DN would be nodomain. That is exactly happening here and you getting error because you are trying with cn=amdin,dc=testlab,dc=dev but ldap don't know about this DN. The dn in ldap is dc=nodomain so the admin account is cn=admin,dc=nodomain.

You can correct this by two ways I know.

Method 1

> sudo dpkg-reconfigure slapd

And answer like
> 
No
testlab.dev
testlab.dev
test
test
HDB
No
Yes
No


Now try to run

> ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif 

Method 2

> nano /etc/ldap/slapd.d/cn\=config/olcDatabase\=\{1\}hdb.ldif

And replace all instances of  
> dc=nodomain

with
> dc=testlab,dc=dev

Remove existing ldap database

> rm /var/lib/ldap/*

Restart ldap

> service slapd restart

Add the following to the top your base.ldif file otherwise you will get no such object (32) error.

> 
dn: dc=testlab,dc=dev
dc: TESTLAB
objectClass: top
objectClass: domain


Now run the add command again and hopefully you will by happy

> ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif 

Hopefully you will be happy using any of those two methods

Let me know if you have any question(s)

Thank you

---

### Post by gsedej on 2012-07-26
It works now! Reconfiguration of slapd helped out (Method 1). Thank you for all the time and help.

---

### Post by ryazkhan on 2012-07-26
> **gsedej said:**
> It works now! Reconfiguration of slapd helped out (Method 1). Thank you for all the time and help.

Glad to help, I am glad that it is working for you

---

### Post by quartz75 on 2012-08-10
Hi all. Help me plz. I want configure openldap server on ubuntu 12.04 with TSL and i need step by step tutorial for server and client. Help me plz i am desperat i lose 3 day.

thanks

---

### Post by quartz75 on 2012-08-13
anyone help me?????

---

### Post by namerg on 2012-08-24
Hello Guys,

Is it possible the following scenario:

Ubuntu 12.04.1 LTS with OpenLdap installed not part of a domain.
Windows AD Network Domain.

Can I sync OpenLDAP with Windows AD ?

If i log into ubuntu and query AD can I restrict of doing any modifications from this box to the Windows AD ?

But, I do a change from Windows AD can be reflected into the OpenLdap installed in the ubuntu box ?

Any guidance will be helpful, I am 100% newbie with openldap

Thanks for your help,
G

---

### Post by LHammonds on 2012-08-25
> **namerg said:**
> Is it possible the following scenario:

Ubuntu 12.04.1 LTS with OpenLdap installed not part of a domain.
Windows AD Network Domain.

Can I sync OpenLDAP with Windows AD ?

I'm no expert in this area but if I were tackling this problem, I would be concerned about the following:


[LIST]
[*]Export AD user list for import into OpenLDAP (passwords cannot be sync'd since they cannot be extracted from AD)
[*]What happens if an AD user is disabled in AD?
[*]What happens when there are OpenLDAP users that exists but no longer in AD?
[*]Are groups going to be sync'd as well?  If so, then membership will need to be exported too.
[/LIST]

I have done something similar to this but mainly exporting AD users to be imported into a Zimbra mail server.  You can see the scripts I wrote in the Zimbra link in my sig.

LHammonds

---

### Post by namerg on 2012-08-27
LHammonds, Thank you for your reply.

Let me rephrase my problem.

I want to query AD users from Ubuntu.

I would expect to get all of your user data including office phone, email, etc.

Thanks for your help,

---

### Post by BrianBlaze on 2012-08-29
I just wanted to thank you! I was having all kinds of problems and I used your help and I am slowly going to become an LDAP master! Thank you sooooo much :):popcorn::guitar:):P

---

### Post by ryazkhan on 2012-10-31
> **ryazkhan said:**
> Hi folks, 

The new LTS version is very impressive, it equipped with all latest and greatest open source stuff ! I find that configuring any thing like samba,ldap etc.. has been made even simpler than 10.04 LTS. Ubuntu official documentation are little confusing as they always are, so don't totally relay on them and expect to have working setup, it might work or might not, anyway it did not worked for me but was main source of my references in configuring my OpenLDAP Server and setting it up for authentication. The procedure has been tested few times in virtual environment for the sake of accuracy and functionality. Currently its available on my website, I have not got enough time to write it here, I will update the thread whenever I got some extra time to spare.

[http://www.ryazkhan.net/?show=ldap12](http://www.ryazkhan.net/?show=ldap12)

Corrected the URL for [[COLOR="Blue"]original[/COLOR]]("http://www.ryazkhan.net/?show=ldap12") and most up to dated article.

---

### Post by Sanaew on 2012-11-23
Hi all!
I set up an LDAP server and Samba for instructions. All is wonderful.
But when I give the command
[FONT="Courier New"]sudo smbldap-groupmod -m 'rkhan' 'Domain Admins'[/FONT]

I get the error
[FONT="Courier New"]No such object at /usr/share/perl5/smbldap_tools.pm line 979.[/FONT]

Here is the line
[FONT="Courier New"]$mesg->code && die $mesg->error;[/FONT]

Help me.

---

### Post by gsedej on 2013-02-27
**edit:** I missed out Troubleshoot explained on [http://www.ryazkhan.net/?show=ldap12](http://www.ryazkhan.net/?show=ldap12). 


Hi,

I tried the installation again, strictly step by step on rkhan tutorial, but it fails at step:

```
$ ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif

ldap_bind: Invalid credentials (49)

syslog:
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 fd=13 ACCEPT from IP=127.0.0.1:48915 (IP=0.0.0.0:389)
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=0 BIND dn="cn=admin,dc=testlab,dc=dev" method=128
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=0 RESULT tag=97 err=49 text=
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=1 UNBIND
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 fd=13 closed
```

I checked the *cn=config*

```

sudo ldapsearch -Y EXTERNAL -H ldapi:/// -b cn=config

...

# {1}hdb, config
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=nodomain
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=nodomain" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=nodomain" write by * read
olcLastMod: TRUE
**olcRootDN: cn=admin,dc=nodomain**
olcRootPW: {SSHA}ltLI+IvG1rjday4QvuQyzW+XsO3yv2H1
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: uid eq,pres,sub
```

After trying to add like 
```
ldapadd -x -D cn=admin,dc=nodomain -w test -f base.ldif
```
it was added ok.

Any idea why admin gets to *dc=nodomain* instead of *dc=testlab,dc=dev*?

(I tried setting *sudo dpkg-reconfigure ldap-auth-config* several times)

---

### Post by ryazkhan on 2013-03-15
> **gsedej said:**
> **edit:** I missed out Troubleshoot explained on [http://www.ryazkhan.net/?show=ldap12](http://www.ryazkhan.net/?show=ldap12). 


Hi,

I tried the installation again, strictly step by step on rkhan tutorial, but it fails at step:

```
$ ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif

ldap_bind: Invalid credentials (49)

syslog:
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 fd=13 ACCEPT from IP=127.0.0.1:48915 (IP=0.0.0.0:389)
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=0 BIND dn="cn=admin,dc=testlab,dc=dev" method=128
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=0 RESULT tag=97 err=49 text=
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 op=1 UNBIND
Feb 27 12:17:03 ubu-ldap-test slapd[3398]: conn=1079 fd=13 closed
```

I checked the *cn=config*

```

sudo ldapsearch -Y EXTERNAL -H ldapi:/// -b cn=config

...

# {1}hdb, config
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=nodomain
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=nodomain" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=nodomain" write by * read
olcLastMod: TRUE
**olcRootDN: cn=admin,dc=nodomain**
olcRootPW: {SSHA}ltLI+IvG1rjday4QvuQyzW+XsO3yv2H1
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: uid eq,pres,sub
```

After trying to add like 
```
ldapadd -x -D cn=admin,dc=nodomain -w test -f base.ldif
```
it was added ok.

Any idea why admin gets to *dc=nodomain* instead of *dc=testlab,dc=dev*?

(I tried setting *sudo dpkg-reconfigure ldap-auth-config* several times)

That is because at the start you did not modified your /etc/hosts file and did not added testlab.dev as your domain to your host, it would look something like 
> 10.10.10.10    ldap.testlab.dev   ldap where ldap is your domain controller and its ip is 10.10.10.10, feel free to change it
Hope above will help.

---

### Post by lordmorgoth on 2013-09-16
I've been trying to follow the official documentation for this to work in vain ! This worked like a charm ! thanks !

---

