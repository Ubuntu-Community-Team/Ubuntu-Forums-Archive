---
title: "Old iBook any good as some sort of server?"
date: 2006-10-02
forum: Server Platforms
---

### Post by ixus_123 on 2006-10-02
I own an old indigo iBook that has the following specs:

366mhz G3
320mb RAM
c. 9GB Hard Disk (noisy - overheated it years ago using it on a heat wicking mattress - but still works).

os X is virtually unusable on it due to the 800x600 resolution.  I did try Ubuntu on it with XFCE desktop & that was nice & fast but again I don't really care for the limited screen resolution any more.

I don't want to get rid of the computer - instead I'd like to get Linux (Ubuntu) back on it & use it for something.

I was wondering if there were any suggestions?

I deally I'd like to run a LAMP setup with Wordpress blogging software & Gallery2 to handle photos.  Do you think it would be fast enough to run these - bearing in mind the ram & 4200rpm hard disk.

Any other possible uses?  Proxie / mail server?

I have a main PC running Ubuntu Dapper & a mini-itx N10k, 512mb, 160gb also on Ubuntu acting as a blog server.

I'd rather keep teh ibook over the itx box as it is smaller & has screen & keyboard included - the only limiting factor is hard disk space & cpu speed but I just read an article about someone webhosting on a Lisa!
[http://www.macmod.com/content/view/825/217/]("http://www.macmod.com/content/view/825/217/")

Any tips / suggestions welcome - thanks :)

---

### Post by firefly2442 on 2006-10-02
Try out the desktop install maybe?  If that's too slow, then try a minimal server install and then a lightweight GUI.  As a reference, I've got some old 200 Mhz machines with 128MB of RAM and 7200 RPM IDE drives and they work fine as servers (no GUI like Gnome or KDE).  They're fine for personal use but I certainly wouldn't try to use them for a production server. ;)  Good luck. :)

---

### Post by Cyberflunky on 2006-10-03
Laptops are great routers and servers with there built in power backups. NoCat [http://nocat.net/](http://nocat.net/) would be a great thing to run from your ibook so would m0n0wall [http://m0n0.ch/wall/](http://m0n0.ch/wall/) all thou this would take some hacking to make it work on a Mac.

---

### Post by pppetter on 2006-10-03
800x600 is no fun at all. 

Go ahead and test with personal little LAMP server. The specs are fine for that!

If you aren't already good with the command line...this will be a fun and learning challenge ;)

---

### Post by kelt65 on 2006-10-03
dunno about a router - ibooks only have 1 ethernet interface and no pcmcia slots. Not sure if you could manage to get another ethernet interface in there somehow.

I have a 500mHz iboot 320MB / 20GB 12" screen and xubuntu runs on it just fine ... although I like to just use the console as well.

---

### Post by ixus_123 on 2006-10-03
firefly2442: I did have X / Ubuntu on it before. Gnome was a bit too slow but XFCE was great on it - especially coming from os X - the thing is the resolution is just too much of a step down for me.  I've gotten used to 1280*1024 & anything less is painful.

Cyberflunky: I idn't think of the battery as an UPS - that could prove very useful although it makes me think of another question probably more suited to the PPC section of these boards - how to I set up the bios / firmware to reboot after a power out?

I had a look at no0cat but don't fully understand networking yet & would like to be greedy & keep all my bandwidth for me + I'd be worried about people browsing immoral sites through my router - be that terrorsim stuff, kiddie porn, warez etc

pppetter: - I think I'll go for it.  No Gui - I'm not good at the CLI - I can follow instruction but that's about it.  It would be nice if I could view a GUI representaion of this machine from a remote machine - would VNC do this?

---

### Post by ixus_123 on 2006-10-06
Well the install was a bit of a pain.  I had teh split screen issue & although it's an easy fix I didn't fancy doing it every reboot.

Installing was slow & the installer crashed many times - every time I tried to use XFS or RieserFS as a file system.

I have the Desktop CD & on Dapper there doesn't seem to be an option to just install a base system?  - f this really is the case why not - I wouldn't have thought it that hard - it was on previous CDs.

I settled on ext3 as that was only file system that wouldn't crash the installer but couldn't set up a manual partition scheme.  The installer refused to erase the first partition on hda & would again crash the installer or send me back to square one.  I also couldn't get a yaboot /boot partition set up that Ubuntu would recognise.  Auto install was the only thing that worked which means I only have / & swap.

Far from ideal but good enough for me to mess around with & try things out untill my shipit server edition arrives.

I'm surprised how snappy the site is although once I add a gallery I expect things to slow down a lot.  For my needs, the hard drive & file system don't seem to be a bottleneck as far as teh blog is concerned.  I think the install of Gallery2 will change things though

---

### Post by just_jeepin on 2006-10-16
A lot of people take old laptops and turn them into digital photo frames ([http://www.likelysoft.com/hacks/pictureframes.shtml)](http://www.likelysoft.com/hacks/pictureframes.shtml)). That's what I'd like to do.

---

