---
title: "Slow, lag, freeze, clean install 16GB RAM Dell Laptop, is Linux desktop helpless?"
date: 2017-08-13
forum: Ubuntu, Linux and OS Chat
---

### Post by stephen-direct on 2017-08-13
Hi all,


It is almost unusable. My fresh installation of Linux Ubuntu (latest version) is extremely slow, all apps are lagging.


Surfing the web, using Calc sheets, video, audio, ...


I got the same problems with my former Asus Laptop from 2010. So I've bought a brand new Dell (because Dell is supposed to be very compatible with Linux), i7 Intel CPU, Radeon graphics and a huge 16GB RAM.


And... exactly the same problems!


I'm really pissed I can't stand it anymore. Is Linux desktop dead? Why not honestly tell "OK we can't make a simple, stable and efficient OS, please switch to Microsoft or Apple". That would prevent people looking for productivity (like me) to waste their time with an experimental OS.


A few years ago I gave up all special apps, because everything is buggy and it's always a nightmare to get it to work. I only stick to Firefox, Chromium, LibreOffice, Skype, Pluma, VLC. I try to use as much as possible simple text documents, I do not use any fancy desktop effects, AAAAND... it's not enough!


I only do level 3 updates, not higher. I only install apps from the software center (except Skype), I never install manually to avoid mistakes.


I've done a fresh re-installation 3 times in the past months. At first, it's always FAST and it works perfectly, then after a few months or weeks, performances go down. Exactly like Windows. Congratulations, after 20 years of development, now Linux is a bloatware like M$.


Instead of rushing like crazy to publish new versions of desktop environments and widgets like madness, why not focus on producing JUST a stable and efficient OS that works on mainstream platforms?


Yeah I know, it's probably because of X, Y, or Z component... There is always a good reason... But an average user is not supposed to dig into that mess just to get a simple Calc spreadsheet to work. When you use a car, you're not supposed to build the engine by yourself. Otherwise it is an experiment, and it should not be advertised as a car for everyone.


I've also installed Linux Mint, but it's the same problem.


I can't believe I'm the only one experiencing such problems. So is there a solution? Buying a MacBook?


I really wonder what kind of people are  SERIOUSLY using Linux. I mean, for productive work, not just for geek stuff. I've used Linux for the past 10 years, I wanted to believe in it, but I must admit I've never advised anyone to use it. Because they will get so disappointed.


Printing? Video editing? I had to buy a second laptop with Windows to do those tasks. Spending months to get those apps to work on Linux is much more expensive than buying a commercial license. So I was just using Linux for office basic tasks, but event that seems not possible anymore.


Does someone have a real simple solution to that problem, or should I give up Linux for good?


Thanks.

---

### Post by Autodave on 2017-08-13
What version of Linux did you install?

I am currently running Xubuntu 16.04 on 13 machines. Only the one machine with a high performance video card required me to do anything other than just install and go. All machines work infinitely faster on Linux than they did on Win XP, 7, or 10. Three of the machines are dual boots and the Linux is faster than Windows.

My guess on your current situation is that your Radeon video card needs a driver installed. Can we have the model of your computer or the model of the video card in it?

I personally to not use Radeon cards because they used to be terrible about getting drivers for. However, lately I have heard that Radeon is getting better at releasing Linux drivers.

Please post your specs and someone here who is used to the Radeon cards will assist.

---

### Post by vasa1 on 2017-08-13
I've moved this thread to Chat because there no specific question and reads more like a rant.

---

### Post by cariboo on 2017-08-13
It would be nice to see the exact specifications of your laptop, as I think there may be a problem with the packages or drivers you have installed. I'm running a fairly low-end Toshiba laptop. Specifications here:

