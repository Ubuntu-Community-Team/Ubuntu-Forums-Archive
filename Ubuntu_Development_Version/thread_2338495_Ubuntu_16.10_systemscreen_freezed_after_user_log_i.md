---
title: "Ubuntu 16.10 system/screen freezed after user log in"
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by 1j4fj67 on 2016-09-28
I attempted to install today's build (9/28 - early this morning US East Coast time) after downloading the .iso, verifying SHA256, and using Startup Disk Creator to create the bootable USB stick. The installation seemed to go OK although at the very end, after being prompted to remove the installation media, I had to manually shut down the machine and then restart it. Upon booting, I had no trouble getting through the HDD encryption password but then upon entering my user log in, the system bar (? at the top of the screen with the clock and date) disappeared and I was left with a colorful background on both monitors but nothing happened. The launcher never appeared nor the time/date bar at the top. I manually shut down the machine and rebooted with no difference. I installed it again but had the same issue. I read this afternoon that an updated "beta 2" release was issued today. Does anyone have any idea when it was released? Has anyone run into similar issues? Thanks. I'm using the Nouveau drivers.

---

### Post by 1j4fj67 on 2016-09-28
I just saw that the latest build .iso was modified at 08:03 this morning although I don't know if that's GMT or another time zone.

---

### Post by ventrical on 2016-09-28
> **1j4fj67 said:**
> I attempted to install today's build (9/28 - early this morning US East Coast time) after downloading the .iso, verifying SHA256, and using Startup Disk Creator to create the bootable USB stick. The installation seemed to go OK although at the very end, after being prompted to remove the installation media

At which point it did a double blink here. I installed unity8. Tried to take a screenshot and froze up.

Regards..

---

### Post by 1j4fj67 on 2016-09-29
Ventrical, once I get things working, I'd like to try Unity 8 as well.

---

### Post by ventrical on 2016-09-29
> **1j4fj67 said:**
> Ventrical, once I get things working, I'd like to try Unity 8 as well.

Well that would be great but I am no longer boosting unity8 for this cycle. Maybe the next cycle. There have been a lot of let downs and disappointments this cycle which equals excessive down time. Perhaps if you wanted to test xubuntu or lubuntu .ISOs  would be more appreciated.

Thank you and regards..

---

### Post by 1j4fj67 on 2016-09-30
I tried again with the newly released 16.10 final beta yesterday and had the same problem: After logging in with user name and password, the desktop with the launcher does not appear. The system appears to be frozen and I can only reboot using the PC's power button. I tried installing it a second time, this time unticking "Require a password at login" during installation, but the same thing happened: desktop wouldn't appear. My 16.04.1 install is working perfectly. Has anyone else run into this problem? Before creating a bootable USB stick with Startup Disk Creator, I did check the .iso with SHA256SUM. Thanks for any ideas.

---

### Post by ventrical on 2016-09-30
what  kind of hardware are you using?


you may have to do an alternate install with nomodeset.

Regards..

---

