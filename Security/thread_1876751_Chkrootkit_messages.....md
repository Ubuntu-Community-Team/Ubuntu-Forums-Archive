---
title: "Chkrootkit messages...."
date: 2011-11-06
forum: Security
---

### Post by Brian0312 on 2011-11-06
I ran a scan with chkrootkit and mostly came up with nothing.  I got a few hidden directories and removal temporarily broke my system, so I've decided to believe they should be there.

The other thing I keep getting is 

```
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1061], /sbin/dhclient3[2333])
```Upon review, even though they've changed a few times, they always seem to be standard issue TCP/UDP ports that I'd assume are required for me to get on the internet.

Is my assumption reasonable, or am I looking at a wide open door?

---

### Post by Dangertux on 2011-11-06
wpa_supplicant and dhc3clieny should be there. I would say false positive.

---

### Post by Enigmapond on 2011-11-06
Definitely false positive. The chances of you actually getting a rootkit are about 5%...relax...enjoy.

---

### Post by Brian0312 on 2011-11-07
Thanks for the help!  I suspected that, but false assumptions are how people get in trouble.  Better to ask and know....

---

