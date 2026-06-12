---
title: "Cannot access ubuntu server via hostname..."
date: 2009-05-30
forum: Server Platforms
---

### Post by ubila on 2009-05-30
Hello all :D

Im having trouble accessing my ubuntu 8.10 server running samba from my windows xp home sp2 machine ONLY when using hostname.

I can successfully access it using IP address eg .. \\192.168.2.43\dev
But cannot access it using the ubuntu hostname eg .. \\host1.my.com\dev

my hostname is setup as host1.my.com with ip address 192.168.2.43
i am able to ping this ip address from windows cmd, but cannot ping the hostname.
it does however work if i ping host1 (without the .my.com on the end)

Any ideas?

Cheers

---

### Post by roman_platonov on 2009-05-30
you need setup dns server on ubuntu server and make changes in network settings on clients (if you use static ip), or on dhcp server

---

### Post by cariboo on 2009-05-30
Edit the hosts file in C:\WINDOWS\system32\drivers\etc

```
# Copyright (c) 1993-1999 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost
192.168.2.43    host1.my.com


```

It's a lot easier than installing bind9. If you have several computers on your network you may want to install dnsmasq on the server. It is available in the repositories.

---

