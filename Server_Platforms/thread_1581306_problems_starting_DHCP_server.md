---
title: "problems starting DHCP server"
date: 2010-09-24
forum: Server Platforms
---

### Post by BarryDocks on 2010-09-24
I have previously set up DHCP server to dynamically update BIND9 DNS server using ubuntu 8.04 several time without a problem, mainly using this method:
[http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable]("http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable")

Trying to do the same on Ubuntu 10.04 but keep getting this error when starting the dchp server
```
/etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Can't open /etc/bind/rndc.key: Permission denied

```

here are the permissions for the /etc/bind/rndc.key file:
```
root@Server64:~# ls -l /etc/bind/rndc.key
-rw-r--r-- 1 bind bind 71 2010-09-24 22:58 /etc/bind/rndc.key

```

I really can't see why this is a problem?:confused:

---

### Post by sikander3786 on 2010-09-24
This might help.

[http://ubuntuforums.org/showthread.php?t=1198162](http://ubuntuforums.org/showthread.php?t=1198162)

---

### Post by BarryDocks on 2010-09-25
Thankyou

I added the following lines to the dhcp3 apparmor profile as per the link provided:
```
/etc/bind/ r,
/etc/bind/** r,
```

Now works without a problem:popcorn:

---

