---
title: "Whats the best BSD for someone new to BSD"
date: 2006-01-13
forum: The Cafe
---

### Post by JimmyJazz on 2006-01-13
I was thinking of trying BSD on one of my old computers but I'm not really sure which one I should try.  I know there was a thread like this before but I can't  seem to find it.
I think what I want to see most of all is the speed and I don't want a distro that takes more than 1 CD to install.

---

### Post by DigitalDuality on 2006-01-13
Well that knocks out FreeBSD, not sure how many discs Net or Open are.  I think, but don't quote me on it, that DragonFly is one disc.  Haven't heard many reviews on it though.

---

### Post by tseliot on 2006-01-13
FreeBSD 6.0 (1CD). It's fast but you need to read the documentation to configure the xserver (i.e. create your xorg.conf) (and maybe recompile the kernel) and do things which are peculiar to BSD.

---

### Post by Omnios on 2006-01-13
I have PC-BSD which is based on free BSD on a old P2 because linux will not install on it properly. Install was painless and hardware detect was also good.

---

### Post by curuxz on 2006-01-13
*waits for bsd freak to come along and post something*.......ok he is not about. erm i asked the same kinda thing a few days ago. I think you should get freebsd (the one im trying at the mo) its only 2 disks, which aint that bad :)

---

### Post by Quake on 2006-01-13
Maybe you can try [FreeSBIE]("http://www.freesbie.org"): A fully configured FreeBSD with a working Xserver LiveCD

