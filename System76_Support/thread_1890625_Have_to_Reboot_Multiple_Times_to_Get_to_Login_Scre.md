---
title: "Have to Reboot Multiple Times to Get to Login Screen"
date: 2011-12-03
forum: System76 Support
---

### Post by gkend on 2011-12-03
I have a Pangolin (panv3, I believe) that is now running Ubuntu 11.10.  The boot problem is getting progressively worse.  When booting, I get the Phoenix BIOS splash screen, then the cursor on the black screen for a few seconds, then the purplish Ubuntu screen -- all normal.  Then after several seconds on the purple screen, the Ubuntu logo and the flashing dots should appear.  What happens most of the time, though, is that the screen goes black (like powered-off black) and the Ubuntu logo never appears.  The fans are still running, and I may even see some activity on the HDD light; but I can't get it to do anything else.  So I have to hold the power button for a hard shutdown and reboot.  After several iterations of this, I may get the screen that offers other boot options (recovery mode, memtest, etc.), but booting in standard mode or in recovery mode seems to make no difference.  The only option I have is to continue booting, failing, and restarting until it finally hits the Ubuntu logo.  Each time it gets that far in the boot process, it succeeds.

Please help; I don't know what to do.  Thanks.

---

### Post by cbennett926 on 2011-12-03
My suggestion would be to do a re-installation. :/ It's a sad day when it comes to that but it sounds like a boot problem and the quickest way to fix that is try another install.

---

### Post by sfmadmax on 2011-12-07
Sounds like there was a package installed that didn't agree with your system. Could be holding it down.  What you could do is boot from cdrom and mount the hard drives then troll /var/log/syslog on the mounted hard drive. 

That would at least be a good start.  

Otherwise as suggested prior , re-installation might be best if you really don't know why it broke or don't want to deal with fixing it.

---

