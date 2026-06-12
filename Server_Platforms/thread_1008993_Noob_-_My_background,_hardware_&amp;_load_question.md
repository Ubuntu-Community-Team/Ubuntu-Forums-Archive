---
title: "Noob - My background, hardware &amp; load question for server"
date: 2008-12-12
forum: Server Platforms
---

### Post by jtsmith on 2008-12-12
Hello all, my first post in the server forum, please bear with me. Just a quick little bit of background on me first:  I was really into computers and worked at an ISP when I was a teenager, doing a little bit of Linux server stuff back in the mid to late 90s.  (the distros of linux we used were not graphical back then!)  Long story short, instead of becoming a computer science major, I ended up going to pre-med and then to grad school to become a doctor of chiropractic, and have been practising for almost 5 years now.  I have been out of linux for a long time, but would like to make a comeback and learn some server administration again, and a little programming as well in time.
Just bought the book Ubuntu Server Administration by Michael Jang, and it looks like a good intro-hold my hand- first book here.

Why am I in the Ubuntu Server forum?  Well, after I just lost a HDD on a machine last week, and it was a mad scramble to try to save some data, I can see a need for health care professionals to have an off-site storage, web server, e-mail, and VPN that is HIPPA compliant for their office, which does not reside at their physical office, in the sense that it would be like an off-site backup for them in a time of need.
(I know, I should have had a backup system in place, thankfully it wasn't a HDD at the office that went down, but a personal one at home - but imagine if it was the office...)

So, I would like to put my hand to the plow so to speak and get this accomplished, and then offer it first to my local friends, and then if it works well, maybe to my colleagues for their offices.  I am currently thinking of running the servers out of the back room at my office w/ a dedicated line.

The timing is really interesting, because I have just been given a Dell Poweredge 1800 server and a WG-X700 firebox by a good friend who no longer needs them.  So, my question pertaining to the hardware is, what would the load be like on a system like this, and should I split my file server & Web/ftp/E-mail/Messaging server like we used to do at the ISP when I was a kid, or run it all on one box?
Box 1:  Dell Poweredge 1800 - Dual Xeon 2.8Ghz w/ HT for 4 total threads, 4GB DDR2 RAM, (2) 160GB SATA HDDS in RAID 1 on CERC 6channel 1.5 SATA card, (2) SCSI cards, Dell 72GB tape backup drive, Gigabit Ethernet, on board ATI 7000 graphics.
Box 2:  My personal box, which I would be willing to make into another server if needed:  Dual core Athlon64X2 6000+ at 3.0Ghz, 8GB DDR2 800 RAM, ATI HD3850 graphics, 250GB SATAII HDD and (2) 500GB SATAII HDDs (was thinking of putting these in the poweredge and making that the file server).

Thanks for any thoughts - I am willing to put better hardware in my box, perhaps a dedicated RAID board, Gigabit Ethernet, and PhenomII when they come out 1st Q. 2009...
Sorry for a long post, but I really don't know where to start, but I'm not afraid to roll up my sleeves and spend a couple months of long nights learning.
Sincerely,
Dr. Jedidiah T. Smith (D.C.)
Ventura, California

---

### Post by kerry_s on 2008-12-12
just using the 1 box for everything should be fine, after all you need to get your feet wet and just dealing with 1 box will make things easier, you always have the option to add to your setup down the line if it turns out you need more.
your hardware's fine just start reading up on the software and learning how it now works, been a lot of changes since the 90's.
so start here:
[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

grab the iso to install and then read the doc's:
[https://help.ubuntu.com/7.10/server/C/index.html](https://help.ubuntu.com/7.10/server/C/index.html)

---

### Post by tubezninja on 2008-12-12
The specs on the server seem pretty good.  Unless you expect constant traffic to the backup server involving massiv amounts of data, I see no reason to break out the tasks into two boxes, if you're just starting out.  As demands increase, that could change though.

You'll find that in the past few years, the capability of the servers and the OS has improved dramatically.  Though, a lot of us still find that the best way to manage a server is through the command line. :)

---

### Post by jtsmith on 2008-12-12
Thank you for the vote of confidence and the answer to run it all on one box - I understand there is exponentially more power in one box today than there was in two back in the late 90s!  I just didn't know how demanding this project would be on the server.

Installed The desktop of Ubuntu 8.10 just to get a feel for it, and I will install the server version later tonight per Michael Jang's book instructions.

Two more questions if you have time, please:

1.  Should I use RAID 1 or RAID 5 for the 500GB HDDs in the server box?  I realize RAID 5 would require a third 500GB HDD - I'm just not sure which is better at this point; RAID 1 or 5.

2.  Is there good linux support for a relatively inexpensive, yet decent video card that can run up to 1680x1050 for native resolution of a 21.6" widescreen I just bought for the server (didn't come with a monitor).  The integrated ATI Radeon 7000 is not that powerful - I can't seem to get it to run that resolution, but it could just be the drivers.
One issue is that the card will have to be PCI, PCI-X or PCI express X1 or X8 -- Dell's infinite wisdom, they did not make a PCI express x16 slot.  :p

Thanks so much for the help!  I hope to report back with success.
Sincerely,
Dr. Jed

---

### Post by kerry_s on 2008-12-12
1. try raid1 just simple mirroring.

2. you know linux servers don't have a gui by default and it doesn't take much to display simple text. the stock vid is just fine. you'll probably just need the monitor for the initial setup, then just run it headless.

---

### Post by jtsmith on 2008-12-12
Hi, thanks for the advice.  I will just keep the two in RAID 1 then.
Also on the monitor - yeah, that is true about no GUI w/ server, I had forgotten about that - I just wasn't real happy w/ the resolution on the current install of desktop 8.10 I have on there - it only lets me do 1440x900, and as that's not the native display resolution, it looks a little worse than it should.  :p
But I won't worry about the GUI and get cracking with the server stuff.
Thanks again!
Dr. Jed

---

