---
title: "where to find dhcp leases?"
date: 2008-12-09
forum: Server Platforms
---

### Post by jpgeerets on 2008-12-09
hi
im running a dhcp3 server on ubuntu.
now i want to see who is using my ip-addresses.
there is a file:
/var/lib/dhcp/dhcpd.leases
but this one is empty.

can any tell me where i can find the active leases?

thanks in advanced

Jean-Paul

---

### Post by cdenley on 2008-12-09
That's where active leases are stored for me. Are you sure there are active leases on that server?
```

tail /var/log/dhcpd.log

```

---

### Post by jpgeerets on 2008-12-09
well,
i know my clients get an ip-adres of the server.
it's the only dhcp on this subnet.

i can not find the file you named.

any ideas?

Jean-Paul

---

### Post by jpgeerets on 2008-12-19
someone any idea?

---

### Post by cdenley on 2008-12-19
```

sudo lsof -p `cat /var/run/dhcp3-server/dhcpd.pid`

```
This will list all files your dhcp server has open. This is my output:
```

COMMAND   PID  USER   FD   TYPE             DEVICE    SIZE     NODE NAME
dhcpd3  22480 dhcpd  cwd    DIR                8,1    4096        2 /
dhcpd3  22480 dhcpd  rtd    DIR                8,1    4096        2 /
dhcpd3  22480 dhcpd  txt    REG                8,1  572608 96700687 /usr/sbin/dhcpd3
dhcpd3  22480 dhcpd  mem    REG                8,1   47528 64668402 /lib/libnss_files-2.7.so
dhcpd3  22480 dhcpd  mem    REG                8,1 1436976 64668390 /lib/libc-2.7.so
dhcpd3  22480 dhcpd  mem    REG                8,1   15080 64667780 /lib/libcap.so.1.10
dhcpd3  22480 dhcpd  mem    REG                8,1  127480 64668384 /lib/ld-2.7.so
dhcpd3  22480 dhcpd  mem    REG                8,1  217016 59769910 /var/cache/nscd/services
dhcpd3  22480 dhcpd  mem    REG                8,1  217016 59769909 /var/cache/nscd/group
dhcpd3  22480 dhcpd  mem    REG                8,1  217016 59769822 /var/cache/nscd/passwd
**dhcpd3  22480 dhcpd    1w   REG                8,1   25679 59375963 /var/lib/dhcp3/dhcpd.leases**
dhcpd3  22480 dhcpd    3u  unix 0xffff81003c480840         12764038 socket
dhcpd3  22480 dhcpd    4u   raw                            12764037 00000000:0001->00000000:0000 st=07
dhcpd3  22480 dhcpd    5u  IPv4           12764043              UDP *:bootps 
dhcpd3  22480 dhcpd    7u  sock                0,4         12764041 can't identify protocol
dhcpd3  22480 dhcpd    8u  sock                0,4         12764042 can't identify protocol

```

---

### Post by jpgeerets on 2008-12-19
cool!
thats a fast reply!
tnx!!

i will try it monday when im at work again!

have a good weekend!!

Jean-Paul

---

### Post by jpgeerets on 2008-12-22
hi!

yeah,this works great!!
this works. 
i also have reconfigured webmin, and now i can easily see the current leases!!!

thanks again!

Jean-Paul

---

