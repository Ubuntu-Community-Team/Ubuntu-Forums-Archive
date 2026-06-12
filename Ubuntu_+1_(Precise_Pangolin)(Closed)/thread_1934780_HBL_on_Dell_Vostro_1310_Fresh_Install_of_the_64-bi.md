---
title: "HBL on Dell Vostro 1310 Fresh Install of the 64-bit Beta"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-02
It's funny how we have Ubuntu working perfectly and better right before the beta, and then **H**ell **B**reaks **L**oose when it is released, with new bugs and stuff we thought were not likely to happen at this stage of development. Same thing from last cycle...

I tried to install the 64-Bit ISO from [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) (correct MD5) using CD and USB method, to a working Dell Vostro laptop running fully updated PP Alpha. Therefore, to make sure everything would be set from scratch, I selected "Upgrade from 12.04 to 12.04" in the installer. 

The install went fine but, in the first boot, I'm stuck at busybox. Apparently, it can't read /dev/sda due to a "DMA Link not ready" error. That's kind of new to me. 

It's bizarre: The thing was working perfectly 10 minutes ago with PP. How can't it handle PP now? I'm not even gonna investigate, attempt and workaround, etc. It's useless. But I thought I should post in case someone else goes through the same thing.

BTW, I have installed the Beta in other machines, everything went fine... Go figure. I'm beggining to feel like the latest Alpha is a better product than the betas and finished product. Maybe all the pressure over developers to put stuff out for the Beta no matter what and in which state forces Beta quality down.

Regards,
Effenberg

[B]EDIT:
[/B]
Also: 
Dead touchpad (the synclient workaround we discussed here and reported).
Dead Broadcom (as discussed and reported here)
Dead Bluetooth (also Broadcom)
Broken Plymouth (Oh, this is a new one to me)
Wrong keyboard type (despite selecting/testing the correct one during install)
Brightness craziness (as reported on Oneiric)
No suspend (...)

Well, back where I come from we call a laptop with no wireless, no bluetooth, no touchpad and no keyboard, with corrupted graphics a piece of ... joy. lol

---

