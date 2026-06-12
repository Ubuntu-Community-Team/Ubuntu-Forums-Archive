---
title: "How are the ATI drivers in Linux?"
date: 2010-03-09
forum: The Cafe
---

### Post by RussianVodka on 2010-03-09
I got my new laptop yesterday from Dell, and it has a Radeon 4570 in it. The computer has a 320GB HD, which is more then enough to dual boot and have sufficient space for both OS's, but the last time I had an ATI card the Linux drivers were horrendous. Granted, this was about 5 years ago.

So, before I go and partition my hard drive and install Ubuntu, can anyone tell me about their experience with ATI cards in recent years?

---

### Post by snova on 2010-03-09
> **RussianVodka said:**
> I got my new laptop yesterday from Dell, and it has a Radeon 4570 in it. The computer has a 320GB HD, which is more then enough to dual boot and have sufficient space for both OS's, but the last time I had an ATI card the Linux drivers were horrendous. Granted, this was about 5 years ago.

So, before I go and partition my hard drive and install Ubuntu, can anyone tell me about their experience with ATI cards in recent years?

Fglrx works well for me. I'm hardly a heavy user of my card (a Radeon 5750), but I've never noticed any issues in the time that I've had it. Installation (using the download from their site) is reasonably painless and I have a working dual-monitor setup.

Anything more complicated than that I can't speak for, but the worst that can happen is that it doesn't work.

---

### Post by undecim on 2010-03-09
fglrx works fine for me, too. ```
undecim@caffeine ^_^ ~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```

---

### Post by Xbehave on 2010-03-09
Open source drivers on the latest kernel (2.6.33, so wait for lucid) are very stable for me and performance for 2d/basic 3d effects (kwin/compiz not gaming) work well enough. my card is quite old though
```
VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
```
not sure what model it is, some embedded stuff (aspire 5101)

---

### Post by ddp127 on 2010-03-09
They are reasonable, still not perfect of course, but it has improved a lot

---

### Post by doorknob60 on 2010-03-09
Works just fine for me (with Catalyst) :)

---

### Post by admiralspark on 2010-03-09
> **Xbehave said:**
> Open source drivers on the latest kernel (2.6.33, so wait for lucid) are very stable for me and performance for 2d/basic 3d effects (kwin/compiz not gaming) work well enough. my card is quite old though
```
VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
```not sure what model it is, some embedded stuff (aspire 5101)

It's an ATI Radeon XPress 200M, which I also have. Compiz works 100% on 9.10 here, but I wouldn't suggest trying to play anything more graphics intensive than OpenArena. 

2D ATI graphics is mostly perfect, 3D is coming well but still has a little ways to go for it to be perfect. It's definitely liveable.

---

### Post by Pressondude on 2010-03-09
I have intermittent issues with my Radeon HD 4670, but I've noticed that they've gotten a lot better. I will say that switching to Kubuntu (which doesn't use Compiz) helped as well. I have some hang-ups, but to be honest, the card has some issues in Windows XP when I run my CAD software.

---

### Post by earthforce_1 on 2010-03-09
Running an i7 with a new HD5970 on 64 bit Karmic and they absolutely suck.  The fglrx driver boots into a black unusable screen and you need the grub rescue to remove it!  (Tried with two different monitors)  The open source drivers don't drive my monitor properly, so I am running 1600x1200 instead of 1920x1200 and everything is blurry and stretched.

I did have it working with my previous 4870x2 card, I upgraded because I was having hardware issues and I am sorry I stuck with ATI.  I need a high end card to run X-Plane 9 on my normal Syncmaster 305T monitor, which is down for repairs.


lspci -nn | grep ATI
04:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:689c]
04:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa50]
05:00.0 Display controller [0380]: ATI Technologies Inc Device [1002:689c]

---

### Post by ndefontenay on 2010-03-09
It works just fine for me.

---

### Post by earthforce_1 on 2010-03-09
> **ndefontenay said:**
> It works just fine for me.

What card are you running?  Have you tried it with the HD5970?  Are you running the 64 bit OS?

