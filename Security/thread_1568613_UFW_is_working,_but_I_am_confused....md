---
title: "UFW is working, but I am confused..."
date: 2010-09-05
forum: Security
---

### Post by uRock on 2010-09-05
UFW is blocking someone from trying to connect, but I am confused by how they are getting passed my router if my system has nothing running that is network aware when I started observing the log, except for Pidgin. I ran whois o the IP and it is a Google server. Any thoughts on what may be causing and if any action needs to be taken? Here is today's ufw.log.

```
Sep  5 11:20:27 rabbit-desktop kernel: [33232.187832] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=95.79.94.20 DST=192.168.156.100 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=41832 DPT=58570 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 11:20:47 rabbit-desktop kernel: [33252.374680] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=95.172.109.93 DST=192.168.156.100 LEN=95 TOS=0x00 PREC=0x00 TTL=117 ID=17942 PROTO=UDP SPT=18065 DPT=51413 LEN=75 
Sep  5 11:20:56 rabbit-desktop kernel: [33261.512225] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=87.153.229.207 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=110 ID=28130 PROTO=UDP SPT=40133 DPT=51413 LEN=38 
Sep  5 11:20:59 rabbit-desktop kernel: [33264.460134] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=87.153.229.207 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=110 ID=28661 DF PROTO=UDP SPT=40133 DPT=51413 LEN=38 
Sep  5 11:21:06 rabbit-desktop kernel: [33271.644131] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=83.183.211.238 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=116 ID=4317 PROTO=UDP SPT=26212 DPT=51413 LEN=38 
Sep  5 11:21:09 rabbit-desktop kernel: [33274.675960] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=83.183.211.238 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=116 ID=4599 PROTO=UDP SPT=26212 DPT=51413 LEN=38 
Sep  5 11:21:13 rabbit-desktop kernel: [33278.169899] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=24.119.221.18 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=120 ID=16951 PROTO=UDP SPT=44121 DPT=51413 LEN=38 
Sep  5 11:21:16 rabbit-desktop kernel: [33281.186993] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=24.119.221.18 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=120 ID=17238 PROTO=UDP SPT=44121 DPT=51413 LEN=38 
Sep  5 11:21:18 rabbit-desktop kernel: [33283.777180] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=91.123.219.181 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=50643 PROTO=UDP SPT=12242 DPT=51413 LEN=38 
Sep  5 11:21:20 rabbit-desktop kernel: [33285.574510] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=94.141.38.189 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=120 ID=34279 PROTO=UDP SPT=44777 DPT=51413 LEN=38 
Sep  5 11:21:21 rabbit-desktop kernel: [33286.738163] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=91.123.219.181 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=115 ID=50981 PROTO=UDP SPT=12242 DPT=51413 LEN=38 
Sep  5 11:21:23 rabbit-desktop kernel: [33288.568706] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=94.141.38.189 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=120 ID=35265 PROTO=UDP SPT=44777 DPT=51413 LEN=38 
Sep  5 11:21:31 rabbit-desktop kernel: [33296.349601] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=72.230.133.110 DST=192.168.156.100 LEN=58 TOS=0x00 PREC=0x00 TTL=108 ID=30833 PROTO=UDP SPT=22084 DPT=51413 LEN=38 
Sep  5 11:22:11 rabbit-desktop kernel: [33336.805581] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=78.86.193.124 DST=192.168.156.100 LEN=40 TOS=0x00 PREC=0x00 TTL=244 ID=0 PROTO=TCP SPT=6000 DPT=43432 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 11:22:11 rabbit-desktop kernel: [33336.815210] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=78.86.193.124 DST=192.168.156.100 LEN=40 TOS=0x00 PREC=0x00 TTL=244 ID=0 PROTO=TCP SPT=6000 DPT=43432 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 11:22:12 rabbit-desktop kernel: [33337.298969] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=78.86.193.124 DST=192.168.156.100 LEN=40 TOS=0x00 PREC=0x00 TTL=244 ID=0 PROTO=TCP SPT=6000 DPT=43432 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 11:22:31 rabbit-desktop kernel: [33356.479211] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1Sep  5 11:28:34 rabbit-desktop kernel: [   36.736737] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=38.229.70.20 DST=192.168.156.100 LEN=133 TOS=0x00 PREC=0x00 TTL=57 ID=4047 DF PROTO=TCP SPT=8001 DPT=48854 WINDOW=124 RES=0x00 ACK PSH URGP=0 
Sep  5 11:28:41 rabbit-desktop kernel: [   44.190021] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=98.136.48.80 DST=192.168.156.100 LEN=177 TOS=0x00 PREC=0x00 TTL=57 ID=25600 DF PROTO=TCP SPT=5050 DPT=44915 WINDOW=8326 RES=0x00 ACK PSH URGP=0 
Sep  5 11:28:57 rabbit-desktop kernel: [   59.636410] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=98.136.48.80 DST=192.168.156.100 LEN=177 TOS=0x00 PREC=0x00 TTL=57 ID=47228 DF PROTO=TCP SPT=5050 DPT=44915 WINDOW=8326 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:51 rabbit-desktop kernel: [  113.893594] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60784 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:51 rabbit-desktop kernel: [  114.148390] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60785 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:52 rabbit-desktop kernel: [  114.660692] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60786 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:53 rabbit-desktop kernel: [  115.685201] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60787 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:55 rabbit-desktop kernel: [  117.732649] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60788 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:29:59 rabbit-desktop kernel: [  121.828481] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60789 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:07 rabbit-desktop kernel: [  130.020933] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=60790 PROTO=TCP SPT=993 DPT=39292 WINDOW=139 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:12 rabbit-desktop kernel: [  134.973508] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=11683 PROTO=TCP SPT=993 DPT=39307 WINDOW=106 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:13 rabbit-desktop kernel: [  135.410106] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=11684 PROTO=TCP SPT=993 DPT=39307 WINDOW=106 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:13 rabbit-desktop kernel: [  135.652993] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=28467 PROTO=TCP SPT=993 DPT=39305 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:13 rabbit-desktop kernel: [  136.285912] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=11685 PROTO=TCP SPT=993 DPT=39307 WINDOW=106 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:34 rabbit-desktop kernel: [  156.893414] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12041 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:30:54 rabbit-desktop kernel: [  176.893681] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12043 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:31:14 rabbit-desktop kernel: [  196.893633] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12045 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:31:34 rabbit-desktop kernel: [  216.893338] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12047 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:31:54 rabbit-desktop kernel: [  236.894243] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12049 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:32:14 rabbit-desktop kernel: [  256.895627] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.127.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=12051 PROTO=TCP SPT=993 DPT=49767 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Sep  5 11:32:35 rabbit-desktop kernel: [  278.268879] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=11711 PROTO=TCP SPT=993 DPT=39306 WINDOW=106 RES=0x00 ACK PSH URGP=0 
Sep  5 11:32:55 rabbit-desktop kernel: [  298.033760] [UFW BLOCK] IN=eth0 OUT= MAC=00:16:17:ac:80:86:00:23:69:04:e1:5f:08:00 SRC=74.125.53.16 DST=192.168.156.100 LEN=81 TOS=0x00 PREC=0x00 TTL=54 ID=11713 PROTO=TCP SPT=993 DPT=39306 WINDOW=106 RES=0x00 ACK PSH URGP=0 
```The last half of the log was filled after restarting because of a system lock up, that I am unaware of the cause. When it locked up I had Xchat-gnome, transmission, pidgin, and Firefox running. Firefox was logged into UF and no other site when this happened.

