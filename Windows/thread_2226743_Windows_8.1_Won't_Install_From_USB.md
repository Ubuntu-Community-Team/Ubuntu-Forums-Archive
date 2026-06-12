---
title: "Windows 8.1 Won't Install From USB"
date: 2014-05-28
forum: Windows
---

### Post by wyratt on 2014-05-28
I have a desktop running the latest Ubuntu OS and I wanted to install Windows 8.1. I downloaded the ISO from Microsoft and put it on a USB using WinUSB. I also marked it as bootable with GParted and set boot order in BIOS to USB first. But when I rebooted my computer it showed a black screen for a few seconds and then a box appeared in the upper-lefthand corner saying Windows USB - Loading... I thpought this was good, but it stayed that way for about 45 minutes, when I hit the power button to shut it down. Any ideas about what the problem is? I would really like to ba able to install Windows. Thanks!

---

### Post by pqwoerituytrueiwoq on 2014-05-28
try running it in [virtualbox](apt:virtualbox)

---

### Post by wyratt on 2014-05-28
"[COLOR=#000000]try running it in [/COLOR][virtualbox]("apt:virtualbox")"

How do I do that?

---

### Post by LastDino on 2014-05-29
What is your system config?

---

### Post by pqwoerituytrueiwoq on 2014-05-29
here is a video (just recored)
[http://www.yourupload.com/watch/2S4qw0](http://www.yourupload.com/watch/2S4qw0)
the on-line player does not want to work for me, download and play works fine

---

### Post by wyratt on 2014-05-29
System config:
What part? Do you want everything?

Sorry I have to post this as a new reply, I can't seem to reply to individual posts

---

### Post by wyratt on 2014-05-29
For the virtual box suggestion: is there a way I could dual-boot it instead, or just install it over Ubuntu? I would prefer not to run it in a virtual box because my computer is kind of old and I've heard that a virtual box will make it (windows) run slower.

---

### Post by LastDino on 2014-05-29
Full config is preferred. You can dual boot but WIndows will likely destroy your existing Ubuntu, do you've a spare HDD/SSD? If you do, you can install WIndows on it and remove/disconnect Ubuntu HD while doing it. 

OR

You can take full image of this Ubutnu install and back up everything, then install Windows and then restore the image, then all you need to do is make grub detect this new windows.This could be quite tedious though.

Anyhow, if you want Windows on existing Ubuntu HD, WIndows needs to be installed first and then Ubuntu. You can choose to do fresh install of Ubuntu too by just backing up the data, but that is up to you.

---

### Post by wyratt on 2014-05-29
Yeah I was planning in installing windows and then reinstalling Ubuntu because I don't have much on my 
HD and I don't really care about it, but now Windows won't install.

---

### Post by LastDino on 2014-05-29
We are still not hearing anything which can be used to help you, what happened to system config?

---

### Post by wyratt on 2014-05-29
How do I get the system config info? I'm kind of new to this. Is there a Comand-line prompt I can run?

---

### Post by monkeybrain20122 on 2014-05-30
> **wyratt said:**
> For the virtual box suggestion: is there a way I could dual-boot it instead, or just install it over Ubuntu? I would prefer not to run it in a virtual box because my computer is kind of old and I've heard that a virtual box will make it (windows) run slower.

Well if your computer is kind of old  for VB Win 8 probably won't install. If that is the case problem solved.:P

---

### Post by wyratt on 2014-05-30
I don't know if its too old, I just want it to run slower then it needed to. I have a Pentium R 4 3.6 ghz processor, 2.5 gb of RAM. Is that too old?

---

### Post by pqwoerituytrueiwoq on 2014-05-30
If you have a full size PCI GPU you may be able to run win8 on that
that is a system i would recommend xubuntu for

---

### Post by LastDino on 2014-05-30
+1 to above, I've P4 3.0Ghz and I run Xubuntu or XFCE desktops or lower only. Unity version is usable, but there is considerable difference in performance, so I would also suggest trying Xubuntu.

And instead of W8, try 7 on that. You'll be better served as W8 is not that cool for non touch screen PC's.

---

### Post by wyratt on 2014-05-30
Yeah I don't have a real graphics card, it's an integrated Intel 940. I would really like to have windows so that I can play games though. You thinks windows 7 will work? As for xubuntu, I just checked and I was wrong. I actually do have xubuntu, not Ubuntu.

---

### Post by codingman on 2014-05-30
You probably don't want to be gaming with an iGPU like that. How is it that you didn't know what flavor of Ubuntu you were using?

---

### Post by LastDino on 2014-05-30
Assuming you're talking about the games which could work on this config, yes, W7 can serve you better. I would've suggested XP but that fire has been put out by MS.

By the way, you can play plenty of games on Linux too, I don't play any so I'm not best person to discuss this, but see if you can have Stem on Xubuntu working with that config or not.

---

### Post by wyratt on 2014-05-30
Yeah I have some games like Half-Life, but I was hoping to get some more that aren't on Linux. Also I am planning on getting a new GPU, so that will help a lot. Thanks for the advice, I'll try installing w7, hope it works.

---

### Post by wyratt on 2014-05-31
I have one last question. Do you guys think that this problem wa caused by my computer just being to old, or was it WinUSB, or the way I put it in the USB? In other words, do you think it would work if I did the same thig but with w7?

---

