---
title: "changing ldap password from client"
date: 2011-04-12
forum: Server Platforms
---

### Post by gettons on 2011-04-12
Hi all,


I have been playing a bit with openldap on my router with openwrt Backfire 10.03.1-rc4 on it.
It has a package already compiled, the drawback is that the database is ldif type only ( because of the hardware, being just a broadband router ).

Firstly on my server I configured slapd.conf 
> 

access to *
  by self write
  by anonymous read
  by dn="cn=Manager,dc=linux,dc=gettolandia,dc=org" write
  by * read


and then I started building the 3 ldif files against which, in turn, I run
ldapadd -x -D "cn=Manager,dc=linux,dc=gettolandia,dc=org" -W -f base.ldif
ldapadd -x -D "cn=Manager,dc=linux,dc=example,dc=org" -W -f users.ldif
ldapadd -x -D "cn=Manager,dc=linux,dc=example,dc=org" -W -f groups.ldif

An example from users.ldif is the following one:

> 


dn: uid=boo,ou=People,dc=linux,dc=gettolandia,dc=org
uid: boo
cn: Piccola Boo
objectclass: account
objectclass: posixAccount
objectclass: top
objectclass: shadowAccount
shadowMax: 99999
shadowWarning: 7
userPassword: {SSHA}VqFWUsG/S6BJMkAnXAISFHLOxjbcd9ic
loginShell: /bin/bash
uidNumber: 9001
gidNumber: 9001
homeDirectory: /home/boo
gecos: Boo






Then I set my client workstation up with auth 
authconfig-tui --disablefingerprint 
after the installation of some rpm packages needed ( nss_ldap ... openldap ... )
and I have added
> 
pam_password ssha

to nss_ldap configuration file.

I can getent passwd on the client, I can su - USERONLDAP, I can connect with ssh USERONLDAP@client
Then I tried to change the pass, I get a question about the current LDAP password, I fill in the password and then a new one.

Then I try again to connect locally doing su - USERONLDAP , ssh USERONLDAP@client and it brillianty works.

I can ldapsearch and I presume the below password is the new one I have just changed.

> 
# boo, People, linux.gettolandia.org
dn: uid=boo,ou=People,dc=linux,dc=gettolandia,dc=org
uid: boo
cn: Piccola Boo
objectClass: account
objectClass: posixAccount
objectClass: top
objectClass: shadowAccount
shadowMax: 99999
shadowWarning: 7
userPassword:: e1NTSEF9VnFGV1VzRy9TNkJKTWtBblhBSVNGSExPeGpiY2Q5aWM=
loginShell: /bin/bash
uidNumber: 9001
gidNumber: 9001
homeDirectory: /home/boo
gecos: Boo



The problem is that if I try to run passwd again to change the password ( as USERONLDAP on the client machine ) once I fill in the current password, I get the following error:

> 
boo@clientmachine ~]$ passwd
Changing password for user boo.
Enter login(LDAP) password:
LDAP Password incorrect: try again


I tried with both of them, the old one and the new one.

The log says:
> 
Apr 12 16:18:50 clientmachine passwd: pam_ldap: error trying to bind as user "uid=boo,ou=People,dc=linux,dc=gettolandia,dc=org" (Invalid credentials)






TIA



Tommaso

---

