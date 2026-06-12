---
title: "Carbuntu"
date: 2007-10-25
forum: The Cafe
---

### Post by toupeiro on 2007-10-25
This has been in my list of things to do for a while, so I think in the next month or so I am going to give it a shot. (if I allocate the funds for hardware)

12V DC power supply
7" touchscreen display
audio fed into car stereo system via aux. audio jack.
Mini-Itx form factor, 2.5" sata disk
Slimline CD-ROM
USB/Firewire/1000baseT/802.11g/PCMCIA



Target:
Ubuntu based automobile computing featuring (hopefully): Audio/Video/Open Source GPS/automobile performance monitoring / tuning if applicable/Voice activated hands free calling (For all of us Californians who are about to be ticketed for hands-on cell phone usage while driving) using 100% open source software if possible.

Has it been done already?  If so, any horror stories? Success stories?

---

### Post by yatt on 2007-10-25
I see two main problems.

The first is simply getting everything to work correctly. I'm not sure how well touchscreens are supported. I can also see you being rather unsatisfied with your sound setup once you get it working. Having the computer do it would be ideal, but also be a mega PITA.

The other problem will be apps. None of the media players have a car mode (I think). You'd probably have to code some new apps so that you have some apps that are usable while driving (ie enormous media controls on the media player, a new system for opening apps (menus/slab/usp all require too much finesse for use in a car)).

---

