---
title: "Daru2 Webcam won't turn on"
date: 2009-08-13
forum: System76 Support
---

### Post by elusivespoon on 2009-08-13
I'm on a Daru2 running Ubuntu 9.04 and no program can detect my webcam. If I press the P2 button nothing changes. The output of `lsusb` remains the same. I read in a [related post]("http://ubuntuforums.org/showthread.php?t=734788") that Kubuntu might cause problems in keymappings. Some time ago I did install a KDE program which resulted in enough of KDE getting installed that I now have the Kubuntu startup screen, so that could be the issue. How can I reset the keymappings if necessary to get the webcam working?

---

### Post by thomasaaron on 2009-08-13
We don't support Kubuntu. However, the first step is to determine if Kubuntu is actually the problem.

I would boot from a live Ubuntu CD, go to a terminal and run lsusb, then press P2 and run lsusb again to see if the output is any different.

---

### Post by elusivespoon on 2009-08-16
Booted from the LiveCD, and after pressing P2 `lsusb` did list the webcam. So apparently it is a problem with configuration somewhere. Any suggestions on how to move forward?

---

### Post by Mr. Farlops on 2009-11-07
I seem to be having the same problem but I'm under Ubuntu 8.04.

I think I did this to myself though. My theory is that I may have mapped some other system function to the P2 key and thus broke whatever config file is supposed to point the way to the camera driver when I run lsusb.

Now, if I run lsusb before and after pressing P2, I still don't see the camera listed. Can Thomas or anyone tell me where to look to hook these things back together again?

---

### Post by thomasaaron on 2009-11-09
elusivespoon, was the live CD you tested from a Kubuntu CD or an Ubuntu CD?

---

### Post by elusivespoon on 2009-11-09
No clue. I would guess ubuntu, but I can't find the CD. I'm hoping to upgrade to 9.10 sometime soon, so maybe I'll have some luck there.

---

### Post by elusivespoon on 2009-11-24
Just did a fresh install of 9.10, and my webcam is working fine.

---

### Post by elusivespoon on 2009-11-24
> **elusivespoon said:**
> Just did a fresh install of 9.10, and my webcam is working fine.

Check that. It's rather flaky. Sometimes pressing P2 will cause the camera to show up in the output of `lsusb` and when it does, it only occasionally is detected by software.

Edit: after more testing it's pretty much unusable. Can't even guarantee it will work after a fresh boot. If it's working Skype kills it when used on a call (which is pretty much the only reason to use my webcam). And otherwise it stops working pretty quickly on it's own.

---

### Post by thomasaaron on 2009-11-25
Shoot me an email (support...at...) and I'll provide further instructions. We'll probably need to bring it in.

---

### Post by elusivespoon on 2009-12-02
After a little more time, it does appear that the P2 button is working, but sometime it takes a few minutes for the camera to turn on.

It seems to be working with Skype now. I'm not sure what made the difference as I hadn't changed things. Skype was definitely killing the camera before, but it hasn't over the last few tests. I'll update if it starts happening again.

---

