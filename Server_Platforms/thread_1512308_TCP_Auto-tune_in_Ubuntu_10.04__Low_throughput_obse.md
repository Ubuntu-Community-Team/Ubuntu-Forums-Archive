---
title: "TCP Auto-tune in Ubuntu 10.04 :: Low throughput observed in Simultanious FTP (TCP)"
date: 2010-06-18
forum: Server Platforms
---

### Post by ranjish on 2010-06-18
Hi All,
 
Setup: Ubuntu 10.04 as FTP Server/ Iperf Server
Win7 as Client machine
 
Single FTP upload or download works fine, desired throughput acheived.
But when Simultanious ftp is tested, there is huge varaition in throughput. I think ubuntu is priotrizing download more than upload.
Is there a way we can give equal priority to Ftp upload and ftp download.
 
Tested the same with iperf utiltiy, same results observed under simultanious iperf tcp upload and tcp download.
simultanious udp upload and download works fine.
 
Dosent Ubuntu 10.04 autotune TCP settings like Windows 7 and vista OS ?
 
 
-RaNjI

---

### Post by denarced on 2010-06-20
Are we talking gigabit network or 100mbit?
What kind of hardware are you working with? Router in between or a switch?

Windows 7 does something for uploads and downloads. There's some kind of optimization going on. I noticed this when I could download 80MB/s with win7 and only about 45MB/s with Ubuntu.

---

### Post by ranjish on 2010-06-29
> **denarced said:**
> Are we talking gigabit network or 100mbit?
What kind of hardware are you working with? Router in between or a switch?

Windows 7 does something for uploads and downloads. There's some kind of optimization going on. I noticed this when I could download 80MB/s with win7 and only about 45MB/s with Ubuntu.

Its a 100Mbit network.
The applications that i use hardly take more than 30Mbps simultaneous in both the direction.

I have tried with Switch, router and without them as well. No change in my simultaneous throughput.
If i replace ubuntu server with a windows 2003 server I am able to achieve excellent throughput with the same hardware configurations.

Any help is much appreciated.
-Ranjish

---

### Post by bburbank on 2011-11-21
I know this outdated for the OP to use, but for anyone else coming across this, the solution is to edit your */etc/sysctl.conf* file by adding the following line:

```
net.ipv4.tcp_window_scaling=0
```


---all Windows Vista machines appear to have this problem too, if you have them in your environment the fix is to type the following at the command line once from an admin account:

```
netsh interface tcp set global autotuninglevel=disabled
```

from what I can tell, the source of this problem is the firewall, I've seen this with a Sonicwall hardware appliance and an OpenBSD box setup as a router.  I never found the source problem, but the above fix worked for the desktops in both environments.

---

