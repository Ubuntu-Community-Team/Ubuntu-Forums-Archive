---
title: "OpenLDAP on ubuntu server 8.04.4 issues"
date: 2010-02-26
forum: Server Platforms
---

### Post by lokimon on 2010-02-26
i have been trying to get a working LDAP server going and am having a lot of trouble.  i have read the guides on this site but am still hitting a brick wall.

i saw that OpenLDAP has issues with ubuntu server 9.10 so i decided to go with the older, LTS server option of 8.04.4.  i followed this guide: [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html) after reading this page as well: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

i have a fresh install of ubuntu server.  during  the install, the only server option i installed was OpenSSH server.

step 1) i installed slapd and ldap-utils via apt-get
step 2) i ran dpkg-reconfigure slapd and fed it my domain info and a password for the admin.
step 3) i tested it with the following command as suggested:

```
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
```

i am then prompted for a password:

```
Enter LDAP Password:
```

which i enter.

then, i keep getting this error:

```
ldap_bind: Invalid credentials (49)
```

that error isn't very helpful.  it usually means that the username or password is wrong.  i have repeated the 3 steps over and over with various passwords.  i always get the same error.

i hope someone can shed some light on this.  this is literally a fresh install that has followed the guide step by step.  i don't see what i could have done wrong.

---

### Post by lokimon on 2010-02-26
more info:

when i run this command:

```
root@ldap:~# ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
```

i can't find a slapd.log but in the syslog i see the following error:

```
Feb 26 20:56:15 ldap slapd[9710]: conn=2 fd=14 ACCEPT from IP=127.0.0.1:60257 (IP=0.0.0.0:389) 
Feb 26 20:56:15 ldap slapd[9710]: conn=2 op=0 BIND dn="cn=admin,cn=config" method=128 
Feb 26 20:56:15 ldap slapd[9710]: conn=2 op=0 RESULT tag=97 err=49 text= 
Feb 26 20:56:15 ldap slapd[9710]: conn=2 fd=14 closed (connection lost)
```

but when i run a generic ldapsearch i do get a response:

```
root@ldap:~# ldapsearch -x
# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1
root@ldap:~#
```

and the log:

```
Feb 26 20:57:19 ldap slapd[9710]: conn=3 fd=14 ACCEPT from IP=127.0.0.1:57627 (IP=0.0.0.0:389) 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 op=0 BIND dn="" method=128 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 op=0 RESULT tag=97 err=0 text= 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 op=1 SRCH base="" scope=2 deref=0 filter="(objectClass=*)" 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 op=1 SEARCH RESULT tag=101 err=32 nentries=0 text= 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 op=2 UNBIND 
Feb 26 20:57:19 ldap slapd[9710]: conn=3 fd=14 closed
```

---

### Post by lokimon on 2010-03-01
still at this, and not understanding why this isn't working.

started over from scratch:

purged the install (apt-get remove slapd ldap-utils)

deleted my slapd.conf and ldap.conf files.

followed this guide: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

installed slapd, ldap-utils and db4.2-util via apt-get

this time i was not asked to identify the domain, or give a password for some reason. when i looked at the slapd.conf it had added my domain info for me.

i used slappasswd to generate a password and then i copied and pasted that password hash into my new /etc/ldap/slapd/conf file onto a line just below the entry for rootdn as outlined in the guide.  i also had to comment out the rootdn line (not mentioned in the guide but seemed necessary.)

made an init.ldif file just as in the guide, only substituted my own domain info instead of example.com.  generated passwords using slappasswd for this file as well (made the admin user password the same as in the slapd.conf file.)

tried to load this in using ldapadd but got an error of invalid credentials:

```
loki@ldap:~$ sudo ldapadd -x -W -c -D "cn=admin,dc=fmri,dc=columbia,dc=edu" -f init.ldif
Enter LDAP Password:
ldap_bind: Invalid credentials (49)
```

then i tried the other method outlined:

deleted the contents of /var/lib/ldap to get rid of the old databases
used slapadd to add my init.ldif file
chowned /var/lib/ldap to openldap:openldap
restarted slapd

tried an ldapsearch again

invalid credentials.

---

### Post by lokimon on 2010-03-02
gave up on this.  am now trying to get it running on 9.10

it's a real shame that LDAP is so broken under ubuntu.  proper LDAP support is something that needs to be sorted out before universities and businesses can adopt ubuntu.  i know this has been fixed before, but it always seems to get screwed up with each new release.

---

### Post by nyu2007 on 2010-03-02
I have an openldap server on 8.04LTS running.
I can help you. Could you post step by step you do?

---

### Post by nyu2007 on 2010-03-02
Hi Lokimon

This is error of your credential. Try plain text password to test, if ok

Try
- slappasswd -h {SSHA}

And put it to slapd.conf

May be it run :p

---

### Post by lokimon on 2010-03-03
> **nyu2007 said:**
> Hi Lokimon

This is error of your credential. Try plain text password to test, if ok

Try
- slappasswd -h {SSHA}

And put it to slapd.conf

May be it run :p

LDAP of any type is simply horrible to configure and install.  the documentation has not kept up with the releases, and now that they have moved away from slapd.conf it has only gotten worse, because there is next to no documentation about the new database config setup (as opposed to text conf files.)

somehow, i got openLDAP running under ubuntu 9.10, but unfortunately SSL seems to be royally screwed up with that release, so i may try to do this again with 8.04.4

if/when i run into problems i will update this thread.

---

### Post by vinaysagi27 on 2010-03-05
Yes. I have tried openldap in 9.04. It works fine now.

But I need NFS automount **without samba**. 
I have windows and mac clients who has to access centralized storage. My openldap server has to authenticate the users and automount on that storage. Anyone can help me on this..

All document needs slapd.conf file. But in 9.xx series, the slapd structure has been changed.

If you have any idea. Please help me on this.


Regards/Vinay

---