```
 inxi -b
System:    Host: alexis Kernel: 4.12.0-11-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: laptop System: TOSHIBA product: Satellite C50-B v: PSCMLC-02Y00T
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           UEFI: TOSHIBA v: 1.70 date: 12/11/2014
Battery    BAT1: charge: 25.4 Wh 100.0% condition: 25.4/31.7 Wh (80%)
CPU:       Quad core Intel Pentium N3530 (-MCP-) speed/max: 541/2582 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.3 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 17.1.4
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
Drives:    HDD Total Size: 256.1GB (25.6% used)
Info:      Processes: 188 Uptime: 10 min Memory: 742.4/3835.1MB
           Client: Shell (bash) inxi: 2.3.34 
```

I recently upgraded the hard drive to an SSD, and my boot times have gone from approximately 1 - 2 minutes to:

```
systemd-analyze
Startup finished in 2.847s (kernel) + 19.416s (userspace) = 22.264s

```

I'm running 17.10, so the boot times are all over the place, but have never exceeded 30 seconds. I usually update the system twice a day and have artful proposed enabled, and I haven't noticed any problems that I need to create a bug report for. During normally operation which includes doing some coding and photo editing there is no discernible lag, and and since upgrading to an SSD, I'm totally happy with the way the system runs.

---

### Post by vocx on 2017-08-13
> **stephen-direct said:**
> Hi all,
I got the same problems with my former Asus Laptop from 2010. So I've bought a brand new Dell (because Dell is supposed to be very compatible with Linux), i7 Intel CPU, Radeon graphics and a huge 16GB RAM.
And... exactly the same problems!

Sounds like you don't install the video drivers, making everything choppy.

> 
I'm really pissed I can't stand it anymore. Is **Linux desktop dead?** Why not honestly tell "OK we can't make a simple, stable and efficient OS, please switch to Microsoft or Apple". That would prevent people looking for productivity (like me) to waste their time with an experimental OS.

Linux is not dead. Millions of people use it every day for all sorts of things, including productive people like scientists, engineers, bankers, biologists, pharmaceutical researchers, and many students.

> 
I only do level 3 updates, not higher. I only install apps from the software center (except Skype), I never install manually to avoid mistakes.

What is level 3 updates? I've never heard about that.

> 
I've done a fresh re-installation 3 times in the past months. **At first, it's always FAST and it works perfectly, then after a few months or weeks, performances go down**. Exactly like Windows. Congratulations, after 20 years of development, now Linux is a bloatware like M$.

Sounds like you don't install the video drivers so you keep working with a non-optimal system.

> 
Instead of rushing like crazy to publish new versions of desktop environments and widgets like madness, why not focus on producing JUST a stable and efficient OS that works on mainstream platforms?

That's exactly what Linux desktop is! It is stable, efficient, and just works on my system, which is a mainstream platform.

> 
I can't believe I'm the **only one experiencing such problems**. So is there a solution? Buying a MacBook?

Maybe you are not the only one, but maybe you are! Maybe you are one of the 1% for which Linux doesn't work.

> 
I really wonder what kind of people are  **SERIOUSLY using Linux**. I mean, **for productive work, not just for geek stuff**. I've used Linux for the past 10 years, I wanted to believe in it, but I must admit I've never advised anyone to use it. Because they will get so disappointed.

Hey, that's offensive to geeks! A lot of people seriously use Linux, like school teachers, electrical and mechanical engineers, computer scientists, network engineers, accountants, pensioners, governments who have opted to not renew their Microsoft Office licenses. How do you think websites run? They sit on top of a Linux machine that hosts them, and replicates them to other machines all around the world. Also, the Android phones run on Linux, so many people use those.

 If anything, I have the impression you are an office drone, like an accountant, so your work is just bureaucracy and not very innovative. How have you not ditched Linux in 10 years, if you have so many problems?

> 
Printing? Video editing? I had to buy a second laptop with Windows to do those tasks. Spending months to get those apps to work on Linux is much more expensive than buying a commercial license. So I was just using Linux for office basic tasks, but event that seems not possible anymore.

