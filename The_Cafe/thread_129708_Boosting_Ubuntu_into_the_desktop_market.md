---
title: "Boosting Ubuntu into the desktop market"
date: 2006-02-14
forum: The Cafe
---

### Post by TheStig on 2006-02-14
Don't take this the wrong way, I'm not trying to be some ego maniac who thinks he knows everything. I'm very interested in other users ideas, tell me what problems you see with mine... I think within a few years Linux / Ubuntu will gather a lot of speed in the desktop market, a lot of that might be from people getting sick of Vista.


Ok here are the ideas:

1)One of the biggest problems I've found coming from windows is that the software install process can be a big pain on Linux... Now I love apt but it has a big problem it doesn't compile the packages from source. So if it's not in the repository because it's an updated version that just got released or its never been added, you have a problem.. Why couldn't there be an apt for source? So if I wanted to install the latest firefox release I could just ```
apt-get install http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-US/firefox-1.5.0.1.tar.gz
```

           Because I'm not a developer I don't know why this hasn't been done. But it seems like it would be possible to do.

2)LDDB (Linux Device Database) The next problem is getting curtain hardware to work, tv tuners, laptop displays, wireless cards, new mice, etc. A lot of the problems can be solved by just editing a simple text file, but finding the info on what to edit can be a big pain. What if when you installed your new device a program would search a database of config files and download the correct one for your device?

3) Ditch Gnome. 
This might only be a problem for me, but I dislike gnome, I don't like KDE either, both are very bloated. But gnome seems to crash a lot, there isn't a day when it doesn't crash at least once. It seems to be a problem with nautilus. I hate to say it but I think it crashes more in a week than windows did in a month. A nice alternative/s to gnome would be fluxbox (might needs some customizing) or xfce. 



Please add your ideas and comment on mine.

---

### Post by TrendyDark on 2006-02-14
Ubuntu has a XFCE version, Xubuntu.

Good ideas otherwise.

---

### Post by endersshadow on 2006-02-14
1. Because of the fact that each program is packaged differently, you can't just simply install from a tarball.  That's where deb files come in, it's a uniformed way to install files.  At any rate, it's *usually* not any more than 6 commands:

1. wget [http://sourcepackage.tar.gz](http://sourcepackage.tar.gz)
2. tar xzf sourcepackage.tar.gz
3. cd sourcepackage/
4. ./configure
5. make
6. sudo checkinstall -D make install (or sudo make install if you prefer)

However, each program packages differently.  Installation is different for Perl programs, C++ programs, C programs, etc.  .deb files provide a uniform way of installation, which is why they're used as opposed to directly from source.  Moreover, the files in the repositories are officially maintained packages that have been tested and work.

As for #2, I agree, that'd be great, and Ubuntu is working on it.  Check Applications>System Tools>Ubuntu Device Database.  While it's still being developed and worked on, it's a start.

As for #3, I love my Gnome, and don't you dare touch it :)  But the great thing about Linux is that you can choose...XFCE, Openbox, Fluxbox, E16/E17, etc.

---

### Post by nursegirl on 2006-02-14
1. Part of the whole "Ubuntu Just Works" philosophy is that newbies should only be able to apt-get things that the development team know will work.  So, with the default repos you can't apt-get something that will splonk your install.  The hope is that only people who know what they're doing can compile an untested package from source.  It means less flexibility until you know what you're doing, but part of the reason so many people's Windows boxes are a mess is because they install untested, untrusted programs onto their computers.

---

### Post by TrendyDark on 2006-02-14
Kind of reminds me of this girl's computer I once used. She was running Windows ME and had like 15 toolbars in IE, then window was so small and she didn't even notice. I asked her about them all and she said that they just showed up, didn't know how they got there.

---

### Post by aysiu on 2006-02-14
[QUOTE=TheStig]Don't take this the wrong way, I'm not trying to be some ego maniac who thinks he knows everything. I'm very interested in other users ideas, tell me what problems you see with mine... I think within a few years Linux / Ubuntu will gather a lot of speed in the desktop market, a lot of that might be from people getting sick of Vista.[/quote] Ubuntu as is will never gain significant desktop market share. However, some Linux distribution *based* on Ubuntu (either produced by Canonical or not) probably will. Mepis could be in the running for that. Who knows?

It'll take a lot more than "people getting sick of Vista," though. I know a lot of Windows users who don't know how to protect their systems and have all sort of adware and malware on their computers and are "sick of" Windows but who stick with Windows anyway, for whatever reason. My boss, for example, (and her husband) like Macs better, but their most recent computer purchase was a Windows XP computer because they've already bought a lot of Windows software.

Most computer users will not buy a Vista CD (or even pirate Vista) when Vista is released. They'll keep using XP (or 2000 or ME or 98) until they get a new computer. When they get a new computer, that computer will be preloaded with Vista. I don't see, then, why they'd be "sick of Vista."

For Ubuntu or Linux to gain significant desktop market share, several things must happen, and generally (by some freak of nature) all around the same time:

1. There's a huge publicity about Ubuntu--not just in PCWorld, but Newsweek or Time Magazine. Some article that *everyone*, not just computer nerds, reads.

2. Another huge security flaw in Windows is uncovered *and* exploited, but a huge security flaw in Ubuntu is not uncovered around the same time.

3. Crossover Office works with every major Windows program.

4. Some Ubuntu-based distro (but one that includes a lot of proprietary codecs) takes off among the computer-savvy.

5. A large computer manufacturer (Dell or HP) begins selling Linux-preloaded desktops that are easily found/ visible on their website's front page and that are the same price as Windows PCs or slightly cheaper.

6. A couple of cool but in no way nerdy celebrities mention in interviews that they use Linux.

Once those five or six things happen within months of each other, Ubuntu or whatever distro will then make significant strides in desktop market share. That one distro will then be the standard, and anyone making Linux software will have to offer a .deb or .rpm (or even double-click install.sh) compatible with that distribution.

> 
1)One of the biggest problems I've found coming from windows is that the software install process can be a big pain on Linux... Now I love apt but it has a big problem it doesn't compile the packages from source. So if it's not in the repository because it's an updated version that just got released or its never been added, you have a problem.. Why couldn't there be an apt for source? So if I wanted to install the latest firefox release I could just ```
apt-get install http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-US/firefox-1.5.0.1.tar.gz
```

           Because I'm not a developer I don't know why this hasn't been done. But it seems like it would be possible to do. It's not, not the way you've described it.

> 
2)LDDB (Linux Device Database) The next problem is getting curtain hardware to work, tv tuners, laptop displays, wireless cards, new mice, etc. A lot of the problems can be solved by just editing a simple text file, but finding the info on what to edit can be a big pain. What if when you installed your new device a program would search a database of config files and download the correct one for your device? This already happens, actually. When it doesn't, it's because that device isn't part of the database yet.

> 
3) Ditch Gnome. 
This might only be a problem for me, but I dislike gnome, I don't like KDE either, both are very bloated. But gnome seems to crash a lot, there isn't a day when it doesn't crash at least once. It seems to be a problem with nautilus. I hate to say it but I think it crashes more in a week than windows did in a month. A nice alternative/s to gnome would be fluxbox (might needs some customizing) or xfce.  Can I make a wild guess and say you've tried Gnome on only one computer--yours, and then you're making an anecdotal claim that Gnome crashes a lot? I've used Ubuntu on several computers and have hung around this forum *a lot*, listening to others' experiences and problems. Believe me, Gnome is a lot more stable than KDE. Your experience was an abberation.

Regardless, Ubuntu has Ubuntu (Gnome), Kubuntu (KDE), and Xubuntu (XFCE), so you already have your choice.

---

### Post by jimcooncat on 2006-02-14
Not intending to troll, but why not try Gentoo? 

I loved it until I got tired of compiling and monkeying with the OS. Ubuntu with XFCE takes care of me now. Still I miss some things like the nice environment variable initialization and boot runlevels that Gentoo provides.

---

### Post by TrendyDark on 2006-02-14
[QUOTE=jimcooncat]Not intending to troll, but why not try Gentoo? 

I loved it until I got tired of compiling and monkeying with the OS. Ubuntu with XFCE takes care of me now. Still I miss some things like the nice environment variable initialization and boot runlevels that Gentoo provides.[/QUOTE]

I moved to Linux about 4 months ago and I'm still awaiting the day I understand what you just said, haha. 

aysiu, I agree for the most part, but I think you're wrong about Ubuntu. If any Linux distribution can make leaps and strides in the desktop field, it's going to be the one that is hands down the easiest and most popular. Ubuntu still isn't that at all, but with new versions and more time and even more attention brought to Ubuntu, I believe that it will change drastically for the better.

---

### Post by aysiu on 2006-02-14
[QUOTE=TrendyDark]
aysiu, I agree for the most part, but I think you're wrong about Ubuntu. If any Linux distribution can make leaps and strides in the desktop field, it's going to be the one that is hands down the easiest and most popular. Ubuntu still isn't that at all, but with new versions and more time and even more attention brought to Ubuntu, I believe that it will change drastically for the better.[/QUOTE] I specifically said a distribution *based* on Ubuntu would take off.

The reason Ubuntu itself won't take off is its lack of proprietary codecs--for philosophical reasons, not just cost.

A distro based on Ubuntu (which Mepis is going to be soon) can have whatever proprietary codecs it wants (MP3, NVidia, etc.) **out of the box**, and that's what most computer users want (I'm talking about my mom and dad and just about everyone I know here). Vanilla Ubuntu will never offer this.

---

### Post by xequence on 2006-02-14
> A distro based on Ubuntu (which Mepis is going to be soon) can have whatever proprietary codecs it wants (MP3, NVidia, etc.) out of the box, and that's what most computer users want (I'm talking about my mom and dad and just about everyone I know here). Vanilla Ubuntu will never offer this.

If there was a program as easy to use as nLite for ubuntu, id make my own install CD of ubuntu with all the codecs and stuff.

It would just be a special version of ubuntu, nothing different from the normal ubuntu except it has lots of stuff like codecs and video card drivers.

> 3) Ditch Gnome. 
This might only be a problem for me, but I dislike gnome, I don't like KDE either, both are very bloated. But gnome seems to crash a lot, there isn't a day when it doesn't crash at least once. It seems to be a problem with nautilus. I hate to say it but I think it crashes more in a week than windows did in a month. A nice alternative/s to gnome would be fluxbox (might needs some customizing) or xfce.

Gnome beats KDE in stability for me. Very much.

Does that mean I should tell another distro to ditch KDE? No!

---

### Post by wrtpeeps on 2006-02-14
installing from sources would take a lot longer anyway. Many people probably dont want to have to wait (like myself :P)

---

### Post by tageiru on 2006-02-14
[QUOTE=TheStig]Don't take this the wrong way, I'm not trying to be some ego maniac who thinks he knows everything. I'm very interested in other users ideas, tell me what problems you see with mine... I think within a few years Linux / Ubuntu will gather a lot of speed in the desktop market, a lot of that might be from people getting sick of Vista.


Ok here are the ideas:

1)One of the biggest problems I've found coming from windows is that the software install process can be a big pain on Linux... Now I love apt but it has a big problem it doesn't compile the packages from source. So if it's not in the repository because it's an updated version that just got released or its never been added, you have a problem.. Why couldn't there be an apt for source? So if I wanted to install the latest firefox release I could just ```
apt-get install http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-US/firefox-1.5.0.1.tar.gz
```

           Because I'm not a developer I don't know why this hasn't been done. But it seems like it would be possible to do.[/QUOTE]

This is not Windows! Ubuntu (and distributions like it) are centered around providing complete environments in which every part is tested with the rest of the environment. Windows works more like a platform where third parties maintain their own software independently of the operating system.

There are no guarantees that anything outside the repository will be easily installable and stable. With that said there is no reason why Ubuntu could not become more third party centric, but that takes support from organizations like Mozilla.

[QUOTE=TheStig]2)LDDB (Linux Device Database) The next problem is getting curtain hardware to work, tv tuners, laptop displays, wireless cards, new mice, etc. A lot of the problems can be solved by just editing a simple text file, but finding the info on what to edit can be a big pain. What if when you installed your new device a program would search a database of config files and download the correct one for your device?[/QUOTE]

This is actually working nicely with Ubuntu. The main problem is that not all hardware is availible for the developers. But if you look at the situation compared to warty the improvement is astounding, thanks to the hard work from the developers.

[QUOTE=TheStig]3) Ditch Gnome. 
This might only be a problem for me, but I dislike gnome, I don't like KDE either, both are very bloated. But gnome seems to crash a lot, there isn't a day when it doesn't crash at least once. It seems to be a problem with nautilus. I hate to say it but I think it crashes more in a week than windows did in a month. A nice alternative/s to gnome would be fluxbox (might needs some customizing) or xfce.[/QUOTE]

GNOME has not crashed on my computer for ages. Have you checked for hardware problems? Canonical would never ship GNOME as the desktop if they knew that it would crash that much.

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=aysiu]
3. Crossover Office works with every major Windows program.
[/QUOTE]

More like "WINE runs every major..." If the world comes to Linux it will be because its free (price wise).

And I'm glad you pointed this out. Its always been obvious to me that in the computer world unless you offer a migration path then masses ofpeople will never jump to your ship. AMD64 beat out Itanium for this reason.

If the goal is to take over the Window desktop market, there is no single program that is more important that WINE. Yet its does not get the development resources one would think such an important program should have (no major distro directly supports WINE in the ways they support Gnome/KDE/Xorg/etc.).

Why? Two reasons:

1. After years of trying it has been realized that "the holy grail" of having a way to run all (or even just the popular) Window programs perfectly is a pipe dream. Its just too hard to do. Thats why Crossover focuses on specific programs.

2. Many of those who back the Linux desktop could not care if it topples the MS monopoly with direct competition. They are willing to allow economic forces (aka one OS costs no money and another does in a world short of money) do the work.

---

### Post by TheStig on 2006-02-14
> endersshadow]1. Because of the fact that each program is packaged differently, you can't just simply install from a tarball.  That's where deb files come in, it's a uniformed way to install files.  At any rate, it's *usually* not any more than 6 commands:

1. wget [http://sourcepackage.tar.gz](http://sourcepackage.tar.gz)
2. tar xzf sourcepackage.tar.gz
3. cd sourcepackage/
4. ./configure
5. make
6. sudo checkinstall -D make install (or sudo make install if you prefer)

But what about all the dependency problems... That's my only complaint with installing from source.

> Can I make a wild guess and say you've tried Gnome on only one computer--yours, and then you're making an anecdotal claim that Gnome crashes a lot? I've used Ubuntu on several computers and have hung around this forum a lot, listening to others' experiences and problems. Believe me, Gnome is a lot more stable than KDE. Your experience was an abberation.

Regardless, Ubuntu has Ubuntu (Gnome), Kubuntu (KDE), and Xubuntu (XFCE), so you already have your choice.

I've used it on my desktop and laptop. Most of the problems have been on the desktop. I'll give it a try on a few other of my machines.


Thanks for all the replys, I'm enjoying reading them.

---

### Post by briancurtin on 2006-02-14
in order to get the majority of windows users to switch, there is going to have to be a very dumbed down distro. ubuntu is not it. linspire probably isnt even it.

i think a lot of people overlook just how many people there are in this world using windows. microsoft is a name people trust, and if linux is going to take over its going to need to print out money because people just dont believe that other things can make their computer work. id love to see a larger use of linux across the world, across all types of users, but its a ways a way and there is a lot of work to go.

---

### Post by Stormy Eyes on 2006-02-14
[QUOTE=TheStig]1)One of the biggest problems I've found coming from windows is that the software install process can be a big pain on Linux... Now I love apt but it has a big problem it doesn't compile the packages from source.[/quote]

If you absolutely have to have the latest and greatest stuff, and want a "package manager" that builds from source, then why aren't you using Gentoo, Source Mage, or even ditching Linux and using FreeBSD?

[QUOTE=TheStig]So if it's not in the repository because it's an updated version that just got released or its never been added, you have a problem.[/quote]

Actually, I don't have a problem. I have a choice: I can either wait, ask the developer to create a debian package, build it from source, or get the source, build a debian package, install it, and make it available to others.

[QUOTE=TheStig]2)LDDB (Linux Device Database) ... What if when you installed your new device a program would search a database of config files and download the correct one for your device?[/quote]

This is already being worked on, through projects like HAL and udev. If it doesn't quite work perfectly, there's always Google.

[QUOTE=TheStig]3) Ditch Gnome. ... I hate to say it but I think it crashes more in a week than windows did in a month. A nice alternative/s to gnome would be fluxbox (might needs some customizing) or xfce. [/quote]

I'm no fan of GNOME either, but I don't install a GNOME-centric distro and then complain about the use of GNOME; I knew what I was getting when I burned the ISO, after all. If you want to use XFCE, or Fluxbox, or just text-mode apps in a shell, then there's nothing stopping you. All you need is *sudo apt-get install xfce*. If you're a newbie and don't like GNOME, all you have to do is post yet another "GNOME sucks. What are the alternatives?" thread, and somebody will either answer, or link to one of the dozens of older threads dealing with alternative environments. (I recommend Openbox, by the way.)

---

### Post by Stormy Eyes on 2006-02-14
[QUOTE=TheStig]I've used it on my desktop and laptop. Most of the problems have been on the desktop. I'll give it a try on a few other of my machines.[/QUOTE]

If you can afford to, or have spares handy, try replacing your RAM. If you find Linux unstable, and aren't using experimental stuff, then you might have a hardware problem.

---

### Post by briancurtin on 2006-02-14
[QUOTE=TheStig]Why couldn't there be an apt for source?[/QUOTE]
check out Arch Linux and its pacman system, and everything that goes with it

---

