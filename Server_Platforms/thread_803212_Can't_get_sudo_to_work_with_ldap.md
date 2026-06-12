---
title: "Can't get sudo to work with ldap"
date: 2008-05-22
forum: Server Platforms
---

### Post by christoffv on 2008-05-22
Hi all

I have setup a ldap server and want to do auth. and sudo. Everything is working when a user logs into a centos server. If the user execute sudo su -, the user gets sudo access. 

My problem is that I have setup an ubuntu server also. The same user can log into the ubuntu server but can't sudo. After the sudo su - command it ask for the sudo password for the client.

I would like any inputs to resolve this query.

Thanks a mil...
Christoff

The syslog:
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 fd=12 ACCEPT from IP=10.8.0.19:60227 (IP=0.0.0.0:389) 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=0 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" method=128 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=0 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" mech=SIMPLE ssf=0 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=0 RESULT tag=97 err=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=1 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uidNumber=1002))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=2 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=shadowAccount)(uid=pietp))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=2 SRCH attr=uid userPassword shadowLastChange shadowMax shadowMin shadowWarning shadowInactive shadowExpire shadowFlag 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=2 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=3 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=root))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=3 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=3 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=4 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=shadowAccount)(uid=root))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=4 SRCH attr=uid userPassword shadowLastChange shadowMax shadowMin shadowWarning shadowInactive shadowExpire shadowFlag 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=4 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=5 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=posixGroup)(cn=sudo))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=5 SRCH attr=cn userPassword memberUid uniqueMember gidNumber 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=5 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=6 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=posixGroup)(cn=admin))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=6 SRCH attr=cn userPassword memberUid uniqueMember gidNumber 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=6 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=7 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(&(objectClass=posixGroup)(cn=sudo))" 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=7 SRCH attr=cn userPassword memberUid uniqueMember gidNumber 
May 22 10:17:55 ubuntu001 slapd[4103]: conn=31 op=7 SEARCH RESULT tag=101 err=0 nentries=0 text= 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 fd=17 ACCEPT from IP=10.8.0.19:60228 (IP=0.0.0.0:389) 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=0 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" method=128 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=0 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" mech=SIMPLE ssf=0 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=0 RESULT tag=97 err=0 text= 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=1 SRCH base="dc=zylex,dc=co,dc=za" scope=2 deref=0 filter="(uid=pietp)" 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=2 BIND anonymous mech=implicit ssf=0 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=2 BIND dn="cn=Piet Pieterse,ou=people,dc=zylex,dc=co,dc=za" method=128 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=2 BIND dn="cn=Piet Pieterse,ou=people,dc=zylex,dc=co,dc=za" mech=SIMPLE ssf=0 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=2 RESULT tag=97 err=0 text= 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=3 BIND anonymous mech=implicit ssf=0 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=3 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" method=128 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=3 BIND dn="cn=admin,dc=zylex,dc=co,dc=za" mech=SIMPLE ssf=0 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 op=3 RESULT tag=97 err=0 text= 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=31 fd=12 closed (connection lost) 
May 22 10:18:03 ubuntu001 slapd[4103]: conn=32 fd=17 closed (connection lost)

The setup on the ubuntu server:

1.Run passwd root

2.Install the package sudo-ldap

3.Install the following packages: ldap-utils. Libpam-ldap

4.During installation, you will be asked the following questions: 
Should debconf manage LDAP configuration? Yes
LDAP server Uniform Resource Identifier: ldap://10.8.0.10
Distinguished name of the search base: dc=zylex,dc=co,dc=za
LDAP version to use: 3
Make local root Database admin? Yes
Does the LDAP database require login? No
 LDAP account for root: cn=admin,dc=zylex,dc=co,dc=za
Your root password. 

5.Edit /etc/ldap.conf
host 10.8.0.10 
base dc=zylex,dc=co,dc=za 
ldap_version 3 
rootbinddn cn=admin,dc=zylex,dc=co,dc=za 
pam_password md5 
sudoers_base   ou=SUDOers,dc=zylex,dc=co,dc=za

6.If the file /etc/ldap.secret is not present, create and put the rootbinddn password in this file.

7.Change the properties of this file to,
-rw------- 1 root root 8 2008-05-20 08:16 /etc/ldap.secret

8.Edit /etc/pam.d/common-account
account sufficient      pam_ldap.so
account required        pam_unix.so
/etc/pam.d/common-auth
auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure

/etc/pam.d/common-password
password        sufficient      pam_ldap.so
password        required   pam_unix.so nullok obscure min=4 max=8 md5

/etc/pam.d/common-session
session required        pam_unix.so 
session required        pam_mkhomedir.so skel=/etc/skel/ 
session sufficient      pam_ldap.so 
session optional        pam_foreground.so

/etc/nsswitch.conf
and once you're in that file, run this command: 
:%s/compat/ldap files/g

/etc/ldap/ldap.conf
BASE    dc=zylex,dc=co,dc=za 
HOST    10.8.0.10

---

### Post by bonevg on 2009-09-10
Same problem here. Managed to get the Auth working, but sudo didn't work.

I was about to ask if some1 came with resolution.
Anyway while I wrote the 1st line of this post.. the college of mine sitting next to me managed to get it working.

So I'll let you know how he did it.

vim /etc/ldap/ldap.conf

then it should look like this:

```
BASE dc=XXXXX, dc=XX
URI ldap://ip.ip.ip.ip

sudoers_base ou=SUDOers,dc=XXXX,dc=XX
binddn cn=sudoers,dc=XXXX,dc=XX
bindpw secret
sudoers_debug 2
```

So you may ask yourself what would be wrong.. I did it the same way.
Well here is the funny part:

[LIST=1]
[*]CentOS uses /etc/ldap.conf
[*]Ubuntu uses /etc/ldap/ldap.conf
[/LIST]

Gooooo Figure! Such a mess.. Seems every distro behave on its own.. Sometimes this can take hours just to figure that you configured the wrong conf file. Good Luck and Beer for every1 / :beer:

---