[http://www.freesbie.org](http://www.freesbie.org)

---

### Post by JimmyJazz on 2006-01-13
I'm gonna try out that liveCD on my laptop, then probally move onto FreeBSD

---

### Post by byen on 2006-01-13
Great! Someone asked a question that has been tinkering in my mind too..
It looks as if the most popular among the BSD's is FreeBSD. I dual boot with windows and Ubuntu and was thinking about another distro...but I guess BSD would be a better option.
I have one question though.. do I really have to recompile my kernel and xorg?  (*shivers*)

---

### Post by Mr_Grieves on 2006-01-13
I like FreeBSD because there is alot of applications for it. Aswell it's secure and stable. At work we had a FreeBSD installation that ran without any of downtime/reboot for 7 years :D
And then it ran bind/sendmail fulltime.

But.. when we powered down the server to move it.. it never came up again, hahaha.  We actually had an "officiall burrial" for it.. it's was so sad.

---

### Post by tseliot on 2006-01-13
[QUOTE=byen]Great! Someone asked a question that has been tinkering in my mind too..
It looks as if the most popular among the BSD's is FreeBSD. I dual boot with windows and Ubuntu and was thinking about another distro...but I guess BSD would be a better option.
I have one question though.. do I really have to recompile my kernel and xorg?  (*shivers*)[/QUOTE]
I had to recompile the kernel in order to add the support for the sound card of my portable computer.
It was extremely easy (there is the documentation), easier than in Linux.

The xorg.conf can be created with a command (you don't have to write all its content). You have to enable mousescroll and set the resolution (and refresh) you need.

Then you have to select the session manager (xdm, gdm or kdm) and make the Desktop Environment selectable form the session manager.

It's all written in the manual.

It's easier and faster than Gentoo (but it has much less Linux applications)

---

### Post by JimmyJazz on 2006-01-13
I just tried out that FreeBSD live cd suggested above, I must say I am quite impressed there is defintly some speed here.

---

### Post by AMD64_N_Linux on 2006-01-13
I concure with FreeBSD, but have not used BSD in the last 4 or 5 years. I have been testing so many different versions of linux, that I had no extra time to keep working with BSD.

One thing is though, the naming conventions used to be totally different.

hda,hdb (1st and 2nd harddrive) is sda, sdb.

Unless they have changed this, be sure to keep this in mind going in.

---

### Post by majikstreet on 2006-01-13
I'd like to try it on my "server" which will be getting repurposed soon as a test bed.. only problem is the two hd's combined it only has ~7gb... so yeah..

I may put dapper on it and use like openbox over freenx or something.....

FreeBSD has always been interesting to me, as have many distro's both linux and bsd... I wish I had more computers!

---

### Post by Freddy on 2006-01-14
If you want to try out BSD for real, I would recommend.

PC-BSD, which is freeBSD with a anaconda installer and the .pbi installing package system. .pbi's is a one click install package system. There aren't that many .pbi's done yet but they will come and you still have the wonderfull port system for freeBSD.

DesktopBSD, is another BSD system based on freeBSD with a nice graphical installer, the team behind DesktopBSD has made a fine effort to make the ports easy to handle, through a graphical program.

Both of this *BSDs use by default KDE, but with DesktopBSD you could install Gnome through ports but you would still need a hole bunch of kde libs for the portsinstaller app.   /// Freddan

---

### Post by ippiraman on 2006-01-14
I'd go for FreeBSD since a lot of questions can be answered by it's handbook. If you want an easy FreeBSD install, you can choose between FreeSBIE, PC-BSD, or DesktopBSD (they're all in one disc). 

A normal FreeBSD 6.0 install doesn't have a DM by default, you'll need to install it manually either through ports or the second ISO.

Currently I'm dual-booting FreeBSD and Ubuntu without any problems.

HTH

---

### Post by MetalMusicAddict on 2006-06-15
PC-BSD and Desktop-BSD seem to be KDE based. Is there a Gnome based distro? Is Free-BSD too big of a pain? Id like to try something Gnome based with good out-of-the-box hardware support and as up-to-date as possiable. Im leaning towards Desktop-BSD because of "ports".

---

### Post by vayu on 2006-06-16
[QUOTE=MetalMusicAddict]PC-BSD and Desktop-BSD seem to be KDE based. Is there a Gnome based distro? Is Free-BSD too big of a pain? Id like to try something Gnome based with good out-of-the-box hardware support and as up-to-date as possiable. Im leaning towards Desktop-BSD because of "ports".[/QUOTE]

I vote FreeBSD.  You can install Gnome and it has ports.  You can install precompiled packages or you can compile your own.  You install just what you need, no kitchen sinks.  New releases for most major applications are available reasonably quickly.  Ubuntu was my first foray into open source OSs and it together with its forums gave me enough understanding to work with FreeBSD.  FreeBSD has a decent userbase.  The online handbook is well written and complete.  It lacks the prolific forum of Ubuntu but the mailing list is quite active.  You won't get the handholding you get with Ubuntu but you get what you need.

---

### Post by fuscia on 2006-06-16
i've only tried a live version of netbsd on an old POS. it was fine, except for wireless (big surprise).

---

### Post by RAV TUX on 2006-06-16
[quote=JimmyJazz]I was thinking of trying BSD on one of my old computers but I'm not really sure which one I should try.  I know there was a thread like this before but I can't  seem to find it.
I think what I want to see most of all is the speed and I don't want a distro that takes more than 1 CD to install.[/quote]

After trying out all the BSD's I found PC-BSD to be the best, 1 disk needed, fastest install, and fastest OS of all the BSD's. Save yourself the hassle: PC-BSD should be your only BSD option.


PC-BSD
[http://www.pcbsd.org/](http://www.pcbsd.org/)

---

### Post by patrick295767 on 2006-06-17
[QUOTE=Omnios]I have PC-BSD which is based on free BSD on a old P2 because linux will not install on it properly. Install was painless and hardware detect was also good.[/QUOTE]
 
Sounds interesting for my old pc
I tried slackware but my hardware still not recognised (ubuntu do everythg perfectly and well)
  
What's nice with ur bsd on ur old P2 ? What stuffs u can do with it ?  What about the office applications ? 
(screenshots )
  
I can try it too on my old pc shit ... :-) if faster than linux'es (bsd faster than linux ?)

Patrick

  =====================
I found this on the net : :-)  lol

  
***** IMAGE REMOVED *****

---

### Post by MetalMusicAddict on 2006-06-17
I tried Desktop-BSD and it seemed quite snappy. I think Im gonna try Free because you pick you DE. Right? Does Free use xorg not xfree86?

---

### Post by vayu on 2006-06-18
[QUOTE=MetalMusicAddict]I tried Desktop-BSD and it seemed quite snappy. I think Im gonna try Free because you pick you DE. Right? Does Free use xorg not xfree86?[/QUOTE]

Yes, with FreeBSD you choose your DE and you use Xorg.

---

### Post by MetalMusicAddict on 2006-06-18
[QUOTE=vayu]Yes, with FreeBSD you choose your DE and you use Xorg.[/QUOTE]
Nice. I wonder if it will play nice with my broadcom wireless card. :rolleyes: How is the hardward detection otherwise in FreeBSD? Also does "ports" download packages, compile them *then* install them? Is that how it works?

---

### Post by RAV TUX on 2006-06-18
[quote=JimmyJazz]I was thinking of trying BSD on one of my old computers but I'm not really sure which one I should try. I know there was a thread like this before but I can't seem to find it.
I think what I want to see most of all is the speed and I don't want a distro that takes more than 1 CD to install.[/quote] 


Just wondering which BSD's the original poster has tried and what has worked or not worked?

which one of the following BSD's have you tried? Which do you like the best?

[FreeBSD]("http://www.freebsd.org/")

[OpenBSD]("http://www.openbsd.org/")

[NetBSD]("http://www.netbsd.org/")

[386bsd]("http://www.386bsd.org/")

[DragonFly BSD]("http://www.dragonflybsd.org/")

[PC-BSD ]("http://www.pcbsd.org/")

[DesktopBSD]("http://desktopbsd.net/")

[BSDeviant]("http://en.wikipedia.org/wiki/BSDeviant")

[ClosedBSD]("http://en.wikipedia.org/wiki/ClosedBSD")

[FreeSBIE]("http://www.freesbie.org/")

[Frenzy]("http://frenzy.org.ua/en/")

[PicoBSD]("http://people.freebsd.org/%7Epicobsd/picobsd.html")

[Anonym.OS]("http://en.wikipedia.org/wiki/Anonym.OS")

[MirOS BSD]("http://en.wikipedia.org/wiki/MirOS_BSD")

[ekkoBSD]("http://en.wikipedia.org/wiki/EkkoBSD")

[MicroBSD]("http://www.microbsd.net/")

[OliveBSD]("http://g.paderni.free.fr/olivebsd/")

[Gentoo/FreeBSD ]("http://www.gentoo.org/proj/en/gentoo-alt/bsd/fbsd/index.xml")

[Gentoo OpenBSD]("http://en.wikipedia.org/wiki/Gentoo/ALT")

[Gentoo NetBSD]("http://en.wikipedia.org/wiki/Gentoo/ALT")

Gentoo DragonflyBSD

[Debian GNU/kFreeBSD]("http://www.debian.org/ports/kfreebsd-gnu")

[Debian GNU/kNetBSD]("http://www.debian.org/ports/netbsd/")

[BSD/OS]("http://en.wikipedia.org/wiki/BSD/OS") 

[SunOS]("http://en.wikipedia.org/wiki/SunOS")

[Ultrix]("http://en.wikipedia.org/wiki/Ultrix")

[Tru64 UNIX]("http://en.wikipedia.org/wiki/Tru64_UNIX")

[Mac OS X]("http://en.wikipedia.org/wiki/Mac_OS_X")

[FireflyBSD]("http://en.wikipedia.org/wiki/FireflyBSD")

______________________________

(EDIT: on most llinks above I directed the link to the BSD project homepage, if not I directed the link to the Wikipedia page for the BSD OS)

---

### Post by vayu on 2006-06-20
[QUOTE=MetalMusicAddict]Nice. I wonder if it will play nice with my broadcom wireless card. :rolleyes: How is the hardward detection otherwise in FreeBSD? Also does "ports" download packages, compile them *then* install them? Is that how it works?[/QUOTE]

Hardware detection was pretty good for the two computers I have it on. Look/search around on the FreeBSD site and also the mailing list archives for an idea about hardware compatibility and driver availability.
[http://www.freebsd.org/]("http://www.freebsd.org/")

There are two ways to install software.  Ports is the compile it yourself way and for the most part is the preferred way.  

The ports system is set up to be easy and works well.  There is a directory 
/usr/ports that has directories for all the supported apps.  You go to the directory of the program you want and type "make install clean".  It will compile the program and download and compile all its dependencies.  I'm pretty noob and have not had a problem.  I've compiled X, KDE, a kazillion K apps, the latest nVidia drivers, Xine, Firefox, and more without a single problem.  The ports maintainers are on it.  I'm running versions of most things as recent as on Dapper.

Packages are the pre-compiled binaries.  I installed my first system using this way.  The CDs come with the versions that were current at the time of the release of your CD.  You can install from there using the sysinstall program or you can use pkg_add to download and install the latest pre-compiled binary of a given program.  Especially usefull for things like Gnome, KDE, OO, Firefox, etc...  

For my first system I installed everything off the CD and was up and running pretty quickly not much fuss.  I had to add some lines in my /etc/rc.conf file and /boot/loader and I can't remember what else to get a few things like my sound card working.  Most everything you need to know is in the well written online "Handbook".  The rest I found with google.  The main things I had to figure out were my sound card, getting Flash to work and getting my DVD drive accessable in KDE.  In a way it was a little trickier than Hoary and Breezy were for me, but actually not.  I had to tinker quite a bit to get Ubuntu to work.

Once I knew my way around a bit, for my second computer I did it a little differently.  From the CD I had older versions of Xorg, KDE and Firefox (not that old).  I wanted the latested versions without having to upgrade them.  What I did was a minimal install, just the kernel and userland.  Then I recompiled the kernel (real easy and smooth, nothing like Linux).  Then I installed the latest ports tree and then I installed the apps I wanted one by one.  Now I have a system that is clean and pure and no bloat.  I love it.

FreeBSD offers a lot of flexibility.  It is set up to compile your apps but it's set up well, it's easy.  You can also just install off the CD and be up and running in one shot.  Overall, it's not as easy as Ubuntu, there is nothing like Automatix, but it's not that bad and you don't get all kinds of stuff you don't want/need.

That said I still use Breezy on my laptop because it is so easy and there's nothing like apt-get.  I also have a partition on one of my desktop machines that I use Dapper and XGL on.  I read an account of someone getting XGL on FreeBSD, and it didn't look like something I'm ready to tackle yet.

---

### Post by MetalMusicAddict on 2006-06-21
Thanx vayu that was very helpful.

Basically I like to try different distros to do speed and ease-of-use tests. So far most binary distros feel the same. A friend and I tackled Gentoo but for the what seemed to be minimal speed increase it wasnt worth the hassle. I wanted to try a BSD because they have a reputation for stability. Ill probally go the ports way for everything just to see whats involved.

I gotta get some free time though. Between my kids and moving 300 miles away Ive been busy.
Maybe Ill go with BSD for my server instead of a Dapper-server. ;)

---

### Post by forrestcupp on 2006-06-21
I wish a linux distro that is more user friendly than Gentoo had a thing similar to ports.  It seems like it would be a lot better to compile everything, but it's too much of a pain to do it manually when I can just get everything by clicking on it in Synaptic.

---

### Post by hizaguchi on 2006-06-21
I like Free and PC BSD.

PC-BSD is braindead easy to install.  It's the best installer I've ever seen.  It's got a graphical tool for everything... even switching kernels, and you can easily get a working system with KDE without having a clue what you're doing.  It also (theoretically) supports the FreeBSD ports system, but I got a bunch of dependency problems when I tried to portupgrade -a.  That's what lead me to FreeBSD.

Installing FreeBSD is a little more involved, but really not that bad if you glance at the handbook first.  It detected all of my hardware that it was supposed to (you do your own soundcard later), and had me up and going without any trouble.  Xorg was easy to configure with the xorgconf tool as long as you know about your monitor (or pick the safest settings).  Then I just set up all of the sound modules to load at boot and, on the rare occasion that I actually reboot, I just let it pick the one that works.

DesktopBSD is very nice too, but I didn't like the installer because it really doesn't give you much choice in your partitioning or settings.  It's also based on FreeBSD 5.5, so if you're obsessed with being up to date (like me) then be aware of the potential difficulty of upgrading to a new major version.  But the good news is that it works much better with the ports system than PC-BSD did for me, and it has a very nice, Synaptic-like graphical tool for managing your software collection.  Of course, that's available for FreeBSD 6.1 now as "desktopbsd-tools", along with the network and drive mounting utilities.

Anyhow, I like PC-BSD for it's automation, but I'm using FreeBSD because of the ports problem and because it, for some reason, lets my laptop sleep without freezing up Xorg.

---

