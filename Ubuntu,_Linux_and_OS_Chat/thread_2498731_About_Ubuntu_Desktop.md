---
title: "About Ubuntu Desktop"
date: 2024-06-25
forum: Ubuntu, Linux and OS Chat
---

### Post by ahmeetsn on 2024-06-25
Greetings,


I've been thinking about installing Ubuntu Desktop for a long time, and today is the day. I just have a few questions, I wonder if I will have any driver problems when installing 24.04? My computer is a collection computer, I won't have hardware incompatibility, right? I was confused because I saw a lot of comments in google searches such as hardware incompatibility manual drive installation. 


My system information;
ryzen 7 5700x 
MSI 3070

---

### Post by tea for one on 2024-06-25
> **ahmeetsn said:**
> I wonder if I will have any driver problems when installing 24.04? My computer is a collection computer, I won't have hardware incompatibility, right? 
You can answer many of your questions by testing in a live session
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

---

### Post by grahammechanical on 2024-06-25
Microsoft requires hardware manufacturers to provided Windows drivers with their hardware. The Linux developers do not have that power of influence. So, Linux comes with mega bytes of hardware drivers. The package is called firmware.

Newer hardware requires the very latest version of Ubuntu. Even then the Linux developers may not have caught up with the progress of the hardware manufacturers. They do their best.

As suggested above download the Ubuntu 24.04 LTS ISO image and burn it to a USB memory stick and boot into it and choose the Try Ubuntu session.  Test to see if you can connect to your ISP on WiFi and access the internet. To play audio and video files you may need to install some non-free (copyrighted) codex. This can be done during the install process. 

The 24.04 LTS Try/Live session has a utility called Firmware Updater. That will give a detailed report on what firmware (hardware) you have on your machine and whether the firmware drivers are upgradable.

To tell you the truth, I have not experimented with this. I go back to the days when updating the BIOS brought with it a risk of making the computer unusable. Or, to use the expression of those days - brick the machine.

Regards

---

### Post by TheFu on 2024-06-25
There's no way for anyone here to say that your hardware is all perfectly fine.  You'll never know until you actually try an install.  Further, the drivers on the installation ISO are often different from the drivers that get installed.  Crazy, right?  I've never seen a good explanation for why the installation ISO would have newer drivers than those made available through APT.  

Unfortunately, the most common driver issues are:
* GPUs (usually nVidia)
* NVMe
* Wifi Chips, but some Realtek NICs too.
* any odd, limited release, hardware.  Fingerprint readers on laptops are notorious for not having any Linux support.
* too new, bleeding edge, hardware.  For a few years, Intel XE graphics didn't really work. I think that's all better now.

The best thing you can do it just try it and see how it goes.  For 90%+ of the installations, it seems to go mostly fine.

So, do an install accepting the defaults and don't have any other OS on the connected storage.  Doing this should take less than 20 minutes.  If it goes well, login, don't setup anything, see that networking, audio, video, your mouse, keyboard all work.  If it does and you'd like to customize the install, go back and do the install again, this time carefully reading everything and considering all the options as best you can.  Like any skill, the most times you do an install, the better you will be at doing it.  I've probably done 500+ installs in my 30 yrs with Linux and I'm not a bug tester like some of the people in these forums are.  They probably do 3-10 installs every week as part of their "bug team" efforts.

The desktop installs for 24.04 do limit some of the Ubuntu install options that we've had going back nearly 20 yrs now.  As a new user, most of those things won't matter to you.

---

### Post by morovan on 2024-06-27
If you consider Ubuntu having largest market share amongst Linux distribution, that by definition means it has been tested on biggest variety of hardware in compassion to other Linux ditros.
Using same reasoning, one could easily say it it in most active development.
Put the two together and you should agree Ubuntu would statistically have the least issues with hardware when compared to other distribution.

There certainly are things i dislike about Ubuntu, but I am sticking with, as I assume it does cause me the least issues in comparison on average. From time-to-time I try something different, but have not come across anything I would like to use full-time on my main machines - hardware support is totally one of the reasons.

As mentioned above, give it try with live Ubuntu. If all feels fine, but still in doubt for some reason, save image of your current OS, so you have a way of going back if things wont work out for you for any reason after full installation.

---

### Post by 0f4d0335 on 2024-06-30
Ubuntu has better driver support than Debian in my experience. When I'm unsure about hardware, I will install Ubuntu on a secondary disk and boot from it. If I'm having issues, I know that the hardware isn't a good candidate for the install. But I've yet to come across hardware I can't get working with Ubuntu. Ubuntu simply works on many PCs.

---

### Post by 909mjolnir on 2024-07-01
NVMe drives aren't really a problem in Linux anymore if you just test with a LiveCD to show or edit the NVMe drive.  I still install some NVMe driver stuff after the whole reality of installation, after bootup, but I don't think the system really needs it.  

Even my GRUB complains that it doesn't understand what my NVMe drive is, but it doesn't matter because GRUB still works with my one and only drive--my NVMe drive.  So really, it's just silly--it works--it just works.  I think most of the support for newer stuff is getting built into the newer Linux kernels so we don't need to manually install the drivers as much.  

That does maybe make more of a security concern go up as incompatibility goes down, but we have to win something, right?  LOL

At least with USB, if the hardware is USB CLASS COMPLIANT, then it works with Linux too.

---

