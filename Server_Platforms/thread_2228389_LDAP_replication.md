---
title: "LDAP replication"
date: 2014-06-07
forum: Server Platforms
---

### Post by gb10hkzo-fb on 2014-06-07
Hi,

Am running 14.04LTS, but followed the instructions at [https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html) for replication.

Under testing it says *"Once replication starts, you can monitor it by running     **ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN"*

However on my machines I get nothing back, i.e :
```

$ ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN
dn:

```

Syslog has the following to day on the consumer :
```
 do_syncrep2: rid=234 LDAP_RES_SEARCH_RESULT (53) Server is unwilling to perform
 do_syncrep2: rid=234 (53) Server is unwilling to perform
 do_syncrepl: rid=234 rc -2 retrying
 do_syncrep2: rid=234 (4096) Content Sync Refresh Required

```

I have double checked all the ldif config file elements (dn, password etc..) and they are all correct.

The weird thing is, something seems to be happening, because if I add an OU on the provider, replicaiton (eventually) seems to be happening on the consumer because it gets listed by :
[I]sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b dc=example,dc=com dn

[/I][SIZE=5][/SIZE][SIZE=3][/SIZE][SIZE=4]How can I be sure my LDAP sysc is properly configured and not half broken ?[/SIZE][I]
[/I]

---

### Post by elico on 2014-06-12
The link to the guide is broken giving me 404 page not found.

---

