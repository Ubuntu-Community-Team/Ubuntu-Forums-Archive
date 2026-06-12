---
title: "Weird, weirdly persistent problem when installing Ubuntu Studio off a USB drive"
date: 2011-09-23
forum: Ubuntu Studio
---

### Post by notverygoodatthi on 2011-09-23
Incoming wall of text! Apologies, but it's all pretty much on one subject, please read anyway if you think you can help me.

Hi everyone, I'm having a pretty strange problem. I've got a fresh Windows 7 install on a new hard drive and I'm trying to install Ubuntu Studio to run alongside it. I used Unetbootin to put it on a USB drive (not a liveCD, as far as I can tell there is no liveCD for Studio), then went through the installation process booting from the USB drive. Everything ran smoothly until the "select and install software" section, which I accidentally ran through without selecting any additional packages. The next step was rebooting, but I took the back button and selected four or five packages I wanted to install. The installer went through the process again, but resulted in an error, saying the software installation step had failed. Hoping it would still work, I allowed the installer to complete the installation and rebooted, but when I selected Ubuntu from the GRUB menu, it ran fsck, which gave an error something like "disconnected from Plymouth" - no idea what that means - and would not move from that point.

Since then I've tried reinstalling Studio several times, each time wiping the partition, and each time I get to the "installing software" step, it only lists as choices the five packages I picked during the first attempt, then the installing software step fails regardless of whether I choose to install anything or not.
I'm pretty lost as to what to do next, I don't really understand how that data is being stored. I even removed the installer from the USB drive and reinstalled it! Help please?

---

### Post by jejeman on 2011-09-24
Did you check .iso file for errors?
Try it from dvd if you can.

---

### Post by WasMeHere on 2011-09-25
I suppose that you know Ubuntu Studio and really want it. But one step forward might be to find out if you can install 'vanilla' Ubuntu onto your new hard disk.

If that works, but Studio fails, please check the iso file (using md5sum) or try a cd or dvd as suggested by jejeman.

If you have no cd or dvd drive, you can use (borrow or buy) an external usb drive. If you have an old drive from another computer, it can be attached via a multipurpose adapter (ide to usb, sata to usb).

If you cannot install 'vanilla' Ubuntu there is some general problem: Can you run 'vanilla' Ubuntu **live** from the usb drive? By the way, make sure that you install onto the internal drive, not to the usb drive!

---

