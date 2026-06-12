---
title: "ASUS 1005 HAB WiFi AR9285 not working"
date: 2009-11-14
forum: Ubuntu Moblin Remix
---

### Post by mikeremix123 on 2009-11-14
When will there be a release that enables WiFi on the ASUS 1005HAB with the AR9285 chipset family?

Ran the latest 9.10 remix from a flash drive.  Interface is great...except no WiFi.

How about an out of the box install that works the first time?

Would really like to use remix.  Back to XP for now.

---

### Post by MountainX on 2010-06-07
See if this helps:
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

> Wireless networking
This is easy — you just need to install the driver back-ported from the next Ubuntu release.
First, enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”.
Then, open Synaptic Package Manager, find the package linux-backports-modules-jaunty, and install it.

---

### Post by penguin386 on 2010-06-12
I had the same problem.  Then I tried Ubuntu 10.04 and my wireless network worked.

---

### Post by camorri on 2010-07-03
I have the same wireless card. It works in 10.04.

```
Network controller: Atheros Communications Inc. AR9285
```

The driver - ```
lsmod | grep ath
ath9k                 306010  0 
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
cfg80211              126517  3 ath9k,mac80211,ath
led_class               2864  1 ath9k
```

The system is a HP Mini 210.

---

