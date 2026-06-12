---
title: "Ubuntu Nexus 7"
date: 2013-02-15
forum: Ubuntu Development Version
---

### Post by fisch246 on 2013-02-15
I used the Nexus 7 installer app, and everything worked perfectly, until the splash screen. Showed the Ubuntu logo, then black. Nothing. Absolutely nothing. I'm going to try and do it again, and see if it'll work, however I saw posts of people having this same issue and doing it over and over again with the same issue. Any ideas?

---

### Post by fisch246 on 2013-02-15
trying to do it manually right now to make sure I'm using the latest image. I'll let you know if that fixes it. If I set to solved, assume that was the solution.

---

### Post by rtalcott on 2013-02-15
Good Luck...I am VERY interested in hearing how it runs on your Nexus....not sure I am ready to install Ubuntu on mine yet but I am definitely curious to hear how you like it.
rt

---

### Post by fisch246 on 2013-02-15
No luck, running md5 checks on both files, then I'll try again. I guess...

---

### Post by fisch246 on 2013-02-15
Well there are 2 other images I suppose I could try, but the current is completely broken. md5 checks, which means, I repeat, it's broken. I'll try the other 2, and let everyone know which is the current working model. I'll start with the earliest model. Keep in mind I am using the 13.04 daily-preinstalled images.

---

### Post by fisch246 on 2013-02-15
correction, there's 2 images total. the current is also the latest, so i'm using the other image.

---

### Post by fisch246 on 2013-02-15
I currently get this as a warning

> df: warning: cannot read table of mounted filesystems: No such file or directory

maybe this is the problem?

---

### Post by fisch246 on 2013-02-15
Filing bug report for ubuntu-nexus7 on Launchpad

EDIT: link to bug report: [https://bugs.launchpad.net/ubuntu-nexus7/+bug/1126836](https://bugs.launchpad.net/ubuntu-nexus7/+bug/1126836)

---

### Post by lprofil on 2013-02-17
Hey fisch246,

i had the same problem and it is also known on [launchpad]("https://bugs.launchpad.net/ubuntu-nexus7/+bug/1127051"). By using an **old image** i could fix it.
The image is from January the 30th 2013. I found it through a another post here:
[http://forum.xda-developers.com/showthread.php?t=2011403](http://forum.xda-developers.com/showthread.php?t=2011403)

Since the download speed of that source is damn slow and you 
shouldn't bother with that and take the laste working image which was
uploaded by Oliver today (2013-03-18) [to this location.]("http://cdimage.ubuntu.com/daily-preinstalled/last-good-image/").

After doing a ```
sudo apt-get update && sudo apt-get upgrade -y
```
you will have an up to date system which will boot fine.

For those of you who would like to **keep the Android system** and 
have a **DualBoot** oder **MultiBoot system**: hold on until i will write a How to on that soon.

/lprofil

ps: big thanks and my tribute to Vojt&#283;ch Bo&#269;ek alias [Tasssadar]("http://forum.xda-developers.com/member.php?u=3418703")
Make a donation to him if you like his Multibootstuff ;)


Update: Since **Ubuntu-Desktop** seems to be unusable for me on the Nexus 7 due to different reasons
i am looking forward to the release of **Ubuntu-Tablet** which should be released on the 25. this month
according to [this information (bottom left)]("http://www.ubuntu.com/devices/tablet/app-ecosystem").

---

