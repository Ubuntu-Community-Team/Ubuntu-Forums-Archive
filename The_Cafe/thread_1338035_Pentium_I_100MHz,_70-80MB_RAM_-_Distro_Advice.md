---
title: "Pentium I 100MHz, 70-80MB RAM - Distro Advice?"
date: 2009-11-26
forum: The Cafe
---

### Post by KingBongo on 2009-11-26
Hi. I have been thinking about bringing the old Pentium I 100MHz computer our family used ages ago back into life. It has around 70-80MB RAM, I don't remember exactly. 

I want to make sure that I end up with a system that is much better than the crappy Windows 95 that has been used on it before. I understand the options are limited, but that makes it even more fun and challenging. I am prepared to upgrade RAM if I can find some really cheap and it would be useful, but that's about it. So, what distro should I use? 

Requirements:
1. Hard drive installation, i.e. no Live CD
2. Graphical Interface

Preferred features:
1. As close to xBUNTU as possible, i.e. Debian based, similar Splash a.s.o.
2. As close to GNOME as possible
3. Modern Linux Kernel

I understand I will most likely not be able to fulfill the preferred features, but it would be nice. Anyway, I have been checking out wattOS ([http://www.planetwatt.com/](http://www.planetwatt.com/)), which looks really good (Debian based, OpenBox GUI) but I am not sure about the system requirements. Can OpenBox be customized to look more like Gnome? 

Can you help me with some suggestions?

---

### Post by kelvin spratt on 2009-11-26
Antix from mepis is very low on ram, as are most openbox/LXDE desktops. LXDE is very gnome orientated and very fast.

---

### Post by t0p on 2009-11-26
I think you'll have a great time tracking down RAM modules for that machine.

How big is its hard drive? 500 MB?  Less?

---

### Post by SR_ELPIRATA on 2009-11-26
```
<fun>Try GasoLinux, pour gently over machine and light a match :P</fun>
```

Some time ago I saw one distro named Haiku or something, they tried to make it look like the Amiga I think, very simple... I still have the pics, but dont remember the website. There were videos on youtube far as I remember.

ELP

---

### Post by Hallvor on 2009-11-26
> **kelvin spratt said:**
> Antix from mepis is very low on ram, as are most openbox/LXDE desktops. LXDE is very gnome orientated and very fast.

It also integrates very well with KDE. LXDE is a good choice.

---

### Post by KingBongo on 2009-11-26
Thank you guys! Keep it coming, :)

If I remember it correctly it has a huge 16GB HD i bought back in the 90's as an upgrade along with more memory. Of course, such a large HD could not be recognized as one partition (because of BIOS or FAT 16?) so I remember it had to be split into about a zillion smaller chunks, :p

I think I would be able to find some memory sticks on eBay or something. I would guess it is SDRAM. I am not sure how much memory the motherboard can handle though, but it has four slots.

Edit: I am now pretty sure it uses DIMM 168-pin SDRAM memory sticks. Not too old and it should still be possible to find them.

---

### Post by toupeiro on 2009-11-26
I have a copy of Redhat Linux 5.2 that ran on a 486 DX4-100Mhz system.  Not that you'd want to run a 2.0 kernel, but it would run...

---

### Post by jaxxstorm on 2009-11-26
[Spri]("http://www.sprilinux.com")

---

### Post by themusicalduck on 2009-11-26
Damn small linux or puppy linux might be good for it.

---

### Post by KingBongo on 2009-11-26
kelvin spratt:
On antiX site it is claimed that it does not rum on Pentium I.

SR_ELPIRATA:
Haiku is not Linux it seems.

toupeiro:
Thank you! Of course I would like to use a modern Linux Kernel if possible. I added that to "preferred features" in my original post.

jaxxstorm:
Spri looks great!

themusicalduck:
For some reason I don't like DSL or Puppy. But I will have a deeper look into them.

---

### Post by Wiebelhaus on 2009-11-26
Build your own and tailor it you needs and your hardware.

[How to install command line only.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

[Lubuntu:]("https://wiki.ubuntu.com/Lubuntu")

[Lubuntu Packages]("https://launchpad.net/~lubuntu-desktop/+archive/ppa")

[Lubuntu Meta installation packages.]("https://launchpad.net/~lubuntu-desktop/+archive/ppa/+packages")

---

### Post by wilee-nilee on 2009-11-26
If you decide to try puppy here are a list of some of the pupplets.
[http://puppylinux.org/wikka/Puplets?show_comments=1](http://puppylinux.org/wikka/Puplets?show_comments=1)

---

### Post by blueturtl on 2009-11-26
I hate to repeat myself time and time again, but: Debian.

A base Debian install requires very little RAM (text mode) or hard disk space. You get all the advantages of modern Linux (apt-get, huge repository of software, a 2.6 series kernel...).

The only thing that might make you think twice is that it's not a ready package. You will have to hand pick which packages or package collections to install after base install, and you will have to do this from the command line.

That said I believe you will be able to run (albeit slowly) X and some graphical apps. Honestly though, a Pentium 100 MHz is going to have a terrible time multitasking graphical applications. You're better off running pure command line mode, or command-line applications inside X.

Check [this post]("http://ubuntuforums.org/showthread.php?p=7947820#post7947820") I made earlier for some good applications to run on that system of yours.

---

### Post by KingBongo on 2009-11-26
Thank you guys! I think I really have to build something on my own. I tried installing a couple of these "Lightweight" distros in VirtualBox, and so far only wattOS could be installed on 64MB memory, :P It might be something wrong with my setting or VirtualBox itself though. I didn't try Puppy either, so I will give it a shot too. If that doesn't work, it is time to go hardcore!

---

### Post by &#32 Greg on 2009-11-26
Either DeLi or TinyCore might have a shot on that, but I'd probably agree that you're better off with Debian as a NetInstall. Of course if you really want to go hardcore, you can take a look at Crux and kmandla's blog...

---

### Post by anaconda on 2009-11-26
DSL Damn Small Linux woud fit to it, 

BUT

If it were mine I would propably install DOS to it, and loads of old DOS games, and a c64 emulator with even more games...


Wouldnt try to do anything productive or useful with a machine, which is that slow....

---

### Post by anaconda on 2009-11-26
OR 
I wuld install windows 98, and lots of dos games....

The system was designed for win 95 -98 , and thatis what it would propably run best on....

---

### Post by KingBongo on 2009-11-26
Thanks to you guys I now know where to start, :) By the way, VirtualBox does not install Lubuntu either, too demanding.

EDIT:
I must say that wattOS is looking better and better. It installs/works on as little as 80MB memory, looks stunning, can use a relatively high resolution and is blazing fast! It works on 64MB as well but not too good. Check it out! I will probably cheat a little here: Buy some RAM, install wattOS and then probably be happy. 

Does anybody know if you can simulate the speed of a 100MHz processor in VirtualBox?

---

### Post by cascade9 on 2009-11-26
> **t0p said:**
> I think you'll have a great time tracking down RAM modules for that machine.

How big is its hard drive? 500 MB?  Less?

LOL, EDO/fast page RAM is a right pain to find. I think I still have 128MB EDO EEC around here somewhere, I couldnt bring myself to throw it out. 

Probably 1GB-2GB hdd, from the RAM. Guessing. 

@ the OP- you really want to try with a p100? I find better machines than that by the side of the road.

---

### Post by snowpine on 2009-11-26
Check out Xubuntu; it is Ubuntu for older hardware. Good luck!

---

### Post by KingBongo on 2009-11-26
cascade9:
I am doing this just for fun! I recently got a decent Pentium 4 for free, so I know you can get a far better machine than a P100 for nothing, :)

I just looked at eBay, seems to be tons of cheap DIMMs over there.

snowpine:
Xubuntu really is too bloated.

---

### Post by koleoptero on 2009-11-26
You should wait a bit for kmandla to stumble upon this thread. ;)

