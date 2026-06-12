---
title: "Resolution in 10.04 under Virtualbox"
date: 2011-09-02
forum: Virtualisation
---

### Post by jhargis1012 on 2011-09-02
Hello.

I'm running Virtual Box 4.1.2 under Windows 7. I'm trying to get Ubuntu 10.04 32-bit to work as a guest, but I can't seem to raise the screen resolution above 800x600 or get a wide-screen display.

After installing the guest, I updating everything with apt-get. Then, I installed the guest additions. Still no resolutions. I saw this thread ([http://forum.virtualbox.org/viewtopic.php?f=3&t=15679](http://forum.virtualbox.org/viewtopic.php?f=3&t=15679)) and realized I didn't do the steps under "System Preparations" in the guest. I went ahead and did them, and then tinkered around with things trying to make it work. I tried re-installing the guest additions after that and tried updating everything else again just to be safe, but still the resolutions aren't there. I thought I heard a few people saying modifying the xorg.conf might fix it by manually setting the resolution, but apparently Ubuntu doesn't make use of that file? Not too familiar with Ubuntu yet, so I'm not sure.

Should I re-image the guest and start over? Or can it be saved?

Thanks for the help.

---

