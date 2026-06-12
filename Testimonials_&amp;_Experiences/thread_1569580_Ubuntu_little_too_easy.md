---
title: "Ubuntu little too easy"
date: 2010-09-06
forum: Testimonials &amp; Experiences
---

### Post by Makosz on 2010-09-06
I have installed Ubuntu on my computer thinking i will learn Linux as i go. Well I have learned some but now came to dead end. Ubuntu is made so well that i dont need to use bash at all if i dont want to. Is there a way to learn it little more because i don't think i know a lot at all because there was almost nothing i had to do in bash. Or is there another distribution that is easy but makes me learn more. 

I love Ubuntu and have no complains so far but I just want to learn Linux because i wanna advance into what seams really advanced distro Backtrack 4, I know it is Ubuntu based now but there is still a lot knowledge needed to use it to its potential.

Thank You!!

---

### Post by louis--taylor on 2010-09-06
What do you want to learn?

---

### Post by an0dos on 2010-09-06
If you want to use something more painful, err... difficult, you can always try fedora.

---

### Post by Makosz on 2010-09-06
Well best way to put it I want to learn it all. Easier way to put it is anything in Linux that will make me be able to configure hardware and know how to use tools on a computer or know how to figure them out without research on internet. Of course i have to browse the computer.

or at least if thats possible

---

### Post by Supergoo on 2010-09-06
Well if you want harder, here is my suggestions:


Arch Linux

Slackware


Gentoo


One of those should meet you requirements, as for me I think I will take the easy ubuntu way. But each person has to make their own minds up for what is for them, Good Luck and Best Wishes

---

### Post by valbaca on 2010-09-07
It's **wonderful** to hear that you had such a smooth ride into the world of Linux!

Over the past year of distro-hopping, I have the following to offer:

Fedora's an okay place to try, but Fedora isn't as difficult as it is just on the bleeding edge. It won't teach you as much about "Linux" as it will about how Red Hat will look in a couple of years.

Slackware is an interesting one. It does teach you about Linux...at least how Linux **used **to be. I now see its appeal: it comes with all sorts of developers tools (build-essential in Ubuntu), emacs, and KDE/XFCE/Openbox/etc.

Arch Linux is probably the best way to learn about how much Ubuntu already does for you. It is amazing for the most up-to-date and minimal (as in it only has what you put in it) distro. Great learning experience and is **the** distro for some.

Debian...what can I say about Debian....for the install you'll only need the first DVD. Beyond that, you'll really have to decide for yourself.

In the end I realized I was spending too much time "learning Linux" (when I already had learned enough for my purposes) that I decided to stick with **one** distro, contribute back, and get to spreading "the word" of free software.

I decided to stick with Ubuntu 10.04 because of 

[LIST]
[*]stability
[*]3-years support
[*]wonderful compatibility with my laptop
[*]tethering support for my phone (EasyTether for Android)
[*]great community
[*]great case for spreading Linux (it isn't easy selling Arch Linux to a total newbie you run into)
[*]I like where Ubuntu's going
[/LIST]

---

### Post by jrusso2 on 2010-09-07
Install the server version of Ubuntu.  Its command line interface will make sure you learn,

---

### Post by MarcusW on 2010-09-07
> **jrusso2 said:**
> Install the server version of Ubuntu.  Its command line interface will make sure you learn,

+1,
Learning to manage without X11 will probably teach you some things, hopefully without learning completely unnecessary things. :)

---

### Post by sxmaxchine on 2010-09-07
The hardest distro i used was archlinux

---

### Post by KdotJ on 2010-09-07
> **an0dos said:**
> If you want to use something more painful, err... difficult, you can always try fedora.

I wouldn't call Fedora that painful. I used it before I moved to Ubuntu and I didn't find it that much of a problem at all. But maybe I was lucky with my rig...


To the OP, you could always try the Ubuntu minimal installation (which is a bare bones system: no desktop, no default programs installed) which you have to configure yourself.

Or Arch is a good one which also comes with no desktop. I'm just looking in to Slackware myself as I want to learn a little more about linux itself

---

### Post by Makosz on 2010-09-07
If i install eaither the bare version or server version will my wireless card still work? I have inspiron 13 with BCM 4315 or 4312 wireless card i've seen both ways. This is the only machine ia hve so want to still be able to research anything needed. Does slackware have openoffice.org version for it or something like that?

What does it mean when OS comes with no desktop?

---

### Post by julianb on 2010-09-07
I made Ubuntu challenging for myself. Try Lubuntu, and then put it through its paces. Here's what I wanted:
-Minimal hard drive space for the OS. Preferably less than 1.9GB.
-Good performance on a machine with 512mb RAM.
-Compatibility with adobe flash, & with the built in eeepc webcam / microphone.
-easy to use on 7 inch screen. in French.
-able to record video using webcam. (no success yet).
-fast start and shutdown.

---

### Post by Jazzy_Jeff on 2010-09-07
> **Makosz said:**
> If i install eaither the bare version or server version will my wireless card still work? I have inspiron 13 with BCM 4315 or 4312 wireless card i've seen both ways. This is the only machine ia hve so want to still be able to research anything needed. Does slackware have openoffice.org version for it or something like that?

What does it mean when OS comes with no desktop?

When you log into Ubuntu you get the Gnome desktop. That is the graphical user interface. Without the desktop you get just a command prompt.

---

