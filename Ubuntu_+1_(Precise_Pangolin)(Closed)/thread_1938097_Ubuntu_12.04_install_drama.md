---
title: "Ubuntu 12.04 install drama"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-03-09
G'Day;  Tried to install 12.04 on it's own partition but when I get to the point where it should scan the drives the whole thing crashes with an error message;

  [ Package       Ubiquity 2.9.24

   Problem Type          Crash

   Ubiquity crashed with type error in Partman_column_name(): Argument
   of type "None Type" is not iterable 

   If "id" not in Partition type error : argument of type "none type" is not iterable ]

   Is there anyone who might know weather the fault is with the partitions or something
    else.
   Regards  Miykel

---

### Post by |{urse on 2012-03-09
I guess they're sorting it out currently
[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/912031](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/912031)

I'm still hanging back at 11.10 myself.

---

### Post by ckasux on 2012-03-09
> **Miykel said:**
> G'Day;  Tried to install 12.04 on it's own partition but when I get to the point where it should scan the drives the whole thing crashes with an error message;

  [ Package       Ubiquity 2.9.24

   Problem Type          Crash

   Ubiquity crashed with type error in Partman_column_name(): Argument
   of type "None Type" is not iterable 

   If "id" not in Partition type error : argument of type "none type" is not iterable ]

   Is there anyone who might know weather the fault is with the partitions or something
    else.
   Regards  Miykel



i had major problems installing .but all good now fixed all myself .when are you crashing on install or after install .
on install let it pick partan on reboot you may not have grub thats ok .reload cd or dvd f6 pick oem install go throw install reboot and then it will be there

---

### Post by Miykel on 2012-03-09
G'Day Guys and thanks for the quick replies;

        I already have W7 and Ubuntu 11.10 installed on this PC which has multiple drives, I created a partition just to install 12.04 onto, all goes fine until I click on "do something else" option and it goes to the window where it should scan the drives and give me the option where to install, then the whole thing crashes, I use grub to boot into the other OS's so that shouldn't be the issue
  Regards Miykel

---

### Post by pablopancho on 2012-03-09
I had a similar problem - what I did was:
1. Choose the Try Ubuntu instead of Install option so that live environment loads completely
2. Install Ubuntu using shortcut on the desktop

It worked for me, hope it helps you guys :)

---

### Post by grahammechanical on 2012-03-09
I do not know if this helps but I tried a few hours ago to install 12.04 beta and I had problems. I already have a 12.04 that I have been upgrading daily to this point and I wanted to test a Beta 1 install into a new partition

1) It is difficult to get the live CD to run if you delay clicking Try button.

2) When clicking the Install button (which is what I had to do to get anywhere) things worked fine until the Partition Manager took over then I got a "Sorry, we are having a problem, Houston," message.

It comes with a box already ticked for sending a report. Do this:

Uncheck the box. If another Sorry - problem message appears, then uncheck the box for reporting and you will get a Desktop.

From the Desktop the Install icon will let you install. Well, it did for me.

A very roundabout way of doing things. Run Install, hit a bug, reject offer to report bug, get to a desktop which you could not get by running Try Ubuntu, and the run Install.

It worked for me. That is all I can say.

Regards.

---

### Post by tommo1982 on 2012-03-09
I am having similar problem, but the installer doesn't crash it stops responding. I will try to describe the issue as best as I can.

First thing. I have Debian 6 installed on my laptop. I had Ubuntu 11.10 with Xfce which I broke somehow and decided I will try Xubuntu 12.04 64bit Beta. I downloaded iso file, finally managed to put it on a pen-drive and decided to give a try to Live CD version. It started, all was fine so I thought I will remove the old Ubuntu and see what's new in Xfce. The installation was normal until I hit user creation screen. When I tried to create one the installer just froze. I tried another time to see if the files copy at all, and they do. It's the user creation screen that I can't go past. I can switch between consoles, but installer is unresponsive.

This is my bit of new distro problems :)

---

### Post by collisionystm on 2012-03-09
when you boot your live CD, run

sudo apt-get dist-upgrade

then install. if a fix has been released for the packages that are broken on the live cd, this will cure it and allow you to install.

been there and done it...

---

### Post by Miykel on 2012-03-09
Thanks so much for all your replies, I appreciate the time taken, I'll have a play with those suggestion today and see what happens.
One question though Collisionystm, how or can I add the updates to the CD so they will have an effect or just click on the install icon on the desktop.
Ignorance is not always bliss lol.
  Many Thanks Miykel

---

### Post by collisionystm on 2012-03-09
> **Miykel said:**
> Thanks so much for all your replies, I appreciate the time taken, I'll have a play with those suggestion today and see what happens.
One question though Collisionystm, how or can I add the updates to the CD so they will have an effect or just click on the install icon on the desktop.
Ignorance is not always bliss lol.
  Many Thanks Miykel

you cant really add updates to the CD itself. The best way is to download a daily ISO image to get what was compile the night before. Although a lot of times they still dont carry everything updated.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cariboo on 2012-03-09
Doing the updates will store them in ram, and will only be there until you reboot. Once the updates are finished, just click the install icon on the desktop.

There used to be an option to upgrade before installation right at the start of the install process, but that option has since been removed.

---