In the meantime look at his blog for ideas [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/) He's the best at this as far as I know.

---

### Post by weresheep on 2009-11-26
I second blueturtl's advice.

I have a computer with a Pentium 133MHz running Debian stable. It is a headless server that I log into with SSH at home from my desktop or over the Internet while at work. It also acts as a file server for my home network sharing my data via NFS.

Bought new in 1995 it's been upgraded a bit over years and now has 256MiB RAM and a 1TB hard drive.

I have moved almost all of my computing tasks (email, chat, coding etc.) to command line alternatives over the last few years and now do almost everything on that machine. I wont be replacing it any time soon.

Good luck with your machine.

-weresheep

---

### Post by cascade9 on 2009-11-26
> **KingBongo said:**
> cascade9:
I am doing this just for fun! I recently got a decent Pentium 4 for free, so I know you can get a far better machine than a P100 for nothing, :)

I just looked at eBay, seems to be tons of cheap DIMMs over there.

snowpine:
Xubuntu really is to bloated.

Fair enough. I prefer p2s/p3s/super socket 7 AMDs to play with myself, but whatever floats your boat ;) 

+1 on 'xubuntu is bloated'.

---

### Post by witeshark17 on 2009-11-26
To the OP, please keep us posted on what you end up choosing!

---

### Post by Wiebelhaus on 2009-11-26
This one is crazy small (Ten Meg) [Tiny Core.]("http://distrowatch.com/?newsid=05792")

