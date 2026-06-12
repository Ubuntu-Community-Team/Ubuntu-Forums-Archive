---
title: "UFW blocks some nfs mount requests"
date: 2017-05-05
forum: Server Platforms
---

### Post by gabi16062 on 2017-05-05
Hi all,

I have a home server that runs Ubuntu 16.04.2 LTS server edition. It has both Samba and NFS shares. Everything works fine from the point of(re)configuring UFW for about a month. After that UFW blocks the mount requests for two of the four NFS shares. here's a part of **dmesg**'s output:
```
[ 1708.343500] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=22339 DF PROTO=UDP SPT=45799 DPT=53549 LEN=48
[ 1709.346615] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=12338 DF PROTO=TCP SPT=33355 DPT=47111 WINDOW=27280 RES=0x00 SYN URGP=0
[ 1710.343402] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=12339 DF PROTO=TCP SPT=33355 DPT=47111 WINDOW=27280 RES=0x00 SYN URGP=0
[ 1712.347481] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=12340 DF PROTO=TCP SPT=33355 DPT=47111 WINDOW=27280 RES=0x00 SYN URGP=0
[ 1716.355484] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=12341 DF PROTO=TCP SPT=33355 DPT=47111 WINDOW=27280 RES=0x00 SYN URGP=0
[ 1719.426441] [UFW BLOCK] IN=ham0 OUT= MAC=7a:79:19:16:03:f2:7a:79:19:6e:f3:35:08:00 SRC=25.110.243.53 DST=25.22.3.242 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=22651 DF PROTO=UDP SPT=46204 DPT=53549 LEN=48
```
The full output is [here]("https://paste.ubuntu.com/24236901/") if needed. If i disable/reconfigure UFW, all the nfs shares can be mounted again on the client, which is Deepin 15.4 by the way. Here's the full list of firewall rules:
```
Címzett                    M&#369;velet     Feladó
-------                    -------     ------
22/tcp                     ALLOW IN    25.110.243.53
443/tcp                    ALLOW IN    25.110.243.53
8080/tcp                   ALLOW IN    25.110.243.53
2049/udp                   ALLOW IN    25.110.243.53
80                         ALLOW IN    Anywhere
139/tcp                    ALLOW IN    192.168.0.0/24
137/tcp                    ALLOW IN    192.168.0.0/24
139/udp                    ALLOW IN    25.110.243.53
137/udp                    ALLOW IN    25.110.243.53
2049/tcp                   ALLOW IN    25.110.243.53
2049/udp                   ALLOW IN    25.110.243.53
80 (v6)                    ALLOW IN    Anywhere (v6)
22/tcp                     ALLOW IN    2620:9b::196e:f335/96
443/tcp                    ALLOW IN    2620:9b::196e:f335/96
8080/tcp                   ALLOW IN    2620:9b::196e:f335/96
139/tcp                    ALLOW IN    2620:9b::196e:f335/96
137/tcp                    ALLOW IN    2620:9b::196e:f335/96
```
**rpcinfo -p | grep nfs** shows that ports used by nfs are 2049/tcp and 2049/udp. The reason i didn't add them to ipv6 is that nfs does not work with ipv6 for me.
And please don't comment anything like 'the problem must be with the Chinese OS', which was the first reply on another forum. Also I have a friend, who uses Ubuntu 14.04.5 LTS server edition and Linux Mint 17.3 and has exactly the same problem.

---

### Post by steeldriver on 2017-05-05
Hello and welcome to the forums

Not sure if this is still the case, but in the past I have had to fix (and allow) the rpc.mountd port as described here:

[https://ubuntuforums.org/showthread.php?t=2337565&p=13547667#post13547667](https://ubuntuforums.org/showthread.php?t=2337565&p=13547667#post13547667)

You may also need to allow port 111 (rpc portmapper)

---

### Post by gabi16062 on 2017-05-12
I tried it and it still doesn't work. I've added a rule to allow any request from that host ```
sudo ufw allow from 25.110.243.53 to any
``` It's working with this, but for security reasons, i don't want to open every port.

---

### Post by darkod on 2017-05-12
Have you tried using iptables instead of ufw? ufw is a frontend for iptables but it doesn't seem to be very "clean"... It might not be handling established traffic as well as iptables does where you can specifically tell it to allow established and related traffic. Maybe that part will help you.

I suggest to use iptables and see how it goes.

---

