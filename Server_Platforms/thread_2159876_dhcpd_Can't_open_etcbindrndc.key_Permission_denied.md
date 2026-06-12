---
title: "dhcpd: Can't open /etc/bind/rndc.key: Permission denied"
date: 2013-07-04
forum: Server Platforms
---

### Post by damateem on 2013-07-04
I recently performed an upgrade using

```
sudo apt-get upgrade
```

dhcp3 was one of the packages that was upgraded.

After the upgrade, the dhcp server fails to start.

When I try to start the server using

```
sudo /etc/init.d/dhcp3-server restart
```

I get the message

```
dhcpd: Can't open /etc/bind/rndc.key: Permission denied
```

I've done some research and tried changing ownership and permissions on rndc.key, but I continue to get the permission error.

At this point, I'm not sure what to try next. Any help would be greatly appreciated.

---

### Post by nemilar on 2013-07-05
Could you post the output of these?

```
ls -l /etc/bind/rndc.key
ls -ld /etc/bind/
stat /etc/bind/rndc.key

```

---

### Post by damateem on 2013-07-05
```
ls -l /etc/bind/rndc.key
-rw-r----- 1 bind dhcpd 77 Dec 31  2010 /etc/bind/rndc.key
```

```
ls -ld /etc/bind/
drwxr-sr-x 2 root bind 4096 Apr 14 19:57 /etc/bind/
```

```
stat /etc/bind/rndc.key
  File: `/etc/bind/rndc.key'
  Size: 77              Blocks: 8          IO Block: 4096   regular file
Device: fb00h/64256d    Inode: 4457660     Links: 1
Access: (0640/-rw-r-----)  Uid: (  104/    bind)   Gid: (  114/   dhcpd)
Access: 2013-07-02 22:57:18.434182007 -0400
Modify: 2010-12-31 12:16:03.411208154 -0500
Change: 2013-07-04 15:01:19.474074762 -0400
```

---

### Post by nemilar on 2013-07-05
Just a guess, but have you tried:

```
chmod 440 /etc/bind/rndc.key
```

---

### Post by damateem on 2013-07-05
Yes, but I tried again just now.

```
ls -l rndc.key
-r--r----- 1 bind dhcpd 77 Dec 31  2010 rndc.key
```

Same result.

```
sudo /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was:
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Can't open /etc/bind/rndc.key: Permission denied
```

---