---

### Post by Cam42 on 2009-11-26
> **SR_ELPIRATA said:**
> ```
<fun>Try GasoLinux, pour gently over machine and light a match :P</fun>
```Some time ago I saw one distro named Haiku or something, they tried to make it look like the Amiga I think, very simple... I still have the pics, but dont remember the website. There were videos on youtube far as I remember.

ELP
FWIW, Haiku is meant to bring back the BeOS project.

---

### Post by KingBongo on 2009-11-27
Yes. I believe the Ubuntu Community should offer a REALLY lightweight distro, to cover all the bases. By that I mean be able to run on 64MB memory or less and on old hardware. Neither Xubuntu or Lubuntu seem to cut it on extremely low-end hardware. Take a look at wattOS and you know it can be done. I am impressed so far based on VirtualBox performance. I tried playing a flash video (Youtube) in full-screen mode on 800x600 resolution with 64MB memory and it worked! If you put wattOS on a modern computer, you will probably end up with something that is fast as hell. 

I already decided to try wattOS because it seems to fulfill almost all of my criteria. Let's see how it works in the real world though.

---

### Post by snowpine on 2009-11-27
> **KingBongo said:**
> Yes. I believe the Ubuntu Community should offer a REALLY lightweight distro, to cover all the bases. By that I mean be able to run on 64MB memory or less and on old hardware.

The first version of Ubuntu came out in 2004; why should Canonical waste their time developing for hardware that predates the distro itself? 

Slackware, Debian, Red Hat, etc. have been around forever and already have old hardware well supported. Then there's Puppy, DSL, SliTaz, etc. for an old-hardware-specific spin. I am glad Canonical has a strong vision of Ubuntu's niche and stays focused.

---

### Post by cascade9 on 2009-11-27
> **snowpine said:**
> The first version of Ubuntu came out in 2004; why should Canonical waste their time developing for hardware that predates the distro itself? 

Because there is a lot of old hardware out there. A huge amount. If I was doing a ubuntu project to run on older systems, I dont think I would go as low as 64MB, but 120MB+ (128MB with 8MB shared for video) would be a good idea IMO. 

If ubuntu was only made to run on post-2004 computers, there would be far less people in these forums. Look at how many P3/early to mid P4/Athlon/Athlon XP/Athlon 64s there are around here. All pre-2004. 

