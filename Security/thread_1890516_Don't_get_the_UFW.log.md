---
title: "Don't get the UFW.log?"
date: 2011-12-03
forum: Security
---

### Post by MadsRC on 2011-12-03
I've been reading up on firewalls and the UFW for iptables, and sofar I'm using these rules:
```
mads@mads-VPCF12M1E:~$ sudo ufw status numbered
[sudo] password for mads: 
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 53/udp                     ALLOW OUT   Anywhere (out)
[ 2] 20,21,80,443,8001/tcp      ALLOW OUT   Anywhere (out)
[ 3] 1863/tcp                   ALLOW OUT   Anywhere (out)
[ 4] 465                        ALLOW OUT   Anywhere (out)
[ 5] 993                        ALLOW OUT   Anywhere (out)
[ 6] 51413                      ALLOW OUT   Anywhere (out)
[ 7] 23399                      ALLOW OUT   Anywhere (out)
[ 8] Anywhere                   DENY OUT    Anywhere (out)
[ 9] 53/udp                     ALLOW OUT   Anywhere (v6) (out)
[10] 20,21,80,443,8001/tcp      ALLOW OUT   Anywhere (v6) (out)
[11] 1863/tcp                   ALLOW OUT   Anywhere (v6) (out)
[12] 465                        ALLOW OUT   Anywhere (v6) (out)
[13] 993                        ALLOW OUT   Anywhere (v6) (out)
[14] 51413                      ALLOW OUT   Anywhere (v6) (out)
[15] 23399                      ALLOW OUT   Anywhere (v6) (out)
[16] Anywhere (v6)              DENY OUT    Anywhere (v6) (out)

```

I've got my conky set up on my dekstop to also show me the content of a few logfiles, and I've noticed that ufw.log still reports a few connections blocked on ports that should be open.

The content of ufw.log states:
```
Dec  3 21:46:11 mads-VPCF12M1E kernel: [  146.415259] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=220.165.8.37 DST=xx.my.ip.xx LEN=40 TOS=0x00 PREC=0x00 TTL=104 ID=256 PROTO=TCP SPT=6000 DPT=65500 WINDOW=16384 RES=0x00 SYN URGP=0 
Dec  3 21:46:36 mads-VPCF12M1E kernel: [  171.163213] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24282 DF PROTO=TCP SPT=54849 DPT=63527 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:37 mads-VPCF12M1E kernel: [  172.266919] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24291 DF PROTO=TCP SPT=54850 DPT=63527 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:38 mads-VPCF12M1E kernel: [  173.377422] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24294 DF PROTO=TCP SPT=54851 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:38 mads-VPCF12M1E kernel: [  173.388441] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24295 DF PROTO=TCP SPT=54852 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:39 mads-VPCF12M1E kernel: [  174.153702] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24298 DF PROTO=TCP SPT=54849 DPT=63527 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:40 mads-VPCF12M1E kernel: [  175.263445] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24302 DF PROTO=TCP SPT=54850 DPT=63527 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:41 mads-VPCF12M1E kernel: [  176.370896] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24305 DF PROTO=TCP SPT=54851 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
Dec  3 21:46:41 mads-VPCF12M1E kernel: [  176.383470] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:14:b7:c6:38:00:1d:a2:e8:63:d9:08:00 SRC=92.145.245.39 DST=xx.my.ip.xx LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=24306 DF PROTO=TCP SPT=54852 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0
```

From what I can see, the following ports are somehow being blocked:
```
Port 80 TCP
Port 443 TCP
Port 63527 TCP
Port 65500 TCP
```

As we can see, port 80 and 443 shouldn't be blocked, but the last two should.

Anyone know why these 2 are reported being blocked? Sometimes it's also port 51413 that's being blocked, though it shouldn't.

I'm running Thunderbird with Gmail, Firefox and Ubuntu One. also got empathy running msn, and when that log was captured, the software center was also running.

Can anyone tell my why the logs report those ports blocked?

---

### Post by oklokl on 2011-12-03
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
&#52280;&#44256; &#54616;&#49464;&#50836;.. 
sudo ufw delete deny out to all
sudo ufw deny in 666,777,9001/tcp

x in out.. ->My out-> download
Others pc -> In 
gufw gul setting 
remove all setting
re reset -> gufw

---

