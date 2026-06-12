---
title: "Is it true that Bootcamp on OSX allows you to run almost any Windows app/game in OSX?"
date: 2009-10-14
forum: The Cafe
---

### Post by hoppipolla on 2009-10-14
My friend says that with Bootcamp, he can run any Windows game or app with little slowdown or performance impact within OSX (he didn't actually mention that this involves DUAL BOOTING with Windows, but still! lol)

Is this true? Why can't we do this on Linux or is it possible with virtual machines? As of course Cedega/Crossover/Wine doesn't allow you to run anything at all!

Please fill me in on this one because I'm rather confused! lol

Hoppi :)

---

### Post by Kobalt on 2009-10-14
Bootcamp alone doesn't permit running Windows applications, it requires a reboot and launching Windows (as far as I know). 
I think Parallel Desktop combined with Bootcamp can achieve this (although not sure, again, you don't have to boot Windows in a virtual machine). But I'm quite sceptical about the performance keeping for that option.

---

### Post by blueturtl on 2009-10-14
Seems like a simple mistake.

Bootcamp will allow you to actually run Windows on a Mac.
Hence any software that Windows can run, you can run on a Mac.

---

### Post by suitedaces on 2009-10-14
Am I misreading this, or is a "windows runs windows apps shocker" thread?

---

### Post by 3rdalbum on 2009-10-14
Bootcamp does three things:

1. Adds BIOS-compatibility to the Macintosh IEFI (booting system) so Windows can boot
2. Partitions your hard disk so there's somewhere to install Windows to
3. Provides you with some drivers so you can use your Mac hardware in Windows.

There's no virtualisation involved and no Wine-like compatibility layers. It just allows you to create a dual-boot system. The Intel Macintoshes originally shipped without the BIOS-compatibility, which was odd because IEFI includes it by default. Boot Camp was announced about a week after some hackers got Windows to boot on the Macintels - it's clear that Apple didn't really want people running Windows directly on Macintosh hardware, but they'd rather people do it safely than rely on a reverse-engineered effort that could potentially brick your computer.

There was actually a community bounty to get Windows to work on a Macintel; it was quite thrilling to see people chipping in with their ideas and say what progress they had been making. I believe the Linux community should do more bounties, it would make things a lot more exciting!

---

### Post by SunnyRabbiera on 2009-10-14
Bootcamp might as well be virtualbox in the end, if you are unhappy with Wine give virtualbox a shot if you have a CD copy of windows.

---

### Post by hoppipolla on 2009-10-14
Oh ok, because he seems to think it does something really special within OSX that a standard VM doesn't do, like he can run all his Windows apps and games and that with minimal slowdown, and that it has some way of "coming out of Mac OS entirely and running Windows"... doesn't sound very true to me unless I'm missing something...

Fill me in a bit more here o.O  I'm well confused lol

---

### Post by ElSlunko on 2009-10-14
It allows you to dual boot.

It's part of Apple's great marketing ability IMO. Makes it sound fancy, but it's just a dual boot.

---

### Post by issih on 2009-10-14
Your friend, or at least your interpretation of their belief is wrong.

Bootcamp is no different to dual booting any computer with windows, that is all it is, nothing more or less.

Virtualisation software to allow you to run a version of windows within OS-X is of course available,(parallels, etc) but that is also true of linux, and all virtual machines suffer some element of slowdown due to the virtualisation overhead, the exact amount will depend more on the capabilities of the hardware being used, than the software.

Finally, compatability layers exist that transpose windows API calls into native code calls. In this arena, wine is king, and the mac equivalent is darwine, which is really nothing more than a mac port of wine, which in fact requires the X server to run at all, even on a mac.

There is nothing special about bootcamp..

---

### Post by KiwiNZ on 2009-10-14
> **hoppipolla said:**
> Oh ok, because he seems to think it does something really special within OSX that a standard VM doesn't do, like he can run all his Windows apps and games and that with minimal slowdown, and that it has some way of "coming out of Mac OS entirely and running Windows"... doesn't sound very true to me unless I'm missing something...

Fill me in a bit more here o.O  I'm well confused lol

Bootcamp allows you to Dual boot a Mac with either OSX or Windows be it ,XP , Vista or Win 7.

It needs this additional support as Macs do not use a traditional Bios as such they use a Apple Firmware .

---

### Post by Bachstelze on 2009-10-14
BootCamp is not a very well defined term.

[http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)

But anyway, it all has to do with dual booting, not virtualization. I don't really agree with the "it usually helps" part about the BootCamp Assistant, by the way. All it does is hold your hand through the process, most people shouldn't need it.

---

### Post by doorknob60 on 2009-10-14
Bootcamp is just dual booting, all boot camp does is sets up partitions, drivers, etc. You can also use Bootcamp to install Ubuntu (or any other distro) if you wanted to. It's nothing we can't already do on our computers :)

---

### Post by hoppipolla on 2009-10-14
Oh ok cool, I'll have another chat to him and see what he thinks! I really don't think he likes Linux though for some reason, he seems to always go for Mac and Windows even if you can prove that Linux can do this stuff too and is really cool.. I dunno, I'll tell him anyway :)

---

### Post by starcannon on 2009-10-14
> **SunnyRabbiera said:**
> Bootcamp might as well be virtualbox in the end, if you are unhappy with Wine give virtualbox a shot if you have a CD copy of windows.
VirtualBox is a great remedy for certain types of apps. Currently D3D is very, experimental, and results in very poor performance in those rare instances when it works at all.

If your a gamer, and you play lots of MS Windows based games, dual booting is still in your present and future.

---

### Post by hoppipolla on 2009-10-14
> **starcannon said:**
> VirtualBox is a great remedy for certain types of apps. Currently D3D is very, experimental, and results in very poor performance in those rare instances when it works at all.

If your a gamer, and you play lots of MS Windows based games, dual booting is still in your present and future.

ah. Do Macs have a way of doing this better?

It doesn't really affect me that much as I love Lin, but he wants this capability o.O

---

### Post by KiwiNZ on 2009-10-14
> **hoppipolla said:**
> ah. Do Macs have a way of doing this better?

It doesn't really affect me that much as I love Lin, but he wants this capability o.O

You can give Parallels a go , it costs , there is a trial version on the Parallels website .

---

### Post by handy on 2009-10-14
I've been using Codeweavers Crossover for a couple of years under OS X 10.5., to play Guild Wars.  I can run Guild Wars via Wine, Cedega or a Crossover under Linux on the same machine, but unfortunately the ATi GPU drivers are still not as good as those for the Mac.

Bootcamp is made to dual boot Windows specifically & can't be used for Linux.

I use rEFIt to handle dual booting Linux on the iMac. rEFIt is simple to install, set up & use, & it is free.

I've never used Bootcamp, I'm 4 years totally free of windows. :)

By the way, the Codeweavers guys are the biggest supporters of Wine; it is where the main Wine dev's get some money to live.

---

### Post by blur xc on 2009-10-14
> **KiwiNZ said:**
> You can give Parallels a go , it costs , there is a trial version on the Parallels website .

I tried parallels on the recommendation of a friend who said it works better than Vbox, but turns out at the time (a few months ago) it only supports Ubuntu 7.xx (don't exactly remember), which I found out after a while of screwing around, failed installs, and rounds w/ their tech support.

Try Vbox, it's free, and it's working pretty well now.

BM

---

