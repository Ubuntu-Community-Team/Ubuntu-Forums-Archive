---
title: "Webmin and Ubuntu Server 10.04"
date: 2010-04-29
forum: Server Platforms
---

### Post by CharlesA on 2010-04-29
Since a few of the init.d scripts have been changed to upstart scrips, it looks like you just need to edit the module config of whatever servers you are configuring with webmin.

Example:

To stop Samba:

```
service smbd stop
```

To start Samba:

```
service smbd start
```

Just figured I'd throw that out there if anyone is having problems using Webmin with 10.04. :)

---