Thanks,
uRock

---

### Post by uRock on 2010-09-05
[s]This daemon.log looks weird also.[/s] I looked up rtkit and realized what it is, so no longer wasting thought processes on it. =)

syslog and kern.log both have entries related to the UFW blocking also.

At this time the above system has been removed from the network until I can sort this out.

---

### Post by OpSecShellshock on 2010-09-05
Well, it's port 993, which I would assume has something to do with IMAP, so it's probably gmail. However, I think it's weird that it would be getting blocked since I'd figure the connection would have to have been established on your local device in the first place.

---

### Post by uRock on 2010-09-05
> **OpSecShellshock said:**
> Well, it's port 993, which I would assume has something to do with IMAP, so it's probably gmail. However, I think it's weird that it would be getting blocked since I'd figure the connection would have to have been established on your local device in the first place.
I am starting to think they are trying to reply to Thunderbird even after closing it. This is an odd thing in my mind, because it would be wasted overhead for Google to have their servers trying to connect proactively.

Now that I see this is a google thing, I am going to put the system back online and keep letting ufw block google when t-bird isn't running. But I still think something is wrong with Google to keep trying to connect to my client.

This blocked packet looks odd, too. Traceroute and Whois have no info on the destination IP and the UDP proto doesn't seem like a normal thing with there being a previous connection.
```
Sep  5 12:57:14 rabbit-desktop kernel: [ 5356.691931] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.156.100 [COLOR=Red]DST=224.0.0.251[/COLOR] LEN=468 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF [COLOR=Red]PROTO=UDP[/COLOR] SPT=5353 DPT=5353 LEN=448
```

---

### Post by OpSecShellshock on 2010-09-05
That one's MDNS (multicast dns or zeroconf). I think it basically announces your computer's presence to other devices on the same LAN maybe? Not sure. The IP address seems to be reserved space for that.

As for gmail trying to connect even without the client running, it might be worth logging into the web interface and checking the settings on that end. I must admit that I've always been under the impression that even if you do set it to not store messages that have been downloaded to a desktop client it would still hang onto them until you've got the client running. Maybe it does actively try to push them down when certain settings are in place.

---

### Post by BkkBonanza on 2010-09-05
The log entries seem to indicate ACK packets. So they could just be straggling packets ack'ing yours but not received until after the program closed. They appear to happen at 1 minute intervals. Do you have TBird set to auto-check mail every 1 minute? 

It's not uncommon for a few garbage packets to be left bouncing around after a program closes. Anyway, if they are ACKS then it's not trying to connect to you. Connects would start with SYN packets.

---

### Post by uRock on 2010-09-05
I agree, that this is from T-Bird SYNing and Google ACKing. I was just thrown off by having my system lock up and having to do a hard shutdown.

@OpSecShellShock- Thanks for pointing out the MDNS packet. I should have run Wireshark when this was going on and most of this stuff would have panned out easily.

Thanks for the help. I am gonna mark this thread solved, because I have been watching the logs and feel confident this was an operator level false positive. :oops:

Thanx,
uRock

---

