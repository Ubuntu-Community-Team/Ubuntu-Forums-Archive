---
title: "Which Linux Distro to completely replace Windows?"
date: 2015-11-15
forum: Ubuntu, Linux and OS Chat
---

### Post by skor78 on 2015-11-15
[COLOR=#000000][FONT=arial]Hi everyone,[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]I'm getting fed up with Windows and I need your help and advice selecting the best distro for me considering my laptop hardware and most important features for me..[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]The laptop is a Samsung 530U3C and specs are: i5 3317U, intel HD4000, 8Gb RAM, 500GB HDD and 24GB iSSD ExpressCache. [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Important HW functions I'd like to ensure working are: CPU clock not fixed to low or high but hybrid (a bit similar to Samsung Optimized power plan), Fn keys working, ExpressCache configured for Cache and Hibernation, for faster performance and boot, and USB 3.0.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- I use some programming tools like Odin to flash my phone, Samsung Smart Switch and others..[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- I use Samsung Link to connect my laptop to my Smart TV and stream media, and I'd like to know if there's any type of allshare solution like in my Android devices..[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- I play PokerStars..[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Do I need any anti-virus or firewall? What are my options? Also, I use BatteryCare to monitor my CPU and HDD temp, and personalize power plans.. Any alternative there?[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]In addition, I've browsed through Mint page, and I've noticed 4 different desktops available, Cinnamon, MATE, KDE and Xfce.. Whis this important to me or should I just roll with Cinnamon and that's it?[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Thanks in advance.[/FONT][/COLOR]

---

### Post by mystics on 2015-11-15
Before I address your questions, I just want to give a caution about "completely" replacing Windows. Unless you are *absolutely* sure that you will *never *need to use Windows again, you should have some backup plan. Things like dual booting, running Linux as a virtual machine inside Windows, or running Windows as a virtual machine inside Linux are all better forward-thinking plans. I know that Windows can be frustrating at times, but try to not let that frustration create problems for you in the future, which will almost certainly happen if you completely replace Windows without at least a virtual machine plan.

Edit: In general, also using a virtual machine before making a switch can give you a good chance to look for programs you may want to use and test them out before officially installing Linux on your computer. This may solve some of your questions regarding software.

> **skor78 said:**
> I'm getting fed up with Windows and I need your help and advice selecting the best distro for me considering my laptop hardware and most important features for me.[COLOR=#000000][FONT=arial].[/FONT][/COLOR][COLOR=#000000][FONT=arial]

[/FONT][/COLOR]Unless someone has already gone through with your exact hardware, it would be hard to say exactly which distro runs "best". However, it is always best to try out various distros as a Live USB. What this will allow you to do is get a good sense of how the distro works with your hardware right out of the box, but always be sure to check if you start running into problems to see if there are fixes available. Some of these, however, may not be able to be applied to a live session, but at least you'll be able to judge just how many problems you can reasonably solve.

As for good distros to try out: Ubuntu and Linux Mint are the most popular distros, and each can run on a lot of hardware. However, try searching around for other distros to try out. Who knows? You may end up falling in love with something like Fedora.

> - I use some programming tools like Odin to flash my phone, Samsung Smart Switch and others..[COLOR=#000000][FONT=arial]

[/FONT][/COLOR]From what I can tell, it doesn't have a Linux client, and its rating for Wine (a program that allows users to run Windows programs in Linux with varying degrees of success) is "Garbage". So it doesn't look like you'll be able to run this on Linux.

You might be able to run an alternative program. As far as I know, ADB should work for flashing ROMs to the phone, and it is the more official Android program for doing this. 

> - I use Samsung Link to connect my laptop to my Smart TV and stream media, and I'd like to know if there's any type of allshare solution like in my Android devices..[COLOR=#000000][FONT=arial]

[/FONT][/COLOR]Maybe Serviio: [http://www.serviio.org/](http://www.serviio.org/)

If all of it is web-based or supported through Google apps, then using Chrome or Chromium may allow you to do it through Chromecast.

> - I play PokerStars..[COLOR=#000000][FONT=arial]

[/FONT][/COLOR]While I'll always advise caution with Wine, it does appear to have a good rating with running through Wine: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=2899](https://appdb.winehq.org/objectManager.php?sClass=version&iId=2899)

> In addition, I've browsed through Mint page, and I've noticed 4 different desktops available, Cinnamon, MATE, KDE and Xfce.. Whis this important to me or should I just roll with Cinnamon and that's it?

Try them all out on a Live USB and see which one you prefer. I would personally go with Cinnamon, but that's just me. There's a lot of other people that like the other desktop environments as well. 

There's also other desktop environments like Unity (main one for Ubuntu), GNOME, and LXDE. All of these are also well-liked by a lot of people.

---

### Post by grahammechanical on 2015-11-15
This is a Ubuntu user forum. Therefore, the answer to the question of which is the best Linux distribution to replace Windows must surely be Ubuntu, or Kubuntu, or Lubuntu, or Xubuntu, or Ubuntu Gnome, or Ubuntu Mate. That selection will give you the following user interfaces: Unity, KDE Plasma, LXDE, Xfce, Gnome 3 shell, Mate.

User interfaces are a matter of personal choice. To find out what suits you download the ISO images and create a live session DVD disc or USB memory stick and try each one out for yourself.

The other concerns are a different matter but do not expect any Linux distribution to be like Microsoft Windows. You should seriously consider dual booting until you have Linux setup to met your needs. You need to take the precautions in this wiki page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Oh, by the way, Linux Mint is not part of the official Ubuntu family of Linux distributions. Just so you know. 

Regards

---

### Post by Sweet_Baby_Jamie on 2015-11-15
And a good place to look for Linux-equivalent applications for Windows apps is [http://osalt.com](http://osalt.com)

---

### Post by Geoffrey_Arndt on 2015-11-15
Because of the specialized wants/needs you've expressed, be prepared to install Windows as a guest OS using a VM like VMware or Virtual Box.   CHeck out the youtube site for tutorials.

Might want to also read all you can re UEFI dual boot setup.   Sometimes can be a real-challenge.   Grahams post link a good place to start.

Regarding alternative software another great site is:   [URL="http://alternativeto.net/software/microsoft-excel/"]http://alternativeto.net/software/microsoft-excel/


[/URL]

---

### Post by gordintoronto on 2015-11-16
For temperature monitoring, I use Conky to display the results from hddtemp and lm-sensors. You are probably looking at a couple of hours in Google to set it up the first time.

You should definitely look at Kubuntu. I don't use it myself, but it will probably feel familiar, like Mint/Cinnamon. Your system is powerful enough to run either very nicely.

Use the Windows tools to free up some space on your hard drive and dual boot. 20 GB is enough space to run Kubuntu, but as soon as you download some videos it will be inadequate.

You will trip on this: documents and Documents are completely different places in Linux.

---

