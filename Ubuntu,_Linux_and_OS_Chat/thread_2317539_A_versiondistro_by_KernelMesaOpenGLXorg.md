---
title: "A version/distro by Kernel/Mesa/OpenGL/Xorg"
date: 2016-03-17
forum: Ubuntu, Linux and OS Chat
---

### Post by edu6 on 2016-03-17
Hi. First of all, sorry about my english ;)

I'm stuck for days trying to build a htpc with an old hardware. To resume the story, the machine runs **very well** using OpenELEC 5.0.8 32 bits. I'm watching Youtube videos and movies in 1080 without any problem.

The problem when installing Ubuntu/Linux? The video card: XFX Radeon HD 4650 AGP. Btw, to buy a new hardware it's not an option right now =/

So, I tried everything (I think). I tried to use many Ubuntu versions (starting with from 15.10 to 12.04) and Linux distros (Debian, Mint,...). I also know that is a question of Kernel and the lack of support of the proprietary drivers.

OpenELEC 5.0.8 32 bits have this (xorg.conf is attached):


[LIST]
[*]Kernel 3.17.8
[*]Xorg 1.16.4
[*]OpenGL 3.0
[*]Mesa 10.3.7
[*]"radeon" drivers
[/LIST]

So... there's a way of reproduce these conditions? What would be the best version of ubuntu (or distro) to do that?

Thanks in advance!!!

---

### Post by edu6 on 2016-03-19
Not a "bump". More infos...

