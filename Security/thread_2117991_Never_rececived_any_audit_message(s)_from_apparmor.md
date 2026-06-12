---
title: "Never rececived any audit message(s) from apparmor."
date: 2013-02-19
forum: Security
---

### Post by arroy_0209 on 2013-02-19
I am using ubuntu12.04 and earlier used 10.04. I have apparmor enforced perhaps one and half year ago but so far have never noticed any audit messages in the system log file viewer except the followings:
> 
audit: initializing netlink socket (disabled)
apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=942 comm="apparmor_parser"
apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk" pid=943 comm="apparmor_parser"
The first one is not even apparmor related but appears in log viewer. There are other profile_load and  profile_replace messages. These make me confused. Is apparmor really active in my ubuntu or did I make some mistake so that either I am not receiving any messages or apparmor is not working the way it is supposed to do? I use firefox 18.0.2.

---

### Post by Doug S on 2013-02-20
All I see in my /var/log/kern.log.1 file is apparmour audit messages from the last re-boot:```
doug@doug-64:~/temp3$ grep apparm /var/log/kern.log.1
Feb 11 17:03:53 doug-64 kernel: [   11.995970] type=1400 audit(1360631030.624:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.996261] type=1400 audit(1360631030.628:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.996421] type=1400 audit(1360631030.628:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.997232] type=1400 audit(1360631030.628:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=470 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.997540] type=1400 audit(1360631030.628:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=470 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.997702] type=1400 audit(1360631030.628:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=470 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.998343] type=1400 audit(1360631030.628:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=484 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.998649] type=1400 audit(1360631030.628:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=484 comm="apparmor_parser"
Feb 11 17:03:53 doug-64 kernel: [   11.998807] type=1400 audit(1360631030.628:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=484 comm="apparmor_parser"
Feb 11 17:03:54 doug-64 kernel: [   15.388327] type=1400 audit(1360631034.020:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1093 comm="apparmor_parser"
```So I thought, why not create an apparmour violation, and look again. My example may seen odd, but I did it because I alreay knew it was a violation. I ran tcpdump and tried to have it automatically execute a program from my local directory after each file rotation. With the default /etc/apparmor.d/usr.sbin.tcpdump file apparmor would not be happy:```
doug@doug-64:~/temp3$ sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 60 -z /home/doug/bin/packet_post_processor
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
compress_savefile:execlp(/home/doug/bin/packet_post_processor, eth1-2013-02-19-21-11-44.bin): Permission denied
compress_savefile:execlp(/home/doug/bin/packet_post_processor, eth1-2013-02-19-21-12-47.bin): Permission denied
...
^C823 packets captured
823 packets received by filter
0 packets dropped by kernel
doug@doug-64:~/temp3$

```O.K. I see the proper stuff in the terminal window, so now check either syslog or kern.log again:```
doug@doug-64:~/temp3$ grep apparm /var/log/kern.log
Feb 19 21:12:47 doug-64 kernel: [706154.293879] type=1400 audit(1361337167.978:19): apparmor="DENIED" operation="exec" parent=20426 profile="/usr/sbin/tcpdump" name="/home/doug/bin/packet_post_processor" pid=20427 comm="tcpdump" requested_mask="x" denied_mask="x" fsuid=0 ouid=1000
Feb 19 21:13:47 doug-64 kernel: [706214.292423] type=1400 audit(1361337227.978:20): apparmor="DENIED" operation="exec" parent=20426 profile="/usr/sbin/tcpdump" name="/home/doug/bin/packet_post_processor" pid=20430 comm="tcpdump" requested_mask="x" denied_mask="x" fsuid=0 ouid=1000
...
```O.K. so I conclude that apparmor is working properly.

---