Yes, printing and video editing work quite well. I just made a sweet animation in Blender of the translation of the Earth around the Sun, in order to explain the Solar declination and how it affects the efficiency of Solar panels.

> 
Does someone have a real simple solution to that problem, or should I give up Linux for good?

Thanks.
If you cannot learn enough about Linux in 10 years, you may be the kind of person who does not learn things easily. You may need to stick to what you know in order to feel you are in control. Maybe even then, I bet you would call technical support if something doesn't work in Windows.

I have a complaint with the way you post. You leave two full empty lines between each sentence you write. That looks very bad. You should space your sentences better to avoid that.

---

### Post by Habitual on 2017-08-13
LinuxMint uses "Levels"

---

### Post by vasa1 on 2017-08-13
An earlier, more polite, and somewhat more coherent post is here: [Slow response and lag, Ubuntu 16.04, powerful Dell laptop 16GB RAM]("https://ubuntuforums.org/showthread.php?t=2354368")

---

### Post by sgian on 2017-08-14
The other post mentions the use of kde.  I've run into problems with the file indexer for kde occasionally, where it takes up all the processing power trying to index stuff for the file search function.  That is probably what the original poster experienced.  It is a simple workaround, just go into system settings and turn off file search.

---

### Post by Geoffrey_Arndt on 2017-08-14
For certain folks, Google Chromebooks are a good solution.   Everything is done for you - - no user intervention and chances to mess up.   And the hardware matches the OS.    

I don't recall if you ever said anything about installing the proper video drivers - - via add drivers app.     I much prefer all Intel machines (cpu, gpu, wireless, etc.) - - much better compatibility,

A much better solution if you insist on running Linux is to get a laptop with Linux pre-installed.    System76 has some great choices.

See the link in my sig. for more info.

---

### Post by stephen-direct on 2017-08-14
Welcome on Linux Airlines...


Pilot: We're going to take off


Passenger: Great!


Pilot: Sorry, there is a problem, it seems that your suitcase version is 17.66.9.1


Passenger: Hu I dunno, so what?


Pilot: That's why the plane is lagging, we cannot take off. You should have installed suitcase 17.66.9.2


Passenger: What? Never heard of that, I'm just an average passenger and I just want to fly from A to B for business, isn't it what Linux Airlines is about?


Pilot: Yes, millions of people fly with us every year, but not with suitcase 17.66.9.1, everybody knows that... you're probably an accountant or some low-IQ passenger.


Passenger (coming back after 2 weeks): OK, I've ordered suitcase 17.66.9.1, I've lost 2 weeks of business work, but at least I'm ready to take off!


Pilot: Did you pay attention to wings compatibility?


Passenger: What!? 


Pilot (condenscending): Come on, everybody knows the wings on that plane are version 4.7.8.9, they're not compatible with your shirt colour. You should wear red instead of a blue shirt. Otherwise I won't be able to use the wing flaps.


Etc ... etc...

---

### Post by pauljw on 2017-08-14
So in 10yrs all you've managed to learn is how to compare linux to windows and complain that it's different.  

Millions of people successfully use linux every day without issues like yours.  One major difference between linux and windows is a lack of vendor supplied drivers, developers must reverse engineer new devices and write linux drivers for them, this takes time.  

As a linux user you must verify device compatibility prior to purchase as the latest and greatest has more of a chance that there hasn't yet been a driver created for it.  Don't blame linux for this, blame the vendor.  

There are manufacturers that do an excellent job at supporting linux, Dell computers and HP printers come to mind.  Intel systems seem to be better than others.  If doing a bit of research and then some tinkering, maybe even in a terminal session, is more than you can tolerate, perhaps linux isn't for you.  It isn't for everyone.  Windows and Apple aren't for me.  Each of us has needs and desires that we have to decide the best method of meeting in many areas of our lives including which OS is best for us.

Good luck with whatever you choose to use.  :)

Paul

---

### Post by oldos2er on 2017-08-14
Nice note to end on, thanks Paul.

---

