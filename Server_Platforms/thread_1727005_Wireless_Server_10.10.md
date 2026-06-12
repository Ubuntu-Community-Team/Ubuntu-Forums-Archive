---
title: "Wireless Server 10.10"
date: 2011-04-11
forum: Server Platforms
---

### Post by thep8ntballfreak on 2011-04-11
I just installed ubuntu server, while ive had this setup before it was with a different router.

when i type

sudo iwconfig wlan0 essid WOW!621930

i get the following error

-bash: !621930: even not found

ive tried in quotations as well with the same results any help would be greatly appreciated

---

### Post by papibe on 2011-04-12
The character ! has an special mean to the shell. It calls for the last command that starts with (in your case) 621930. In order to use it you need to escape it using the backslash (\). Like this:
```
$ sudo iwconfig wlan0 essid WOW\!621930
```
Regards.

---

