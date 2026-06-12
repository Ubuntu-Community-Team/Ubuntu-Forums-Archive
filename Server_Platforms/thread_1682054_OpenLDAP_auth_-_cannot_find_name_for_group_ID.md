---
title: "OpenLDAP auth - cannot find name for group ID"
date: 2011-02-05
forum: Server Platforms
---

### Post by thesti on 2011-02-05
Hello,

I've installed OpenLDAP and libnss-ldap, as instructed in [this]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html") tutorial. Then I try to login but I got the error 

```
groups: cannot find name for group ID 10000
```

Here's the user and group ldif entry that I use to login

```

dn: uid=iwan,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: iwan
sn: Doe
givenName: iwan
cn: iwan Doe
displayName: iwan Doe
uidNumber: 1000
gidNumber: 10000
userPassword: 123456
gecos: iwan Doe
loginShell: /bin/bash
homeDirectory: /home/iwan
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: iwan.doe@example.com
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress: 
initials: SC


dn: cn=example,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example
gidNumber: 10000

```

Wonder why the group name is not found? Hope someone could help.

Thank you.

---

### Post by luvshines on 2011-02-05
What do following say```

getent passwd iwan

getent group example
```

---

### Post by thesti on 2011-02-05
Hello,

"getent passwd iwan" returns

```
iwan:x:1000:10000:iwan Doe:/home/iwan:/bin/bash
```

while "getent group example" returns nothing


Thanks

---

### Post by luvshines on 2011-02-06
What is written in /etc/nsswitch.conf against these entries```

passwd:
group:
```

---

### Post by thesti on 2011-02-06
Hello luvshines,

Here is what is written in nsswitch.conf against those entries

```

passwd: files ldap
group: files ldap

```


Thanks

---

### Post by luvshines on 2011-02-06
Ok, nsswitch too looks gud

Make sure that you are able to ldapsearch that group.
Check if nss_base_* appear in your /etc/ldap.conf, they are set with proper suffixes(dc=example,dc=com)

---

### Post by thesti on 2011-02-06
Hello. Thanks luvshines, it works!

I could search ldap for the group example, then I search /etc/ldap.conf for nss_base_* entries. I saw this nss_base_group entry and its value is "ou=Group,dc=padl,dc=com?one". It is pointing to the Group ou, while I put the "example" group in Groups ou. I thought maybe that's the problem. So, I uncomment that line, and changed the value to

```

nss_base_group          ou=groups,dc=example,dc=com?sub

```The error "cannot find name for group id xxx" is gone. I am able to login as my ldap user (iwan), but then after successfully logging in, I see the prompt is still 

```

administrator@server1:~$

```I type "whoami" and it gives the respond "administrator". Does the login is successful? But basically, the case is solved. Thank you luvshines!

---

### Post by luvshines on 2011-02-06
Maybe 1000 UID points to some local user named "administrator" in /etc/passwd file```

egrep "administrator|:1000:" /etc/passwd
```

---