### Post by julianb on 2010-09-07
If you install from an ubuntu-server or ubuntu-minimal CD, it is possible to install wireless support but wireless support is probably not included by default. 

There's a command line tool called iwconfig that is designed to get you connected to a wireless network using the command line. 

```
iwconfig --help
```

I think if you run the above command, it will either give you the iwconfig help printout, OR if the command is invalid, it will tell you which package you need to "apt-get install" so that you can use the iwconfig command.

---

### Post by KdotJ on 2010-09-07
> **julianb said:**
> I think if you run the above command, it will either give you the iwconfig help printout, OR if the command is invalid, it will tell you which package you need to "apt-get install" so that you can use the iwconfig command.

This is not possible without an internet connection, well Ubuntu will suggest packages but apt-get needs the internet...

In my experience, with minimal installations and with Arch, I've had to have the laptop connected to the internet via an ethernet cable to install the drivers for my wireless card. Then of course after I no longer need to be connected via cable

---

### Post by Makosz on 2010-09-07
So if I get the iwconfig package then afterwards i will not have to connect via cable?
I am almost 100% sure its possible but i wanna make sure. Can i install minimal cd and have regular ubuntu at the same hard drive but different partitions?

---

### Post by julianb on 2010-09-07
> Can i install minimal cd and have regular ubuntu at the same hard drive but different partitions
Yes.
> So if I get the iwconfig package then afterwards i will not have to connect via cable?
Yes, provided you can figure out how to use iwconfig. as I recall, you have to know what device you are configuring (it might be ath0, wlan0, or something else) and you have to set the "essid", plus set the "key" (password) if there is one. 

I'm not sure what's the name of the package that contains the iwconfig command, BUT i think if you type "iwconfig --help" when you don't have the package installed, it will tell you what package you need.

---

### Post by wojox on 2010-09-07
> **Makosz said:**
> 
I love Ubuntu and have no complains so far but I just want to learn Linux because i wanna advance into what seams really advanced distro Backtrack 4, I know it is Ubuntu based now but there is still a lot knowledge needed to use it to its potential.

Thank You!!

BT4 is just Ubuntu + Kde + Security applications. You can actually install all the same apps in Ubuntu as BT4.

---

### Post by Makosz on 2010-09-07
Yes I know but the kernel difference will not let me use some of the applications. Also all the support by the Backtrack team stops. 

Making sure that everything is prepared to change into Ubuntu minimal seems to let me learn more about Linux too. Slackware seams really good but I wanna stay with Ubuntu because of all the support and easy I had so far so I don't think it will be too hard to learn more with minimal.

Now how do i know if my machine is 64bit or 32bit? I looked online and it said to run
```
$ grep flags /proc/cpuinfo

```

And I got output of

```
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm

```

---

### Post by v1ad on 2010-09-07
uname -a will tell you if your os is x64, or x86. your cpu is mostly likely compatible with x64, i would just get the cpu info an look it up to see.

---

### Post by wojox on 2010-09-07
lm means Long Mode 64 bit

---

### Post by andrew.46 on 2010-09-07
Hi Makosz,

> **Makosz said:**
> Does slackware have openoffice.org version for it or something like that?

Have a look here:

[http://slackbuilds.org/repository/13.1/office/openoffice.org/](http://slackbuilds.org/repository/13.1/office/openoffice.org/)

Andrew

---

### Post by freebeer on 2010-09-07
You could learn about setting up virtual machines, then install whatever basic OS you want inside that VM.  That way you don't have to reboot in order to get into the other (working) OS when you mess things up.  :)

---

### Post by KdotJ on 2010-09-08
> **freebeer said:**
> You could learn about setting up virtual machines, then install whatever basic OS you want inside that VM.  That way you don't have to reboot in order to get into the other (working) OS when you mess things up.  :)

+1 I always do this first to test it all out. But then I do it for real once I've worked everything out. The downside to VMs is you don't get all the "fun" with sorting out the drivers, and of course the graphics and compositing.

---

### Post by TwelveGauge on 2010-09-08
If you want to learn bash (slowly and bit by bit) and you're running ubuntu...I'd reccomend configuring the shell scripts for a conky or something.

---

### Post by KdotJ on 2010-09-08
> **TwelveGauge said:**
> If you want to learn bash (slowly and bit by bit) and you're running ubuntu...I'd reccomend configuring the shell scripts for a conky or something.

Is conky bash? The script in .conkyrc I mean...?

---

### Post by Makosz on 2010-09-08
Ok I have decided to reinstall my current ubuntu partition get rid of backtrack and only keep windows for now. Than to install both Ubuntu 10.04 full. and than Ubuntu 10.04 minimal which one should i install first? I know that minimal does not have graphical interface so no graphical installer and I do not know about grub.

Thank You

---

### Post by KdotJ on 2010-09-08
> **Makosz said:**
> Ok I have decided to reinstall my current ubuntu partition get rid of backtrack and only keep windows for now. Than to install both Ubuntu 10.04 full. and than Ubuntu 10.04 minimal which one should i install first? I know that minimal does not have graphical interface so no graphical installer and I do not know about grub.

Thank You

The minimal install does have a kind of graphical installer... not a full blown GUI, but what looks like boxes on the screen (similar to that of the first bit of installing XP). It will guide you through the installation of the OS, and also grub. So it's not quite installing by a command line.

---

### Post by Makosz on 2010-09-08
But does it matter which order I do it the reason i ask is because grub messes up when you install BT4 before ubuntu because of the different versions

---

