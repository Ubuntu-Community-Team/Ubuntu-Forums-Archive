---
title: "Huawei E367 set to USB storage only"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by Burkey on 2014-03-03
This was an issue for some time in 13.10 and I think 13.04 but a HUAWEI E367 and various other models which contain both 3G and USB storage (micro-SD) capabilities get set to storage mode only and do not show up as a 3G device.

There is all manner of usb_modeswitch hacks to get it sometimes working but this should be considered barely usable really for most users.

lsusb shows it as 

```

ID 12d1:1446 Huawei Technologies Cp. Ltd. E1552/E1800/E173 (HSPA modem)

```

dmesg only loads usb-storage though.

---

### Post by fani2 on 2014-05-07
Having same issues. Sometimes it would work but with slower download speed, about 15Mbps, while in other devices (smart phone or windows system) same connection would work 21Mbps.

---

### Post by cariboo on 2014-05-07
Unless this concerns Utopic (14.10), I'd suggest you start a new thread in the [Networking & wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") sub-forum

---