---

### Post by handy on 2010-03-10
> **RussianVodka said:**
> I got my new laptop yesterday from Dell, and it has a Radeon 4570 in it. The computer has a 320GB HD, which is more then enough to dual boot and have sufficient space for both OS's, but the last time I had an ATI card the Linux drivers were horrendous. Granted, this was about 5 years ago.

So, before I go and partition my hard drive and install Ubuntu, can anyone tell me about their experience with ATI cards in recent years?

Check out this page:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Then head to the last couple of pages of that thread to see where (mostly) the OSS support development is up to?

I try to keep the thread reasonably up to date, & since I've very recently started using an Arch -git repo I will be continually giving feedback on how the development is coming along re. the OSS drivers. 

The OSS AMD/ATi support will without a doubt become incredibly popular in the FOSS world as time rolls by, as AMD have opened up their tech' info' on ALL of their GPUs, which is of course having the effect of accelerating the development of the FOSS code. :D

This is allowing AMD to set the highest of standards for all of the other proprietary manufacturers to hopefully eventually follow.

---

### Post by markbuntu on 2010-03-10
If you are using a very new laptop with a new ati mobility gpu, you need a very new driver for it. You will not get this from the hardware manager, you need to get it from the ati website. If you have not yet enabled the driver from hardware manager then do not enable it, use the latest ati driver. 

If you have installed a driver that does not work, you need to remove it before installing the latest driver. There are a bunch of threads around here that have detailed instruction for doing all that, like this one:


[http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)

FYI The ATI Mobility HD GPUs used in laptops are not identical to the HD GPU cards so if you ask for help please specify if your gpu is a Mobility series or not.

---

### Post by lethalfang on 2010-03-10
Catalyst 10.2 does not work on my laptop.
I use Catalyst 10.1.

---

### Post by quadproc on 2010-03-10
> **RussianVodka said:**
> I got my new laptop yesterday from Dell, and it has a Radeon 4570 in it. 

So, before I go and partition my hard drive and install Ubuntu, can anyone tell me about their experience with ATI cards in recent years?

I am running HD4870 X2 in 64 bit mode and presently I am pleased.

However, I have had a lot of trouble getting to the present satisfactory state of affairs.  Short recap: I started with Ubuntu 8.10 and could not get X windows to run except in safe video mode; eventually I learned that the X server couldn't decide which video card was primary so it quit executing and left me with a glass teletype interface.  The workaround for this was to add a BusID to one of the cards in the xorg.conf file.  Later, I upgraded to 9.04 and was left with a dead system.  It would boot up to the point of being ready to display the X windows stuff and then die.  It took two very long days to get the system running again; part of what I did during these two days was to switch to the vesa driver and that seemed to alleviate a lot of problems.  Finally, after getting everything else squared away, I changed back to fglrx and things are now working well.  I have not yet worked up enough courage to upgrade to 9.10.  Soon, though.

A few notes regarding fglrx: ATI is no longer supporting drivers for their older architecture video cards so people with older hardware are quite unhappy.  You'll need at least Ubuntu 9.04 to run the current crop of ATI drivers.  Be sure that the version of the driver that you install is compatible with your hardware, and is either 32 or 64 bit according to your system's bus width.  The fglrx file is a little over 80 MB so you'll need enough bandwidth to download it in a reasonable amount of time.  I suggest downloading the file from the ATI site and then executing it thus:
cd <a_local_temporary_directory>
(move the ATI file to here)
<the_correct_ati_file>.run --keep --install
The keep option will leave behind all of the files that it used for installation so that you can peruse them later if you are interested.  Of course, you can remove all of that directory when you are done with it.

Perhaps the most relevant comment: I personally think that ATI is listening to their potential customers and is reacting to their input.

Would I choose to use ATI hardware if I were configuring another system?  Probably.

Hope this helps.

quadproc

---

### Post by cdekter on 2010-03-10
From my personal experience the last 2 weeks... you will not realise how garbage the Catalyst drivers are until you try a system running the latest nVidia drivers. They are worlds apart. Catalyst on my system with a HD4570 are OK with 2D only, but just try using Compiz/KWin compositing and you will experience a world of lag. The performance is hopeless.

