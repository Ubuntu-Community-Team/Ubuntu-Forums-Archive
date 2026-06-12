---
title: "Precise Pangolin will not install!"
date: 2011-12-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Mathor on 2011-12-06
I have tried to install 12.04 many times, but I never get to the install screen. The display just hangs at the purple screen indefinitely. Please help, I want to be able to upgrade.

---

### Post by paul_in_london on 2011-12-06
Do you have an nvidia graphics card? Have a look at this thread:

[Precise Install just hangs after GRUB kernel selection]( http://ubuntuforums.org/showthread.php?t=1890045)

If you have, try booting into recovery mode and reinstalling nvidia-current. If that fails, try reinstalling from scratch without proprietary drivers first and then install them afterwards.

Another option would be (after making sure your 11.10 install is up to date) to run:

```
sudo do-release-upgrade -d
```

to upgrade from 11.10 to 12.04 Alpha 1.

EDIT: sorry, I should have read your post more carefully! Do you mean you can't boot boot a live CD or USB of 12.04 Aplha 1?

---

### Post by paul_in_london on 2011-12-06
Did you check the md5sum of the iso you downloaded?

You could also try to install 12.04 Alpha 1 using the Alternate CD for your architecture instead of the Desktop CD.

---

### Post by paul_in_london on 2011-12-06
Another thought.

Have you tried a [daily build](http://cdimage.ubuntu.com/daily-live/current/)?

---

### Post by cariboo on 2011-12-06
It sounds like the install process is having a problem detecting your graphics card. At the initial boot screen press any key, then press F6 and select nomodeset from the menu, press esc, then enter. You should be able to boot to the install screen after that.

---

### Post by Mathor on 2011-12-07
> **paul_in_london said:**
> Did you check the md5sum of the iso you downloaded?

You could also try to install 12.04 Alpha 1 using the Alternate CD for your architecture instead of the Desktop CD.

i did an apt upgrade, an update center upgrade, the live dvd image, the alternate cd image, and the desktop cd image, and the daily build, all of which gave me the same result. You can imagine my frustration, this is the 6th time i've had to reformat this usb in a day! Immediately after booting, it will go to the purple screen and nothing will happen. I have an ATI graphics card, and it works perfectly in ubuntu 11.10 with no problems, so i don't understand the issue :(

I am going to try f6 nomodeset *fingers crossed*

---

### Post by Mathor on 2011-12-07
I tried installing alpha 1 again, to no avail. a screen comes up where it asks if i want to try or it or install, except those options are presented twice, and this time when i selected install it took me to a black screen, f6 did nothing. Help!

---

### Post by jppr on 2011-12-07
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) I did yesterday fresh live-cd installation and I don´t have
any problem. I don´t ever use or try alternate installation

---

### Post by Mathor on 2011-12-07
installation was almost done and it crashed and offered a bug report

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/901111](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/901111)

---

### Post by Mathor on 2011-12-07
pressing tab at the beginning screen opened a terminal prompt. I put nomodeset in that way and it worked (though f6 didn't work). It eventually took me to a crash, but then loaded the desktop with the "install 12.04" as it did when i first tried it in virtualbox, and I pressed install again it worked! Excited!

---

### Post by karolinger on 2011-12-12
> **Mathor said:**
> installation was almost done and it crashed and offered a bug report

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/901111](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/901111)

I'm not sure if your bug is similar to mine: [https://bugs.launchpad.net/ubuntu/precise/+source/apt/+bug/850264](https://bugs.launchpad.net/ubuntu/precise/+source/apt/+bug/850264)

Ubiquity crashes almost at the end of the installation.

---

### Post by ventrical on 2011-12-13
I know some may disagree with me but there is a big, big problem with some LCD monitor connections. I went through this proceedure many times and the culprit was always an older, legacy monitor.

---

### Post by lolpenguin on 2011-12-13
This also decided to happen on my 11.10 amd64 liveCD, which I have used many times with no problem, but that install was a test using EFI.

---

### Post by cariboo on 2011-12-13
> **lolpenguin said:**
> This also decided to happen on my 11.10 amd64 liveCD, which I have used many times with no problem, but that install was a test using EFI.

What does this have to do with Precise? The name of this sub-forum is Precise Pangolin Testing & Discussion. If you aren't running Precise, post your question in General Help.

---

