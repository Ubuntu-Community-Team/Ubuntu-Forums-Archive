---
title: "ldap_bind: Invalid credentials (49)"
date: 2012-04-18
forum: Server Platforms
---

### Post by florenc on 2012-04-18
Hi to all
I am try to config. openldap server on ubuntu. i have follow this : [http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html)
but when i put this command 

**root@ubuntu:/# ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess**

_shows this problem_
**Enter LDAP Password: **
**ldap_bind: Invalid credentials (49)**
the password is secret but doesn't accept .
do you have any suggestion please?
Best Regards

---

### Post by hawkmage on 2012-04-18
A distinguished name will normally not have more than one "cn" .

Looking at the page you gave the link for the DN for the admin user is "cn=admin,dc=example,dc=com"

---