### Post by Solicitous on 2007-10-25
I remember seeing this sometime back.
[https://www.timekiller.org/carpc/](https://www.timekiller.org/carpc/) he built it into his Mazda.
There is on the gentoo-wiki (unsure if any ubuntu pages exist) on making a car computer, including info on gps etc.  Might be of use.
[http://gentoo-wiki.com/HOWTO_Car_Computer](http://gentoo-wiki.com/HOWTO_Car_Computer)
All I can say is.....have fun.  Looks like a great project.  I've often thought of doing it.

---

### Post by RAV TUX on 2007-10-25
> **toupeiro said:**
> This has been in my list of things to do for a while, so I think in the next month or so I am going to give it a shot. (if I allocate the funds for hardware)

12V DC power supply
7" touchscreen display
audio fed into car stereo system via aux. audio jack.
Mini-Itx form factor, 2.5" sata disk
Slimline CD-ROM
USB/Firewire/1000baseT/802.11g/PCMCIA



Target:
Ubuntu based automobile computing featuring (hopefully): Audio/Video/Open Source GPS/automobile performance monitoring / tuning if applicable/Voice activated hands free calling (For all of us Californians who are about to be ticketed for hands-on cell phone usage while driving) using 100% open source software if possible.

Has it been done already?  If so, any horror stories? Success stories?

The distro has already been done based on Ubuntu:

[Linux ICE]("http://cafelinux.org/distropedia/?q=node/26")

---

### Post by Nano Geek on 2007-10-25
Personally, I don't want anything that's connected to the internet controlling my car.
Especially [Microsoft's Sync.]("http://en.wikipedia.org/wiki/Ford_Sync")

---

### Post by sr20ve on 2007-10-25
removed

---

### Post by Het Irv on 2007-10-25
Question: to go along with the touchscreen... Is there a version of Linux that can run the touchscreen on a Tablet?

---

### Post by Phil Airtime on 2007-10-25
I have enough trouble getting my car radio to tune to 1170 AM. Nah.

---

### Post by RAV TUX on 2007-10-25
> **RAV TUX said:**
> The distro has already been done based on Ubuntu:

[Linux ICE]("http://cafelinux.org/distropedia/?q=node/26")Direct link:

[http://linuxice.com/](http://linuxice.com/)

> **LinuxICE Alpha4 Rolls Out**

 				October 14, 2007 at 01:17 AM by [Kev000]("http://www.linuxice.com/news/news.php?action=mail&uname=Kev000") 
 
 Here is the forth and final Alpha of LinuxICE. This release is a big step forward from the previous Alpha releases and has been a long time cooking.

Torrent:
[LinuxICE-Alpha4 torrent]("http://nghost-project.com/nghost/downloads/LinuxICE-Alpha4.torrent")
[LinuxICE Alpha4 LiveCD]("http://nextabyte.com/nanonymous/downloads/LinuxICE-Alpha4.iso")

New with this release:

New Matchbox Destkop (thanks sanzo)

LinuxICE TrueICE theme (thanks eubey)

Reduced footprint (iso size is only 276MB!)

Latest evtouch touchscreen driver: 0.8.7

New programs: ICETouch, ICEInstall

ICETouch (the touchscreen Calibrator) now supports liliputs, Samsung Q1, Xenarcs and more!

nGhost 1.0Alpha (from unstable).

New LinuxICE software repository so you can get the latest carPC software via ICE-Update.


We hope that we will have LinuxICE Final sometime in the next couple of weeks (with an upgrade path via the LinuxICE repository). Until then, happy testing!
[http://linuxice.com/](http://linuxice.com/)

---

### Post by cyclefiend2000 on 2007-10-25
i wish more people were concerned with the most important task at hand while in the car.... driving!

---

### Post by Het Irv on 2007-10-25
Hey...Maybe we could get Linux to do that too

j/k

---

### Post by toupeiro on 2007-10-25
Thank you for all the great feedback, especially the link to Linux ICE!  a few notes I forgot to add to the regular hardware list:

I'm adding an RF remote control for the mp3 control so you do not  "have" to take your eyes off the road and onto the touch screen to interface with the system.  I have both the ATi and Nvidia RF PC remote controls, and another one I was going to use for a linux based media center.

The motive behind this is to make it as hands free and visually unobtrusive as possible to use when in motion, as much or less than anyone currently would for a car stereo.  Obviously I'm not encouraging messing with the touch escreen while driving, erring to the side of common sense.  The touch screen is there for more control, when its safe naturally.

The deck I have has a stereo-phone aux input that the line out could feed from the PC.  

One of the other challenges I am seeing too is the method of the hands free cell phone usage.  I would use a three phase audio plug (with the help of a soldering iron), or attempt to brave bluetooth.  The three phase plug would be more universal with non-bluetooth phones, but I think bluetooth is pretty standard these days. 

The biggest challenge is the obd2 and obd3 diagnostics software, and the form factor conversion back to USB or DB9 serial.

I found an opensource obd2 project on sourceforge called [freediag]("http://freediag.sourceforge.net/").  I am still looking for an obd3 open source project.  obd stands for on board diagnostics, and is the technology your mechanic uses to troubleshoot and fix problems with your vehicle.

I plan to try and make MSD Prodata+ and ProGraph work through wine if I can.  Its minimum requirements are windows 9x so I bet it won't be too horrible.

Those are the software tools I plan to use to interface with the vehicle.

The wifi was a thought I had to transfer data from systems on a wifi network in the perimeter of your car.  This saves from loading mp3's, videos, or other software on media, so you can conceal the computer completely if you wish and never physically interface with the unit itself.  It will **not** be controlling the car over the internet.

Once again, I appreciate all the feedback, and I will be sure to post updates here as I start to make more progress.  Right now, I am still outlining the project "and its associated costs to see how I can cut them down."

---

### Post by RAV TUX on 2007-10-26
> **toupeiro said:**
> Thank you for all the great feedback, especially the link to Linux ICE!

Good Welcome. ;)

---

### Post by hotrod6657 on 2008-06-11
Bump?  I'm gearing up to do pretty much the same thing, though I have no programming skills so I'm doing my best to utilize pre-existing software, etc.  Just curious if you've mad any progress or is this one doomed to the back burner?

The link to LinuxIce is cool, i'm going to check that out a little bit, and maybe get a bit of inspiration...

hotrod

---

