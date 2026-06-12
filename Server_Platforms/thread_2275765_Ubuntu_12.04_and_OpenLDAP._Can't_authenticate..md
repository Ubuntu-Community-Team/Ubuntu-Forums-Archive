---
title: "Ubuntu 12.04 and OpenLDAP. Can't authenticate."
date: 2015-04-28
forum: Server Platforms
---

### Post by yaztromo on 2015-04-28
Ok this seems like a common problem judging by the number of posts on the Internet about this, and I'm equally as stumped.

Extra complication is that most guides recommend edit slapd.conf, which is no longer used on 12.04.

I followed this guide to the letter:

[https://help.ubuntu.com/lts/serverguide/openldap-server.html](https://help.ubuntu.com/lts/serverguide/openldap-server.html)

I get to the part where it wants:

```
ldapadd -x -D cn=admin,dc=example,dc=com -W -f add_content.ldif
```

Enter the password I chose during slapd install and this happens:

```
ldap_bind: Invalid credentials (49)
```

I can't get past this stage. I've tried numerous solutions on the Internet which usually involve changing olcRootPassword but nothing helps.

---

