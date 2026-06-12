---
title: "Concerning netstat results?"
date: 2007-11-26
forum: Server Platforms
---

### Post by twill30 on 2007-11-26
Hi -- just ran a netstat on our server and got the following UDP connections. Could someone let me know if this is normal, or of concern...

udp        0      0 s1527xxxx.onlineh:49197 Powered.by.Root24.e:ntp ESTABLISHED
udp        0      0 s1527xxxx.onlineh:49198 node00.mneisen.org:ntp  ESTABLISHED
udp        0      0 s1527xxxx.onlineh:49199 unixforge.de:ntp        ESTABLISHED
udp        0      0 s1527xxxx.onlineh:49200 pax.mosquito.net:ntp    ESTABLISHED
udp        0      0 s1527xxxx.onlineh:49201 patrick-nagel.net:ntp   ESTABLISHED
udp        0      0 *:bootpc                *:*
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     313937   /var/run/mysqld/mysqld.sock
unix  2      [ ]         DGRAM                    2018     @/org/kernel/udev/udevd
unix  4      [ ]         DGRAM                    265707   /dev/log
unix  2      [ ]         DGRAM                    313935
unix  2      [ ]         DGRAM                    266394
unix  3      [ ]         STREAM     CONNECTED     266391
unix  3      [ ]         STREAM     CONNECTED     266390
unix  2      [ ]         DGRAM                    215027
unix  2      [ ]         DGRAM                    215026
unix  3      [ ]         STREAM     CONNECTED     15951
unix  3      [ ]         STREAM     CONNECTED     15950
unix  2      [ ]         DGRAM                    15949
unix  2      [ ]         DGRAM                    15655

---

### Post by colo on 2007-11-26
In case your system is configured to use NTP (Network Time Protocol, used to synchronize hosts' clocks over networks) and DHCP (Dynamic Host Configuration Protcol, used to propagate network settings automagically), there's no need to worry.

---

### Post by twill30 on 2007-11-26
Thanks for the reply! It's a case of learning as we go... don't wish to be lax in our vigilance.

---