Try the same thing on nVidia (my new laptop has nVidia 310M) and you will be blown away by the instant response and smooth performance. Seriously, if you love your sanity don't get an ATI card.

Maybe in 6 months or so when the radeon driver is more mature and 3D is working on all the latest cards, the situation will be different. Right now, I wouldn't take an ATI card if it was given to me for free.

---

### Post by 3rdalbum on 2010-03-10
> **admiralspark said:**
> It's an ATI Radeon XPress 200M, which I also have. Compiz works 100% on 9.10 here, but I wouldn't suggest trying to play anything more graphics intensive than OpenArena.

Back when there was a Catalyst driver for it, the Xpress 200 desktop version couldn't handle much more than OpenArena. I used to play Nexuiz on it a few years ago but at very low detail and resolution. The Xpress 200M would be even worse.

---

### Post by markbuntu on 2010-03-10
ATI drivers may be sucky but they wont melt your gpu like nvidia.

---

### Post by handy on 2010-03-11
The AMD/ATi GPUs are in the mid stages of the process that will eventually make them the darling of the FOSS GPU world.

By the end of this year, even Ubuntu (which uses versions of packages that are far from the cutting edge) will be able to provide very good open source support for the ATi GPUs, including power management. :)

This page will give you an idea of where the development is currently up to:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

### Post by kru83 on 2010-03-26
> **snova said:**
> Fglrx works well for me. I'm hardly a heavy user of my card (a Radeon 5750), but I've never noticed any issues in the time that I've had it. Installation (using the download from their site) is reasonably painless and I have a working dual-monitor setup.

Anything more complicated than that I can't speak for, but the worst that can happen is that it doesn't work.

i have question, how did u get the 5750 to work.  I installed ubuntu.  than i went in and installed the prepotiary driver for graphic card.  once i did the restart i get to the boot screen and it goes black. i can hear the sound in the back ground and i can also login in if i press the left mouse key and put the password in and hit enter.   any tips would help.

---

### Post by prodigy_ on 2010-03-26
One word: disastrous.

---

### Post by shebaw on 2010-03-26
I have the exact graphics card, ATi Radeon HD 4570 and I had serious issues with it when I upgraded the wireless network modules. So the best thing to try is to install Envy and let it manage your graphics card. I have 3D effects enabled but it still needs some work, I heard its better on Lucid but I didn't give it a try.

---

### Post by iRiUX on 2010-03-26
> **shebaw said:**
> I have the exact graphics card, ATi Radeon HD 4570 and I had serious issues with it when I upgraded the wireless network modules. So the best thing to try is to install Envy and let it manage your graphics card. I have 3D effects enabled but it still needs some work, I heard its better on Lucid but I didn't give it a try.
You better not. I have the same card and the drivers don't work for me in 10.04. I'm using the open-source drivers, which I'm actually quote happy with.

In 9.10 however, it should just work. I don't know what issue you're having, but just [download]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-3-x86.x86_64.run") the latest driver from ati website and "sudo sh ati-driver-installer-10-3-x86.x86_64.run"

The drivers in Ubuntu repository are always very old (except for the one currently in lucid, but that's a beta and it doesn't work for me).

---

### Post by shebaw on 2010-03-27
Did they release ATi driver installer 10.3? I was using 10.2 fine till I updated my wireless modules since I was having serious issues with my Atheros9K driver. So does the ATi driver from the amd website work on lucid or what?

---

### Post by andrek on 2010-03-27
And I have ATi Mobility 4570 and it just works great with the fglrx driver in Ubuntu 10.04.

---

### Post by realzippy on 2010-03-27
Runs great?

...depends on *what* you run.Many people saying they are ok do not run openGL/3D stuff.
Compiz with 16x FSAA,8x AF,3 MB animated skydome image,quakelive on one desktop while TV running on another means that it is a good driver,unfortunately this driver is not from ATI...  ;-)

---