[COLOR=#252C2F][FONT=Segoe UI]How I'm doing (yeah, it's painful): I install/upgrade the OS, install the drivers and test the video card on the same conditions of OpenELEC (Youtube and movies - local HDD and network - in 1080). For each attempt (driver), a new installation. Yeah, I'm a little crazy (I have time and patience) =P

[/FONT][/COLOR][COLOR=#252C2F][FONT=Segoe UI]I'm trying everything... Ubuntu (11.04, 11.10, 12.04, 12.04.1,... 16.04-beta1; Ubuntu Gnome, Lubuntu, Debian, Mint,...). As I said, "for each attempt (driver), a new installation".

About the drivers, [/FONT][/COLOR][COLOR=#252C2F][FONT=Segoe UI]open source drivers, Oibaf's repositories or the proprietary drivers. Only one attempt was successful: with Ubuntu 11.04 + proprietary driver version 12.4 =/

Again, thanks in advance =)[/FONT][/COLOR]

---

### Post by buzzingrobot on 2016-03-19
The individual distribution pages at Distrowatch (click on the links in the rankings on the right side) list the version numbers of the major packages in that distribution.  I don't think they'll help with the Radeon issue but the other packages should be there.

If I read this correctly, the 4650 is supported in 12.04.1, 14.04.1, and 15.10.  Boot a live image and see what happens.  ([https://help.ubuntu.com/community/RadeonDriver)]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by edu6 on 2016-03-19
Hi, buzzingrobot. Thanks for your answer.

So, I'm following exactly this, the Distrowatch pages. Based on that, now I'm trying to install the exact versions of the packages (as in OpenELEC). That it will include, if possible, the kernel version; I don't know if it's possible to do that.

I almost have a repository of Ubuntu/Linux distros here lol... I have all the flavours on these versions (12.04.1, 14.04.1, and 15.10).

I'm not trying the live version. I only boot and install. Do you think that can give me a different result to see if I have a good result, as in OpenELEC? Oh, and I followed all the instructions of the RadeonDriver too, the one that (apparently) OpenELEC use.

Cheers from Brazil ;)

---

### Post by grahammechanical on 2016-03-19
From my own experience I know that proprietary drivers drop support for old video adapters. I never install Ubuntu and tick the box "Install third party software." That will bring in a proprietary video driver.

I always install to the open source video driver and then look for a legacy proprietary video driver after I get to a working desktop. We can also install the third party audio & video codecs by installing Ubuntu Restricted Extras from the Ubuntu software centre.

Your video adapter is AGP? I doubt if it will run Ubuntu + Unity. How much of its own memory does that video adapter have? You might be better off installing Lubuntu and not Ubuntu.

Regards.

---

### Post by edu6 on 2016-03-19
Hi, grahammechanical.

> I never install Ubuntu and tick the box "Install third party software." That will bring in a proprietary video driver.
Me too.

> I always install to the open source video driver and then look for a legacy proprietary video driver after I get to a working desktop. We can also install the third party audio & video codecs by installing Ubuntu Restricted Extras from the Ubuntu software centre.
me too, but the proprietary driver only for tests.

> Your video adapter is AGP? I doubt if it will run Ubuntu + Unity. How much of its own memory does that video adapter have? You might be better off installing Lubuntu and not Ubuntu.
Yes, AGP. My goal it's to have all done using Ubuntu Gnome. The video adapter have 1GB. I'll try Lubuntu tomorrow, I think.

My focus it's on Ubuntu Gnome as I said. I tried in other flavours of Ubuntu, Debian and Mint too. I think that Arch will be a good try.

It's very interesting to see the performance of OpenELEC with the same machine/video adapter. Incredible for me lol

The big difference between OpenELEC and the distros that I'm trying it's that the second are very robust. Maybe Lubuntu and Arch can do what I need (reproduce the performance of OpenELEC).

---

### Post by goofprog on 2016-03-22
try ... [http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)

---

### Post by mastablasta on 2016-03-23
openelec is at version 6. use that + 12.04+ proprietary AMD drivers for best experience.

option 2 is to use 14.04+opensoruce drivers make sure you use the correct "switches" available to improve experience.

---

### Post by edu6 on 2016-03-23
Hi, mastablasta.

> **mastablasta said:**
> openelec is at version 6. use that + 12.04+ proprietary AMD drivers for best experience.
I tried **Ubuntu **12.04 + opensource drivers + Oibaf's repository. After some tests, reinstalled the OS and tried with the proprietary AMD drivers. No deal.

> **mastablasta said:**
> option 2 is to use 14.04+opensoruce drivers make sure you use the correct "switches" available to improve experience.
I don't know what you wanna say about "switches", but I tried 14.04/14.04.1 and specially 14.04.2 with open source and then Oibaf's repository. No deal. Today I'll try one more time with 12.04 and 14.04 following your tips.

[COLOR=#a52a2a]***goofprog**, [/COLOR]it doesn't work for my HD 4650 (that driver it's for "R9 200, R7 200, HD 7000, HD 6000, and HD 5000 Series")[COLOR=#a52a2a][/COLOR].


I have some new results. Yesterday was a looong day...

I didn't have enough patience to install **Arch**. I'm a beginner when trying to install an OS like that. The problem is the wiki and the beginners guide. I'll try another day/guide.

The best results (until now) were with **Manjaro **(Arch based). Movies/videos in 1080 (from local network) are ok (not amazing). Videos from Youtube are terrible. I'm using the open source drivers.

It seems that it will be impossible to reproduce something of **OpenELEC **(5.0.8; 32 bits): CPU usage of 12% and Used Memory of... **79MB**. The desktop environment is 'violently light' and it's a very clean OS based on Linux.

In my case, I think that the open source drivers doesn't help. I read a lot about the 2D acceleration. I just haven't tested with 'glamor' yet (it's a bit confusing to me the usage/installation).

As I said, it's an old PC (circa 2004). I have some pics of the OpenELEC's specs on it:

[ATTACH=CONFIG]267945[/ATTACH] [ATTACH=CONFIG]267946[/ATTACH] [ATTACH=CONFIG]267947[/ATTACH]

---

### Post by mastablasta on 2016-03-23
now I am not sure what you are trying to do. are you saying that you do not have enough hardware acceleration available to view 1080p videos? the card should easily handle the videos. especially if this is a 1GB version. I mean if Raspberry Pi can do it surely a much stronger GPU can.

Manjaro uses XFCE as far as I know. why are you not just installing openelec? take latest stable 64 or 32 bit and install it: [http://openelec.tv/get-openelec](http://openelec.tv/get-openelec)

---

### Post by edu6 on 2016-03-23
> **mastablasta said:**
> why are you not just installing openelec?

Hi, mastablasta.

I'm using it. I'm not saying that I don't have enough hardware acceleration available to view 1080p videos because OpenELEC show me that it's possible.

What I'm trying to do is to have the same results with a Linux distro. Ok, OpenELEC it's good, but I want freedom. I don't want to depend of add-ons that sometimes doesn't work (ex. the Youtube add-on gave me a big headache last night; died at the 5.1.16 version and the developer doesn't maintain since the end of 2015). OpenELEC it's good but the 32bits version died at the 5.0.8/Kodi 14.1 version. It's good but sometimes the sound management it's a mess too. Oh... the network management it's problematic (loose connection using my wireless adapter). These (sound and network) are problems that I don't have with a regular Linux distro.

I know that a Linux distro it's more robust than OE but it's important to have resources and the chance of changes/updates,...

---

### Post by mastablasta on 2016-03-24
what are you full system specs? do you actually need a 32 bit OS?

i am still not sure what the problem is. Ubuntu will also soon be 64 bit only. for older PCs Lubutnu and such is recomended.

by end of the year Google Chrome (the only one with updated flash player) will be 64 bit only i believe

---

### Post by edu6 on 2016-03-24
Hi, mastablasta. here we go =D

> **mastablasta said:**
> what are you full system specs? do you actually need a 32 bit OS?
Full specs:

[LIST]
[*]Mobo Asus P4S800D-X;
[*]P4 2.4GHz 32bits;
[*]2GB RAM;
[*]Radeon HD 4650 1GB AGP;
[*]Sound Blaster Live! 5.1.
[/LIST]

That's why I need a 32bits OS.

> **mastablasta said:**
> i am still not sure what the problem is. Ubuntu will also soon be 64 bit only. for older PCs Lubutnu and such is recomended.
About the problem, there is a set of factors:

[LIST]
[*]OpenELEC it's a (very) lightweight OS based on Linux
[LIST]
[*]Linux Kernel 3.17.8;
[*]Xorg 1.16.4;
[*]Mesa 10.3.7;
[*]OpenGL 3.0;
[*]Radeon drivers (open source).
[/LIST]

[*]Any Linux distro it's robust if compared to OpenELEC (off course);
[*]I have a fresh install of Arch Linux, so I'm testing each lightweight DM available (Enlightenment, LXDE, XFCE,...);
[LIST]
[*]The results are compared to Manjaro (Arch based);
[/LIST]

[*]My tests are made with movies (1080p) and HD videos in Youtube (1080p and 720p);
[LIST]
[*]in OpenELEC, perfect;
[*]*[Any]*buntu, Debian, Mint,... terrible;
[*]Manjaro, less than terrible and far from perfect. The same on Arch+DMs.
[/LIST]
[/LIST]

As you can see, despite of OpenELEC's performance, I'm trying to use a Linux distro because... I want (lol)... and to have the same results/performance. Arch it's very lightweight, so I'll make one more test: downgrade the Kernel and all the packages to reproduce OpenELEC's conditions.

I know that are people that know Ubuntu and other distros better than me, so I'm here to talk about what I'm trying and discuss the possibilities.

> **mastablasta said:**
> by end of the year Google Chrome (the only one with updated flash player) will be 64 bit only i believe
In my opinion, a bad thing. There's a lot of smartphones that are 32bits (including mine, Moto X 2nd gen). I have 4 PC's at home; a Dell 64bits, 3 generic PCs 32bits. There's a lot of companies (here in Brazil) running 32bits workstations. 64bits it's a thing for OpenELEC, for example, because of the RPi and other solutions. I don't believe that is a thing for Chrome.

---

