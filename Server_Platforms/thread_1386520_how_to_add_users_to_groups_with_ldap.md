---
title: "how to add users to groups with ldap"
date: 2010-01-20
forum: Server Platforms
---

### Post by 2handband on 2010-01-20
Could someone please point me to some information on how to add existing users to existing groups in an openldap environment? Every tutorial I've come across assumes you know what you're doing, and frankly I don't. I got ldap working more by luck than skill. So far I've created the following ldif file:

```
dn: cn=johnstones,ou=Groups,dc=newcrossroads,dc=net
changetype: modify
add: uniquemember
uniquemember: cn=jess
```

And I'm running this command with this output:

```
robert:~# ldapmodify -x -D cn=admin,dc=newcrossroads,dc=net -W -f /var/tmp/adduser.ldif
Enter LDAP Password:
modifying entry "cn=johnstones,ou=Groups,dc=newcrossroads,dc=net"
ldap_modify: Object class violation (65)
        additional info: attribute 'uniqueMember' not allowed
```

I've tried using "member" instead of "uniqumember". Can anybody help? I've been fighting with this thing for three days.

---

