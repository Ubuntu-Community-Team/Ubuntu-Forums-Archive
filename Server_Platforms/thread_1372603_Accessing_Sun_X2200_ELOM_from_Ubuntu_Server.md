---
title: "Accessing Sun X2200 ELOM from Ubuntu Server"
date: 2010-01-04
forum: Server Platforms
---

### Post by tr333 on 2010-01-04
How can I access the ELOM on a Sun Fire X2200 from Ubuntu-server?
I've tried to use the links2 browser (gui mode) over a ssh session with x-forwarding but the frames support (or something else) appears to not work properly when browsing the site after login.  I've also tried to connect with ipmitool but it just gives an error.
```
$ ipmitool -H 10.0.0.4 -U root mc info
Password:
Activate Session command failed
Error: Unable to establish LAN session
Get Device ID command failed
```

---

