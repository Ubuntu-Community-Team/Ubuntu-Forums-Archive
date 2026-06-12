---
title: "Lost WiFi connectivity on Dell Inspiron N7010 with Precise Beta2"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zolero on 2012-04-16
Hi anybody.

Have a big problem on my Dell notebook powered by Precise Beta2 (fresh install). While tried to bring up the "Run App" terminal box I've pressed ALT+F2, but it just deactivated the WiFi card (which was functioning perfectly). Then I've tried ALT+Fn+F2, and figured out that this worked well (since the Fn -function- button is meant for switching between function keying, or special laptop features). Now all was OK, till I mistakenly pressed CTRL+ALT+F2, and my wireless was totally gone. The network indicator in my taskbar doesn't even see any WiFi connection at all (found it well before).
I have tried to reinstall the Broadcom driver by official package installation way, and also tried to manually recompile the most newest STA driver from Broadcom, but no luck. Although driver is compiled just fine with both procedures (ie. Software Center's dkms, and manual compilation as well) it doesn't insert it into kernel, so I hadn't WiFi at all. By manual trial it reports: "No module wl.ko found" (but it's there for my life) and while modprobe -ing it with full path specified, says: "FATAL: Invalid kernel module -1".
Now what? I want my WiFi back without an OS fresh reinstall, but without garbaging my actual installation. Any help would be greatly appreciated. Thanks in advance.


PS. What a helpful community... More than 60 readings, no answer... DOH!!! Never mind. I'm going to reinstall it.

---

