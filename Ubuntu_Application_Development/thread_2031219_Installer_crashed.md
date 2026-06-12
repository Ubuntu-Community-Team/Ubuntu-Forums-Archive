---
title: "Installer crashed"
date: 2012-07-21
forum: Ubuntu Application Development
---

### Post by tim.hoeffel on 2012-07-21
Need a bug fix for the installer program so I can get my computee running again. Happened when upgrading to 12.04, now nothing will ipgrade. Hope you can get it fixed today. I'm now w/o an OS

---

### Post by ajgreeny on 2012-07-21
If you were installing 12.04 using the live CD try again, but before you run the installer, boot to the desktop, open a terminal and run command ```
sudo apt-get remove ubiquity-slideshow-ubuntu
``` It seems that there is a bug in the slideshow with some hardware (including my desktop) which makes the whole installer crash, leaving a spinning cursor but no activity.

If that does not solve your problem you may need to use the alternate installer CD, a text installation system, but still easy to use.

---

