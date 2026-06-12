---
title: "[WNDA4100] Wireless drops, only shows connected network"
date: 2019-07-05
forum: Ubuntu/Debian BASED
---

### Post by yuriislove on 2019-07-05
I'm running POPOS, but had the same issue when I was running Ubuntu so I'm assuming its an issue I'm having with Ubuntu and my adapter.

My problem is that, every once in a while, my wireless connection will drop, and no networks will show up. The only fix I've found so far is replugging the adapter.
Clicking on nm-applet shows no wireless networks found, except for the one I'm connected to. If disconnected, that too will disappear.

```
lsusb
NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
uname -a
Linux pop-os 5.0.0-15-generic #16pop0-Ubuntu SMP Wed May 15 14:41:25 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

[https://pastebin.com/y2kz0sPC](https://pastebin.com/y2kz0sPC) <--- results of wireless script

I also logged what I *believe* is the correct portion of dmesg if anyone wants me to post it.

Thanks

---

### Post by wildmanne39 on 2019-07-05
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