Its an 'in'. I think that a lot of people might try out ubuntu if there was a more minimal version made for old hardware. Once you hae 'joe average' installing an OS on his old PC, if it runs well, hopefully the idea of 'I can make this old banger work, how good would it be on my new system?" will magically appear. :D  

BTW, AFAIK, a lot of older hardware support is actually fromthe kernel, its not like ubuntu will have to do a huge amount of work. All they need to do is make a slightly different version of the alternate installer. 
Yes, I know that the alternate installer exists, and so would the majority of people on this forum. Thats a bit different to 'average' computer users, who would have to dig to find out that info. A nice version made for older hadware would be far easier for newbies to find. 

Besides that, it might have the effect of stopping people sprouting 'xubuntu, its made for older hadware'......when its not.

---

### Post by Wiebelhaus on 2009-11-27
> **KingBongo said:**
> Yes. I believe the Ubuntu Community should offer a REALLY lightweight distro, to cover all the bases. By that I mean be able to run on 64MB memory or less and on old hardware. Neither Xubuntu or Lubuntu seem to cut it on extremely low-end hardware. Take a look at wattOS and you know it can be done. I am impressed so far based on VirtualBox performance. I tried playing a flash video (Youtube) in full-screen mode on 800x600 resolution with 64MB memory and it worked! If you put wattOS on a modern computer, you will probably end up with something that is fast as hell. 

I already decided to try wattOS because it seems to fulfill almost all of my criteria. Let's see how it works in the real world though.

I linked how to in post #11.

---

### Post by snowpine on 2009-11-27
> **cascade9 said:**
> Because there is a lot of old hardware out there. A huge amount. If I was doing a ubuntu project to run on older systems, I dont think I would go as low as 64MB, but 120MB+ (128MB with 8MB shared for video) would be a good idea IMO. 

CrunchBang linux is basically minimal Ubuntu plus Openbox (a really lightweight windows manager). It runs *terrible* on 64-128mb. 

I do not see how any Ubuntu derivative could possibly run well with less than 256mb in my experience... at least not for the everyday tasks we all take for granted (YouTube, Facebook, OpenOffice, etc.) Even SliTaz, one of the lightest-weight distros in existence, recommends 256mb minimum.

Obviously if your needs are very modest (a CLI-only server, you never visit Flash websites, etc.) it is a different story.

---

### Post by KingBongo on 2009-11-27
Wiebelhaus:
I know, I know. But I try to behave like most people whenever I can; Plug in some distro, answer a few questions and off you go. The complicated stuff should the good guys take care of beforehand. And xUBUNTU is exactly that easy by default. Any distro that is not like that will never become widely accepted. 

I can be much geekier than the scenario above, but I don't want to if I don't have to. I spend far to much time in CLI and modifying files already. Computers are a great interest for me, but Snowmobiles are still #1, ;)

---

### Post by -grubby on 2009-11-27
> **snowpine said:**
> Check out Xubuntu; it is Ubuntu for older hardware. Good luck!

Xubuntu won't run on that very well.

---

### Post by Pogeymanz on 2009-11-27
Damn Small may be your only reasonable bet. The thing is, they use the 2.4 kernel because it has more support for old hardware. Plus, I'm guessing it is probably slimmer.

---

