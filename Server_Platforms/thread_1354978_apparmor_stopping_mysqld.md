---
title: "apparmor stopping mysqld"
date: 2009-12-14
forum: Server Platforms
---

### Post by Xiuh on 2009-12-14
I'm consistently getting this audit from apparmor. 


```
Dec 14 02:30:16 revco kernel: [   26.908476] type=1503 audit(1260779416.020:18): operation="open" pid=979 parent=871 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
```

I looked back in my logs to get an idea when it started and it appears since I setup a default LAMP server. The usr.sbin.mysqld apparmor profile doesn't have any audit comments in the file. Furthermore, I've checked my etc/mysql files for anything that might explain why mysql is digging into this directory, but found nothing. This starting directly after the default install, I'd assume the apparmor would have a comment stating why it's stopping the daemon from accessing this folder, so I'm curious what I've got going on here. Can anyone give me a heads up on this?

---

