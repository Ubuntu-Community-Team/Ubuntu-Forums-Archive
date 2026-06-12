---
title: "port 1025 entries in /var/log/messages"
date: 2006-11-23
forum: Server Platforms
---

### Post by StarsAndBars14 on 2006-11-23
Are these any cause for concern?  I get them every boot, two times each boot:

Nov 23 14:45:24 localhost kernel: [17179750.280000] DROPPED IN= OUT=eth1 SRC=68.47.197.11 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=1025 DPT=1900 LEN=140 
Nov 23 14:45:24 localhost kernel: [17179750.284000] DROPPED IN= OUT=eth1 SRC=68.47.197.11 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=1025 DPT=1900 LEN=141 

I know that port 1025 isn't exactly used for some of the greatest stuff (like messenger spam on unpatched XP machines) . . .so. . .

opinions, please?

Oh, and I'm using 6.10, nothing strange is really showing up on Netstat.  I have one port for AVGscan (55555) and one port (25) for a local MTA.  That's it.

---