### Post by MaxIBoy on 2009-11-27
PuppyLinux could be usable on that machine, otherwise try VectorLinux Light Edition: [http://vectorlinux.com/products](http://vectorlinux.com/products)


> **SR_ELPIRATA said:**
> ```
<fun>Try GasoLinux, pour gently over machine and light a match :P</fun>
```Some time ago I saw one distro named Haiku or something, they tried to make it look like the Amiga I think, very simple... I still have the pics, but dont remember the website. There were videos on youtube far as I remember.

ELP
Haiku is its own OS, intended to be a compelling replacement for and upgrade of BeOS. It is compatible with BeOS but Linux software doesn't work on it. It's not a Linux distro.

---

### Post by K.Mandla on 2009-11-27
From my own experiences with 100Mhz and lower machines, I would suggest as little graphical as you can tolerate -- stick with a tiling window manager (Musca is my favorite) and terminal-based applications. Once you get into toolkits and graphical elements, everything slows to a crawl. I can run X in 1Mb on a 100Mhz machine with only 16Mb to work with, but if I add GTK1.2, it's like walking with cement shoes.

I would avoid Ubuntu like the plague (especially Xubuntu). Try Puppy, DSL or Slitaz (I've put Slitaz on that same 100Mhz-16Mb machine and it runs ... hideously, but it runs) or do the best thing and build it all from scratch. Crux is good for that, or Gentoo. Build it on another machine and transplant the drive into your host.

Have fun! ;)

---

### Post by KingBongo on 2010-01-05
Hi again! I am now member of both the wattOS and the Puppy forum, :) wattOS definitely does not work on the P100, so I quickly started playing around with Puppy and derivatives. Puppy really is nice for low-end hardware! I have it working, but not fast enough to my liking despite the fact that I upgraded the processor to 200MHz. So now I have a P200, :) Some of the Puppy releases also seem unfinished (in my opinion), because some of the older ones that should work right away don't. 

A little more memory maybe would solve my issues because I believe 73MB is a serious bottle-neck, but I decided to try some other options too. A few of you guys mentioned a bare-bones Debian install to begin with. I am also interested in Arch. I would like to try those. The problem is that the P1 has the i586 architecture, which it is hard to find modern distros for. It only makes it more interesting though. Those running Pentium Pro's, Pentium II's and newer processors are cheating! :) 

I was able to find Debian and Arch compilations for i586, but they seem to be unfinished and not regularly maintained. Any ideas?

---

### Post by Exodist on 2010-01-05
> **toupeiro said:**
> I have a copy of Redhat Linux 5.2 that ran on a 486 DX4-100Mhz system.  Not that you'd want to run a 2.0 kernel, but it would run...
LOL I think I have my 5.2 CDs around here somewhere.. hehe
I have suse 7.1 also, it porb only work as a CLI install. 
Also got a old as hell Mandrake around here as well. They used to run on my K6-350 with 192MB RAM. 
But I dont think he is going to get X anything to run on that amount of RAM.
CLI with FB support should be possible.

---

### Post by The Real Dave on 2010-01-05
PC-100 SDRAM? I've got a bucket of 64Mb sticks of that, not too difficult to find :) Try Damn Small Linux or Puppy, or you could try a CLI install of Ubuntu and build a text based system on it, or even Openbox or LXDE. Keep it as light as possible :)

---

### Post by forrestcupp on 2010-01-05
If you look at things objectively, anything you can get to run on that machine will be at least as crappy as Win95 if not crappier.  There's a reason Win95 was so crappy.  It's because it had to run on crappy machines. ;)

---

### Post by KingBongo on 2010-01-12
forrestcupp:
I don't agree. Windows 95 is the biggest POS available, :P In fact, w95 is the sole reason why I left Windows for Mac OS back then, and now additionally for Linux. In terms of crappiness w95 cannot be beaten, :)

I am now going to play around with Debian base (Network Install) on this machine, without tons of apps or any eye-candy. I have a few questions to the smart guys,

A. When I have to choose which software groups to install, I know I have to uncheck "Desktop environment", but what about "Standard system"? What comes with that selection? Is it necessary?

B. What are the differences between a minimal Debian installation and a minimal Ubuntu installation? Is the difference mainly that Ubuntu uses newer (more unstable) packages or what? Please explain.

C. Is there a way to kick-start the Debian CD? The computer doesn't want to boot from a CD (although it should). Smart Boot Manager on a floppy doesn't work either. Any other options?

EDIT: I have now been able to kick-start the CD with the Boot Manager PLoP.

