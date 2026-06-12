---
title: "USB Writing / Premissions Problem in Ubuntu 10.10"
date: 2012-12-25
forum: Virtualisation
---

### Post by zenofire on 2012-12-25
Hello,
Just recently installed Ubuntu 10.10 in Virtualbox on a Windows host (Vista 64 bit) successfully after an initial hurdle related to RAM.

I've run into a problem regarding writing data files on USB. It appears that I have permissions problem and I am unable to write any file to a USB mounted, even if I wipe and reformat the USB.

There has been a thread on this forum already - [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287) but the information is outdated and the manage groups option no longer exists. Can I have any help on this?

(I have already enabled the Virtual Box drivers in System Settings --> Additional Drivers but USB support is still unavailable. I have also tried ```
sudo usermod -a -G vboxusers jacob
``` but it says that ```
usermod: group 'vboxusers' does not exist
```.)

Thanks in advance.
Z

---

### Post by speedwlk on 2012-12-27
I am guessing that "VirtualBox Guest Additions" are not installed. Please check whether it is installed.

Have a nice day!

---

