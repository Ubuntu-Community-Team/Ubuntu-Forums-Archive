---
title: "Samba , PDC: windows xp  unable to join the domain"
date: 2010-12-18
forum: Server Platforms
---

### Post by dummy4ever on 2010-12-18
Hello Guys I'm a newbie here and obviously this is my first post. I've been configuring a PDC using samba I used this tutorial [https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html") as reference. It seems all went well during the installation and configuration not until when I try to join a windows machine to the domain.

Scenario: When the authentication dialog box prompts the username and password of the domain administrator. I supply root as username and its corresponding password. Then I will prompt an error "The user name could not be found. But, I have noticed that when I supply a wrong password of root the it will prompt "Login failure: unknown user name or bad password. It seems that the windows machine was able to recognize the account somehow.

Any help would be appreciated.

Tnx.

---

### Post by dummy4ever on 2010-12-18
Very funny.. Just a few minutes after my first post I was able to resolved the problem.

In case someone wants to know, this is what i did.



vi /etc/nsswitch.conf

change the line
 hosts: files dns
to 
 hosts: files wins dns

and

execute this command

echo "root = administrator" > /etc/samba/smbusers

thats it.

---

### Post by tanlenhat on 2010-12-18
hello dummy!
I am also trying to build a DC with samba&ldap on ubuntu 10.04 for windows xp to join in but I got an error when login to LDAP server and the message for error is: "ldap_bind: Invalid credentials (49)"
My scenario is based on Ubuntu server guide 10.04 like you.
Firstly I install openldap server, populating,authentication, everything run well
After that I install samba, config openldap server,everything still run ok, but when I come to this step:
> 
Finally, using the **ldapadd** utility, add the new schema to the                  directory:                                              **ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif**

I got an error "ldap_bind: Invalid credentials (49)" I dont know why, I am sure that I type correct password.
Please help me this problem :popcorn:

---

### Post by dummy4ever on 2010-12-18
> **tanlenhat said:**
> hello dummy!
I am also trying to build a DC with samba&ldap on ubuntu 10.04 for windows xp to join in but I got an error when login to LDAP server and the message for error is: "ldap_bind: Invalid credentials (49)"
My scenario is based on Ubuntu server guide 10.04 like you.
Firstly I install openldap server, populating,authentication, everything run well
After that I install samba, config openldap server,everything still run ok, but when I come to this step:

I got an error "ldap_bind: Invalid credentials (49)" I dont know why, I am sure that I type correct password.
Please help me this problem :popcorn:

Ldap is a real headache I have tried it once but I was also unsuccessful. Do you have the link of the reference you used? And which part of it that you encounter the problem?

---

### Post by tanlenhat on 2010-12-18
Yea, I also follow the tutorial Ubuntu server guide at [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
Step 1: I do as chapter 6, install OPENLDAP server, populating LDAP => run ok.
Step 2: do as LDAP Authentication section => run ok.
Step 3: Install samba => ok.
Step 4: do as OpenLDAP Configuration section => there's a problem here: when I run the command:
> ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldifI can't login to LDAP server, it said that:
> ldap_bind: Invalid credentials (49)I am sure that the password is correct, but I still receive this message :sad:

---

### Post by tanlenhat on 2010-12-21
dummy are you there? :(

---

### Post by robweps on 2011-01-08
I have the same problem as tanlenhet.

Does someone know the answer?

Rob

---

### Post by robweps on 2011-01-08
Hier de oplossing:

Maak bestand config.ldif:

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: {MD5}FWJl29XTwNdfdf63jsdsadsA==  <---- hier je eigen password

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess


sudo ldapadd -Y EXTERNAL -H ldapi:/// -f config.ldif

---

### Post by HiMannu on 2011-01-22
Hi Tan and Rob,

   If you see the "Invalid Credentials" it is for sure that you have forgot / misconfigured at least one of the important file. Please check the following files carefully :

1.  /etc/ldap/slapd.conf and /etc/default/slapd
2.  smbldap.conf and smbldap_bind.conf ( Normally these files can also be generated thru configure.pl in /usr/share/smbldap-tools/...

  Creating initial database is easy, I would suggest you to follow this link an try once again. Though it is for ver 9.04 but it works for 10.04 as well.

[http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)

** Don't miss any step. 

Mannu

---