---

### Post by madhi19 on 2010-01-12
Seriously anything bellow Pentium 3 is probably a waste of time. You might be able to use the old case for a new rig you want to build or a case mod. I use an old computer case as a tool box for my car! I seen folks who build a mini bar with an old case too!

---

### Post by KingBongo on 2010-01-12
madhi19:
I am playing around with this just for fun. Fun is never a waste of time, :P

---

### Post by caravel on 2010-01-12
Personally I would go with a minimal install of Debian stable and IceWM on that machine.

---

### Post by KingBongo on 2010-01-13
Man. How can Debian take up SO much HD space? I installed the following packages:

1. Minimal Network Install (nothing selected from the Package Groups list)
2. Xorg
3. jwm
4. xdm
5. Synaptic
6. Memtest 86+
7. Hardinfo
8. Opera 10.10

All are lightweight low-space packages, except for Opera and Synaptic. 1 TB of Hardisk space is gone? Is that even possible? Can somebody tell me how to remove packages to make it really bare-bones in an easy way? I found this project (seems great), but it is not active at the moment: [http://debian.cante.net/stem/](http://debian.cante.net/stem/)

PS. I am really impressed by lightweight distros such as Puppy! HOW do they pack all that stuff in such a tiny space???

---

### Post by snowpine on 2010-01-13
> **KingBongo said:**
> Man. How can Debian take up SO much HD space? I installed the following packages:

1. Minimal Network Install (nothing selected from the Package Groups list)
2. Xorg
3. jwm
4. xdm
5. Synaptic
6. Memtest 86+
7. Hardinfo
8. Opera 10.10

All are lightweight low-space packages, except for Opera and Synaptic. 1 TB of Hardisk space is gone? Is that even possible? 

Impossible... possibly a partitioning error? A minimal Debian install should only take about 1 GB.

---

### Post by KingBongo on 2010-01-13
snowpine:
Thank you! I only have a 1.2GB disk so 1GB with almost nothing installed is a little bit too hefty I think. I need to use a bigger disk, but my computer seem to have problems booting from anything bigger than 1.2GB.

---

### Post by madhi19 on 2010-01-17
> **KingBongo said:**
> madhi19:
I am playing around with this just for fun. Fun is never a waste of time, :P

Sorry about that you could try Damn Small Linux or Puppy!

---

### Post by CJ Master on 2010-01-17
> **KingBongo said:**
> forrestcupp:
I don't agree. Windows 95 is the biggest POS available, :P In fact, w95 is the sole reason why I left Windows for Mac OS back then, and now additionally for Linux. In terms of crappiness w95 cannot be beaten, :)

Windows 3.1...?

---

### Post by CharmyBee on 2010-01-17
Puppy 4.20 should work. 80MB of RAM is enough to run a lot of 'light' distros well, you could also run SliTaz.

100MHz P1? Socket 7 I assume, you could put a K6-2 400MHz processor in that and get Knoppix going.

To make the most use out of an old processor like that, you really can't beat Windows. Please leave your flames at the door. There's enough RAM to boot into Windows 2000 without swap heck.

---

### Post by Dr. C on 2010-01-18
> **CharmyBee said:**
> Puppy 4.20 should work. 80MB of RAM is enough to run a lot of 'light' distros well, you could also run SliTaz.

100MHz P1? Socket 7 I assume, you could put a K6-2 400MHz processor in that and get Knoppix going.

To make the most use out of an old processor like that, you really can't beat Windows. Please leave your flames at the door. There's enough RAM to boot into Windows 2000 without swap heck.

If you wish to run Windows on such a system Windows for Workgroups 3.11 / MS DOS 6.22 or Windows 3.1 / MS DOS 6.22 will run really fast. Windows 98 SE (passable). The other option is Windows NT 3.51 (decent) or Windows NT 4 (passable). Windows 2000 will run but so slow as to be utterly useless.

---

### Post by CharmyBee on 2010-01-18
> **FineE said:**
> If you wish to run Windows on such a system Windows for Workgroups 3.11 / MS DOS 6.22 or Windows 3.1 / MS DOS 6.22 will run really fast. Windows 98 SE (passable). The other option is Windows NT 3.51 (decent) or Windows NT 4 (passable). Windows 2000 will run but so slow as to be utterly useless.

You're confusing 100MHz with 80MB with 33MHz with 8mb. Windows 2000 will work fine, I have first hand experience with very old computers like the OP has. 80MB will make Win2k fly, even 64MB is enough for it.

I wouldn't recommend early NT or Windows 3.X at all!

I made a thread with a similar scenario. 
[http://ubuntuforums.org/showthread.php?t=1159563](http://ubuntuforums.org/showthread.php?t=1159563)

---

### Post by koenn on 2010-01-18
> **KingBongo said:**
>  I am also interested in Arch. I would like to try those. The problem is that the P1 has the i586 architecture, which it is hard to find modern distros for. It only makes it more interesting though. Those running Pentium Pro's, Pentium II's and newer processors are cheating! :) 

I was able to find Debian and Arch compilations for i586, but they seem to be unfinished and not regularly maintained. Any ideas?

look for the i486 kernels

---

### Post by GS2 on 2010-01-18
If you only want to use the laptop at home, and have a desktop or more modern laptop within your LAN, then you could run the old laptop as a client,with the X windows server running on the more powerful machine. This will reduce a lot of the workload.

Obviously I wouldn't recommend this over the internet for obvious reasons - but within you own LAN it should be fine - I would setup a SSH tunnel between the two machines.

Aside from that I have run FreeBSD on a Pentium 166 laptop, using XFCE without any problems - so if you fancy a dabble in something different you'll be surprised how lightweight on resources the BSD's are ;)

