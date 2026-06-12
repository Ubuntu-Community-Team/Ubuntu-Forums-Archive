---
title: "Kerberos and LDAP - LDAP ACL"
date: 2012-06-13
forum: Server Platforms
---

### Post by nvigier on 2012-06-13
Hi everyone,

I've been following the Ubuntu Server Guide (12.04) to install and configure Kerberos, LDAP and have them work together.
I'm stuck at the 3.7 step on Configuring LDAP and have this error:
> root@master:~# ldapmodify -x -D cn=admin,cn=config -W
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
replace: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange,krbPrincipalKey by
 dn="cn=admin,dc=human-city,dc=com" write by anonymous auth by self write by * none 
-
add: olcAccess
olcAccess: to dn.base="" by * read
-
add: olcAccess: to * by dn="cn=admin,dc=human-city,com" write by * read

modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Other (e.g., implementation specific) error (80)
	additional info: <olcAccess> handler exited with 1

Thank you.

---

### Post by kennethconn on 2012-06-14
```
olcAccess: to attrs=userPassword,shadowLastChange,krbPrincipalKe y by
```
 
There is an extra space here at Ke y, but that might just be for this post. 
Put it in an LDIF file and use that instead with the -f switch (show the contents of the LDIF file here). Also use the -v switch with the ldapmodify command to see if it gives you more info.
 
replace and add in this way can be tricky so if I were you I would check out the relevant section at:
 
[http://www.openldap.org/devel/admin/slapdconf2.html](http://www.openldap.org/devel/admin/slapdconf2.html)

---

### Post by nvigier on 2012-06-15
I tried what you proposed, didn't work, then I tried this:
```
root@master:~# ldapmodify -x -D cn=admin,cn=config -W -v
ldap_initialize( <DEFAULT> )
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
changetype: modify
replace: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange,krbPrincipalKey by dn="cn=admin,dc=human-city,dc=com" write by anonymous auth by self write by * none
-
add: olcAccess
olcAccess: to dn.base="" by * read
-
add: olcAccess
olcAccess: to * by dn="cn=admin,dc=human-city,dc=com" write by * read

replace olcAccess:
	to attrs=userPassword,shadowLastChange,krbPrincipalKey by dn="cn=admin,dc=human-city,dc=com" write by anonymous auth by self write by * none
add olcAccess:
	to dn.base="" by * read
add olcAccess:
	to * by dn="cn=admin,dc=human-city,dc=com" write by * read
modifying entry "olcDatabase={1}hdb,cn=config"
modify complete

```
But it's stuck here.

Thank you!

EDIT: I killed the command and checked the file, it seems to have worked!

Thank you again,
Nicolas

---

