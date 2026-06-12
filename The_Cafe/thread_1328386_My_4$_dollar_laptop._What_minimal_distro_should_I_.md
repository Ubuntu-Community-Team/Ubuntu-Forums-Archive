---
title: "My 4$ dollar laptop. What minimal distro should I use?"
date: 2009-11-16
forum: The Cafe
---

### Post by wulfgang on 2009-11-16
I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)

---

### Post by youbuntu on 2009-11-16
> **wulfgang said:**
> I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)

You could try a floppy distro - I cannot see any X server running too well on that spec, but I am sure one COULD, albeit terribly.

Try here:

[http://www.mail-archive.com/linux-users@it.canterbury.ac.nz/msg04481.html](http://www.mail-archive.com/linux-users@it.canterbury.ac.nz/msg04481.html)

OR

[http://www.linuxquestions.org/questions/linux-general-1/tiny-linux-distros-for-a-133mhz-laptop-135975/](http://www.linuxquestions.org/questions/linux-general-1/tiny-linux-distros-for-a-133mhz-laptop-135975/)

---

### Post by NormanFLinux on 2009-11-16
It could run LXDE. It runs fine on my netbook. You want to keep it low resource usage.

---

### Post by Bunnybugs on 2009-11-16
Puppy is the smallest I know, but puppy settles on the RAM memory, so I really don't know...

Have you checked out the early editions of Ubuntu???

I've installed one of the first Releases on a 64Mb machine a couple of years ago... and that was really fast...

Used about 10MB ram:P

---

### Post by MasterNetra on 2009-11-16
Idk if any GUI based distro can run. I don't think DSL or Puppy can handle something at 16mb of ram at least a GUI version for it is out of the question. DSL needs at least (better if more) 64MB of ram for graphical anyway could get by on the non-gui part of it which needs at least 16mb though they recommend 24mb of ram. And puppy around 128mb for versions after 1.0.2. and 64mb for before. Either way puppy not gonna work for ya.

[http://puppylinux.org/wikka/MinReq](http://puppylinux.org/wikka/MinReq)

[http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements](http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements)

---

### Post by emigrant on 2009-11-16
i suggest DSL (Damn Small Linux)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

system requirement:
DSL supports only [x86]("http://en.wikipedia.org/wiki/X86_architecture") PCs. The minimum system requirements are a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 8 MB of RAM. DSL has been demonstrated browsing the web with [Dillo]("http://en.wikipedia.org/wiki/Dillo"), running simple games and playing music on systems with a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 16 MB of RAM. The system requirements are higher for running [Mozilla Firefox]("http://en.wikipedia.org/wiki/Mozilla_Firefox") and optional add-ons such as the [OpenOffice.org]("http://en.wikipedia.org/wiki/OpenOffice.org") office suite. It is often used in [virtual machines]("http://en.wikipedia.org/wiki/Virtual_machine") due to its small size and modest requirement of RAM

[http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)

---

### Post by Sealbhach on 2009-11-16
Would puppy fit in 16MB of ram? I think DSL would be the only one that would work.

.

---

### Post by youbuntu on 2009-11-16
I suggest selling it on, and buying a better specced older laptop - I don't think I'd have bothered, even for just $4, sorry.

---

### Post by Sealbhach on 2009-11-16
> **glossywhite said:**
> I suggest selling it on, and buying a better specced older laptop - I don't think I'd have bothered, even for just $4, sorry.

For $4 it's a nice toy to play with. 

.

---

### Post by NormanFLinux on 2009-11-16
Very old computers with tiny hard drives and less than 50MB can't run anything but DOS. If you want a GUI based OS on one, Breadbox GEOS is a
good choice. It will run on top of DOS.

---

### Post by The Real Dave on 2009-11-16
> **emigrant said:**
> i suggest DSL (Damn Small Linux)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

system requirement:
DSL supports only [x86]("http://en.wikipedia.org/wiki/X86_architecture") PCs. The minimum system requirements are a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 8 MB of RAM. DSL has been demonstrated browsing the web with [Dillo]("http://en.wikipedia.org/wiki/Dillo"), running simple games and playing music on systems with a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 16 MB of RAM. The system requirements are higher for running [Mozilla Firefox]("http://en.wikipedia.org/wiki/Mozilla_Firefox") and optional add-ons such as the [OpenOffice.org]("http://en.wikipedia.org/wiki/OpenOffice.org") office suite. It is often used in [virtual machines]("http://en.wikipedia.org/wiki/Virtual_machine") due to its small size and modest requirement of RAM

[http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)

+1 

If it won't run DSL, it won't run anything :D Well, maybe [TinyCore]("http://tinycorelinux.com/"), or its little brother, Microcore. DSL is quite easy to use though, MyDSL makes it easy to add more programs :)

---

### Post by NormanFLinux on 2009-11-16
If it won't run LXDE, then it will run only DOS. That's like 16 years ago!

---

### Post by MasterNetra on 2009-11-16
> **Sealbhach said:**
> Would puppy fit in 16MB of ram? I think DSL would be the only one that would work.

.

If you go command line only then yes. GUI, No. That said also, odds are the OP won't be able to do much with it anyway.

---

### Post by wulfgang on 2009-11-16
I think I may just run a command-line based linux without a gui.

---

### Post by NormanFLinux on 2009-11-16
An old computer should be able to boot to GUI. But don't expect it to run 2D and 3D special effects. It can't.

---

### Post by RiceMonster on 2009-11-16
> **wulfgang said:**
> I think I may just run a command-line based linux without a gui. Surely that will work?

Should yeah, but you may still want to remove some daemons and such. You may also want to check out something like freedos.

---

### Post by MasterNetra on 2009-11-16
> **wulfgang said:**
> I think I may just run a command-line based linux without a gui. Surely that will work?

You can run freedos. lol not GUI but I think your able to run the original C&C Redalert game on it. Which is something. Freedos uses only 512kb of ram.

> **RiceMonster said:**
> Should yeah, but you may still want to remove some daemons and such. You may also want to check out something like freedos.

lol beat me to it.

---

### Post by NormanFLinux on 2009-11-16
If you feel comfortable with the command line. If you can wing it, you can do in Linux what we all did in DOS. That's the only operating system they had in computer classes when I was in graduate school and this was before Windows 95 came along.

---

### Post by julianb on 2009-11-16
16MB of ram and a couple hundred MB of hard drive is enough for a GUI based operating system.

Back when systems like that were common, people were running then-popular GUI operating systems on those machines. I don't have experience with early Ubuntu, but I have used old versions of Windows and Mac OS on machines with only 16MB of RAM. 

Software that is more recent, OR operating system software that wasn't written with your hardware in mind, could be difficult or unworkable.

---

### Post by NormanFLinux on 2009-11-16
Breadbox GEOS will run on DOS. The only drawback is the lack of wireless card support but then old computers didn't even have built-in modems!

---

### Post by john_spiral on 2009-11-16
try the lowram option with Slitaz, you might even get a gui.

---

### Post by Grifulkin on 2009-11-16
Tiny Core, seriously. [this](www.tinycorelinux.com)

---

### Post by wulfgang on 2009-11-16
> **Grifulkin said:**
> Tiny Core, seriously. [this](www.tinycorelinux.com)

That is what I will use thanks.

---

### Post by Exodist on 2009-11-16
> **wulfgang said:**
> I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)


DOS 7.0 should run nicely..

---

### Post by pookiebear on 2009-11-16
Another option is 
[http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html](http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html)

Freedos, it comes with TCPIP stack now and a small gui and arachne web browser. Read that article for more info.

---

### Post by SomeGuyDude on 2009-11-16
Does it have a USB slot? If so, pick something like DSL or Sidux and run it off of that. Otherwise you won't have enough power to run ANY applications.

---

### Post by RabbitWho on 2009-11-16
I want to bump this thread because I want to know how it turned out! 

Oh what fun to find a laptop for four dollars and try and make something out of it. there's something you could take with you anywhere and not have to worry about loosing or forgetting. 

Can you imagine in 15 years the computers we're writing on will be worth no money? And we'll be posting here and asking.. Does it have a sixth-sense interface port? No? You just wasted 4 dollars!

---

### Post by lisati on 2009-11-16
I once tried Puppy on a desktop with a 133MHz proceeeror, 64Mb RAM, and a 3GB hard drive. It worked but was a trifle slow for my liking. Since the laptop in question has less RAM, one of the other suggestions already made might be worth pursuing.

---

### Post by mmmichael on 2009-11-16
According to [http://www.netbsd.org/ports/i386/hardware.html]("http://www.netbsd.org/ports/i386/hardware.html"), netbsd can run the X window system on 8 MB of ram.

---

### Post by NormanFLinux on 2009-11-16
Haiku. Internet connection sucks but BEOS should run on all but very, very old hardware.

---

### Post by starcannon on 2009-11-16
> **wulfgang said:**
> I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)
I've run Damn Small Linux on a pII 133mhz with 96mb of ram, an old gateway solo 2500, I later found a pII 366mhz cpu to put in it, and that made it a bit snappier; there was also a pII 400mhz cpu made for that laptop, but at the time I was tinkering with it, those were still going for over $100, and the laptop running was only worth about $150(at the time). I got the 366 for $35 so it was a decent deal for an upgrade.

Have fun with it, old hardware is a hoot to play with, and if nothing else you can mod the thing and turn it into a digital picture frame with music.

---

### Post by Old_Grey_Wolf on 2009-11-16
wulfgang,

I like your avatar.

I hope tinycore works for you. You could also try freedos.

---

### Post by K.Mandla on 2009-11-16
Build it yourself and you'll get more out of it.

[http://kmandla.wordpress.com/2008/11/24/success-icewm-1236-and-xorg-73-at-100mhz16mb/](http://kmandla.wordpress.com/2008/11/24/success-icewm-1236-and-xorg-73-at-100mhz16mb/)

---

### Post by OneMixDJ on 2009-11-17
> **emigrant said:**
> i suggest DSL (Damn Small Linux)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

system requirement:
DSL supports only [x86]("http://en.wikipedia.org/wiki/X86_architecture") PCs. The minimum system requirements are a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 8 MB of RAM. DSL has been demonstrated browsing the web with [Dillo]("http://en.wikipedia.org/wiki/Dillo"), running simple games and playing music on systems with a [486]("http://en.wikipedia.org/wiki/Intel_80486") processor and 16 MB of RAM. The system requirements are higher for running [Mozilla Firefox]("http://en.wikipedia.org/wiki/Mozilla_Firefox") and optional add-ons such as the [OpenOffice.org]("http://en.wikipedia.org/wiki/OpenOffice.org") office suite. It is often used in [virtual machines]("http://en.wikipedia.org/wiki/Virtual_machine") due to its small size and modest requirement of RAM

[http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)

I tried DSL, Deli, even RH 7.2 on a Compaq Presario 1235 laptop with 32MB RAM and all were terrible. DSL and Deli resulted in terrible graphics and RH 7.2 didn't even boot up. I would try a lightweight distro with LXDE, but not sure if my specs would be up to snuff either. It's a shame too because this older machine is in "like new" condition. Be a shame to not use it.

---

### Post by MasterNetra on 2009-11-17
> **OneMixDJ said:**
> I tried DSL, Deli, even RH 7.2 on a Compaq Presario 1235 laptop with 32MB RAM and all were terrible. DSL and Deli resulted in terrible graphics and RH 7.2 didn't even boot up. I would try a lightweight distro with LXDE, but not sure if my specs would be up to snuff either. It's a shame too because this older machine is in "like new" condition. Be a shame to not use it.

For Starters the OP wouldn't be able to use a GUI with DSL for his system. ***16 mb** of ram*. So technically he would have no graphics problem due to the fact he would be pure command line.

---

### Post by starcannon on 2009-11-17
> **OneMixDJ said:**
> I tried DSL, Deli, even RH 7.2 on a Compaq Presario 1235 laptop with 32MB RAM and all were terrible. DSL and Deli resulted in terrible graphics and RH 7.2 didn't even boot up. I would try a lightweight distro with LXDE, but not sure if my specs would be up to snuff either. It's a shame too because this older machine is in "like new" condition. Be a shame to not use it.

Yeah those ultra light distro's like DSL require geeking out on the tinyX server they use. Or at least they used to use Kdrive tinyX; I seem to remember having to do a bunch of stuff to get a more feature rich xserver going. I think I used Xfree when I was playing with DSL

---

### Post by Eagles18 on 2009-11-17
> **wulfgang said:**
> I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)
Dude,I don't think you can run anything on 16MB of RAM.

---

### Post by lisati on 2009-11-17
> **Eagles18 said:**
> Dude,I don't think you can run anything on 16MB of RAM.

:lolflag:

The first "computer" I owned was a hand-held calculator programmable in a dialect of BASIC. Its RAM was expandable to a massive 1KB!!!! I was surprised what I could do with it with a little ingenuity. Sadly it had an early demise after it fell on the floor and was stepped on.

---

### Post by Eagles18 on 2009-11-17
> **starcannon said:**
> I've run Damn Small Linux on a pII 133mhz with 96mb of ram, an old gateway solo 2500, I later found a pII 366mhz cpu to put in it, and that made it a bit snappier; there was also a pII 400mhz cpu made for that laptop, but at the time I was tinkering with it, those were still going for over $100, and the laptop running was only worth about $150(at the time). I got the 366 for $35 so it was a decent deal for an upgrade.

Have fun with it, old hardware is a hoot to play with, and** if nothing else you can mod the thing and turn it into a digital picture frame with music**.
Creative thinking.I like it lol

---

### Post by openuniverse on 2009-11-17
.

---

### Post by I-75 on 2009-11-17
It would have to be a command line distro. 

I have a 133 Mhz laptop with 48 MB of ram and I could not get any Linux GUI to run on it. It could run Windows NT 4.0 or Windows 98.

With 16 MB Ram you might be able to run Windows 95 on your laptop and run some vintage games on it. Or perhaps use it as a digital picture frame.

---

### Post by starcannon on 2009-11-17
** What is DSL-N and  what are Minimum Requirements for it with X-window **

 However DSL does have a [Slightly Larger Cousin, DSL-N,]("http://www.damnsmalllinux.org/dsl-n/") under development. DSL-N is still Damn Small, but has a few extra whistles included (GTK2, 2.6 kernel, added hardware detection). Note that DSL-N is functional, but still under development, and not considered stable enough for for wide use. Watch for version 1.0. 
Minimum Requirements for DSL-N with X-Window: 
 
[LIST]
[*] i486
[*] 16 MBs RAM (recommended 64MBs)
[/LIST]
 

[http://www.damnsmalllinux.org/wiki/index.php/Frequently_Asked_Questions#What_is_DSL-N_and__what_are_Minimum_Requirements_for_it_with_X-window](http://www.damnsmalllinux.org/wiki/index.php/Frequently_Asked_Questions#What_is_DSL-N_and__what_are_Minimum_Requirements_for_it_with_X-window)

You may have to do some tuning, but you should *just* be able to make it go zoom. All the same, I'd watch Craigslist or Ebay or a second hand store for some more ram to pop in there.
I'd say its more a toy than anything else, email perhaps, light word processing. If you can get some more ram for it, it should make a fine bare bones web appliance.

---

### Post by Bunnybugs on 2009-11-17
> **I-75 said:**
> It would have to be a command line distro. 

I have a 133 Mhz laptop with 48 MB of ram and I could not get any Linux GUI to run on it. It could run Windows NT 4.0 or Windows 98.

With 16 MB Ram you might be able to run Windows 95 on your laptop and run some vintage games on it. Or perhaps use it as a digital picture frame.

To little RAM for a picture frame:P lolz

it can't handle the picture loading... takes an hour to load a 5MP picture:P

---

### Post by Warpnow on 2009-11-17
Slitaz.

---

### Post by darkksyde on 2009-11-17
That thing would make a great coaster, seriously now you might wanna try one of the earlier versions of red hat linux

---

### Post by jaxxstorm on 2009-11-17
> **wulfgang said:**
> I found a Toshiba laptop for 4$ at a flea market. It's cpu speed is 133 MHZ and it has 16 MBs of ram. What minimal distribution do you recommend? I'm considering DSLinux, or Puppy Linux. Is there smaller distro than those two? Thanks. :)


I'd love to know if [Spri Linux]("http://www.sprilinux.com") works on it, if you'd mind trying it out for me?

---

### Post by HappyFeet on 2009-11-17
Tiny Core Linux is only 10mb in size. Give that a try. It is the smallest GUI linux I've heard of.

---

### Post by ve4cib on 2009-11-17
You could always set up a VM with similar specs as your new (and amazingly cheap) toy.  Try out a whole bunch of distros until you find one that works.

You might want to check out [KolibriOS](http://www.kolibrios.org).  It claims to need as little as 8MB of RAM, and fits onto a single floppy.  I don't think it's technically a Linux distro, but it is GPL'd, and should work on your ancient hardware.

You may also be able to make Haiku work, though since that's only an Alpha-1 release it may not be suitable for much yet.

Failing those, TinyCore or MicroCore may be your best options.

---

### Post by RabbitWho on 2009-11-17
I'm guessing if Puppy won't work then Spri won't, but i'm curious too!

---

### Post by LoloftheRings on 2009-11-17
Just install ubuntu server and get lxde, DWM (learning curve, but once learned, it's great) or fluxbox.

I recommend installing a 'normal' distribution and install some light stuff instead of gnome/kde.

---

### Post by imtheguru on 2009-11-17
> **Eagles18 said:**
> Dude,I don't think you can run anything on 16MB of RAM.

Windows 95 ran just fine on 8MB ram and a 90MHz Pentium; flew with 16MB. Same for Slackware '96.

DSL and TinyCore will run just fine on 16MB.

I've got DSL running on old Pentium hardware for browsing recipes (dillo) and checking email from the kitchen.

Cheers.

---

### Post by Eagles18 on 2009-11-17
> **imtheguru said:**
> Windows 95 ran just fine on 8MB ram and a 90MHz Pentium; flew with 16MB. Same for Slackware '96.

DSL and TinyCore will run just fine on 16MB.

I've got DSL running on old Pentium hardware for browsing recipes (dillo) and checking email from the kitchen.

Cheers.

By that I meant anything from this century :D

---

### Post by K.Mandla on 2009-11-17
> **Eagles18 said:**
> By that I meant anything from this century :D
Pfft. I run 2.6.31.5 on a 120Mhz Pentium. Linux is what you make of it.

---

### Post by Warpnow on 2009-11-17
> **jaxxstorm said:**
> I'd love to know if [Spri Linux]("http://www.sprilinux.com") works on it, if you'd mind trying it out for me?

It might would work once installed, but I think its impossible to boot an ubuntu live cd on that little ram. Ubiquity won't run. Doesn't work in a VM, anyway, at least for me.

---

