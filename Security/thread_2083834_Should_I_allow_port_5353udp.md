---
title: "Should I allow port 5353/udp?"
date: 2012-11-13
forum: Security
---

### Post by donsy on 2012-11-13
My ufw.log is filling up with these:
```
Nov 13 13:10:44 BSWZ1S1 kernel: [ 7576.948054] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.2 DST=224.0.0.251 LEN=135 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=115 
Nov 13 13:27:48 BSWZ1S1 kernel: [ 8599.689459] [UFW BLOCK] IN= OUT=wlan0 SRC=fe80:0000:0000:0000:ae72:89ff:fec9:08f1 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=115 

```Should I allow that port?

---

### Post by OpSecShellshock on 2012-11-13
Allowing it would make the messages go away. It's mDNS traffic, probably from the avahi-daemon process. You can kill that process to make the messages go away, but it will come back when you reboot. It's not really necessary but I don't think it does much harm.

---

