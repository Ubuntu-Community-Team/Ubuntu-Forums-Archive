---
title: "LDAP and TLS issues on 10.10"
date: 2010-11-11
forum: Server Platforms
---

### Post by ryankask on 2010-11-11
Hi! I am trying to setup TLS using the instructions found at [https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html). I've installed all the certificates but when I run slapd with debugging, I get this error when trying to connect from Apache Directory browser:


```
connection_get(16): got connid=1002
connection_read(16): checking for input on id=1002
connection_get(16): got connid=1002
connection_read(16): checking for input on id=1002
connection_get(16): got connid=1002
connection_read(16): checking for input on id=1002
connection_read(16): unable to get TLS client DN, error=49 id=1002
connection_get(16): got connid=1002
connection_read(16): checking for input on id=1002
ber_get_next

```

How can I get this working?

Thanks!

Ryan

---

### Post by - Lo - on 2011-01-29
Hi ryankask,

I am experiencing the same problem after following the same guide...did you find a solution?

Thanks in advance!

- Lo -

---

