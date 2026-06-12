---
title: "What does these lines in kern.log mean?"
date: 2010-10-17
forum: Security
---

### Post by claracc on 2010-10-17
I have been seen my kern.log and I have found lines of this kind:

Oct 17 22:23:36 clara1 kernel: [24039.105074] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=75.15.182.95 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=104 ID=30958 DF PROTO=TCP SPT=54807 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 

22:36:51 clara1 kernel: [24833.853838] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=86.177.150.30 DST=192.168.2.100 LEN=52 TOS=0x00 PREC=0x80 TTL=106 ID=4097 DF PROTO=TCP SPT=60480 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 

Oct 17 22:41:19 clara1 kernel: [25101.957924] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=87.219.224.51 DST=192.168.2.100 LEN=64 TOS=0x00 PREC=0x80 TTL=50 ID=89 DF PROTO=TCP SPT=51924 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 

I have only copied three of these lines but there are a lot of them. Could someone explain what is it?, Is there somebody trying to come in my computer?

Thank in advance

---

### Post by OpSecShellshock on 2010-10-17
These appear to be attempts from an external device to initiate a connection to your computer which are being blocked by UFW (or more precisely not allowed to connect per iptables rules). The fact that the destination port (on your end) is 6881 leads me to suspect that the external device is trying to connect by way of a bittorrent client. Either way, it's not successful, so that should only be a problem if you actually want it to connect.

---

### Post by claracc on 2010-10-17
Thanks.

Yes, the 6881 port is that I enable the traffic in when i use ktorrent to download files.

Now it is closed, but when I want to use ktorrent, I open 6881 in ufw. What to do then if I want to use ktorrent?, now I am afraif of opening the port.

---

### Post by claracc on 2010-10-18
Today, also, there are  lots of lines where ufw blocks an ip address (always the same (SRC=79.115.95.78 )to come into my computer:

Oct 18 14:29:08 clara1 kernel: [ 8573.714392] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=79.115.95.78 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=108 ID=53553 DF PROTO=TCP SPT=2142 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 

Oct 18 14:29:55 clara1 kernel: [ 8620.875542] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=79.115.95.78 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=108 ID=60543 DF PROTO=TCP SPT=2294 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 

Oct 18 14:29:58 clara1 kernel: [ 8623.499164] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=79.115.95.78 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=108 ID=60935 DF PROTO=TCP SPT=2294 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 

Oct 18 14:30:04 clara1 kernel: [ 8629.772836] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=79.115.95.78 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=108 ID=61885 DF PROTO=TCP SPT=2294 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 

Oct 18 14:30:51 clara1 kernel: [ 8676.578138] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:bf:58:ea:2a:00:1f:1f:04:ab:41:08:00 SRC=79.115.95.78 DST=192.168.2.100 LEN=48 TOS=0x00 PREC=0x80 TTL=108 ID=3345 DF PROTO=TCP SPT=2438 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 

Of course I won't open my 6881 port in ufw, but how could I get rid of this?. Could I stop in any way these trials to come into my computer?. 

It seems to me that this trials are doing slow my internet connection and I am worried too.

Help please.

---

### Post by SeijiSensei on 2010-10-19
It's quite common to see computers trying to connect to a torrent client after it's closed.  Most clients keep a cache of IP addresses associated with a particular torrent so they aren't routinely requesting them from the tracker.  Eventually they'll update those lists and your address will be deleted.  Until then some peers will continue to try and connect to you.  It's not really dangerous.

You could change the port you use to something in the range of 30000-60000 and open that in your firewall.  Look under Network in the ktorrent configuration dialog.  I use a random high port and leave it open all the time without worry.  If the torrent client isn't running, there won't be anything listening on the port and requests will be ignored.

---

### Post by claracc on 2010-10-19
Thankyou very much for answering.

I am happy to learn there isn't anything to worry about in these kern.log lines.

---