---

### Post by koenn on 2010-01-18
> **KingBongo said:**
> snowpine:
Thank you! I only have a 1.2GB disk so 1GB with almost nothing installed is a little bit too hefty I think. I need to use a bigger disk, but my computer seem to have problems booting from anything bigger than 1.2GB.
What you list there should add up to something like 800 MB. You probably need to delete the downloaded debs (apt-get clean; apt-get auto-clean ).

Even if you didn't select any additiopnal "tasks" during install, you probably had the installer install a bunch of software that is considered 'standard' but that you have no need for (a compiler ? a loa of network troubleshoot tools ...). You might consider hunting down some of those and remove them, or uninstall the packages they came in (but check that you don't remove anything essential)

You can probably also save a few MB by deleting documentation that you're never going to read. 


That said, those  800 MB - 1 GB  - 1.2 GB drives were always to small for anything except win3x - I remember installing Win95 and win 98 on those, and you'd always have only a few 100 MB disk space left for data.

---

### Post by Ibidem on 2010-05-15
I had a 1999 Thinkpad with 64 mb of ram and a PIII at ~500 mhz, running Dapper; IceWM ran fairly fast, along  with Dillo (bad rendering), Abiword, etc.  (Now it won't boot)

But TinyCore Linux is pretty fast on newer hardware, and minimum requirements are listed as:
48 MB RAM (36 for microcore)
486DX
(~12 MB of disk space minimum, though 100+ MB is better, and a bit of time to manually install--it prefers to run "live")

If you have 70 MB of ram, that leaves 22 MB for playing around.
Tinycore is basically a minimal install that includes Xvesa, a package manager, wbar, and a few other things; if you want to do anything, you add software.
I'd suggest trying Opera for browser, though Chimera is the lightest and Dillo is available--Opera does more.
xfe is my suggestion for a file manager (comes with xfw/xfwrite as a text editor and xfi/xfimage as image viewer)

---

### Post by mmix on 2010-05-15
[http://www.delilinux.de/](http://www.delilinux.de/)

and try other oses
freedos, menuetos.

---

