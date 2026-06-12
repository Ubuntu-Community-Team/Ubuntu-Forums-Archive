---
title: "Need Server Recommendation, Advice"
date: 2008-11-13
forum: Server Platforms
---

### Post by Phases on 2008-11-13
I hope this is in the right spot. If not, please move. 

Here's the deal. I have a 5.5 year old mediocre desktop acting as my webserver. 

I've woken up twice this week to it being crashed. Grub 21 error. It seems to fix after I leave it off for a while and turn it back on. 

I've been looking around and actual servers, but, man - you know how it is. I could get one for 200 bucks. I could get one for 20,000 bucks. 

I'm looking for some guidance. Here's what I need kept in mind:

-Good for Ubuntu server, I assume 8.10, may as well upgrade... (so, kubuntu? is that how that works? (then why IS there an ubuntu server?))
-Tower style.
-It will act as a web server for at the moment one low traffic site, a webcomic. 
-email server as well, for a mailing list, and house a couple IRC bots
-needs video, but just to attach a monitor and see what I'm doing, that's it.
-needs to be able to run 24/7 for the next few years.

I don't know what I need, speed/ram wise. The site is, and hopefully it'll still be up when you see this, [http://superstickphase.com](http://superstickphase.com) 

I see the affordable servers all have very low ram and low end processors. What's up with that? Why can I get so much more on a 'desktop' ? 

Will 256 ram and a low end processor do for what I'm doing? Will it be a bit difference? Or should I just get another desktop for a server?

I'd like to spend under a grand if possible. Any advice appreciated. There are few out there I trust more than the uf.org crew.

---

### Post by Nostalos on 2008-11-13
Alot of what you are asking depends entirely not on just what you are running but how often it is used.   These are my personal opinions and I am sure some will disagree with me on points, but this is how I see it.

1.  Should you buy a server or another desktop?
Personally if its going to be anywhere near my personal living space.  Desktop.  Servers are typically loud and obnoxious.  Unless you need something with a hardware Raid 5 controller and craptons of datathroughput there is no real point to buying a true server hardware.


2.  Ubuntu Server vs Kubuntu
The difference is kernel and the amount of stuff installed.  Server Kernel has some added features to ensure compatibility with true server hardware that you would not need in most desktops.   But it will run just fine on most desktops.  Kubuntu is a desktop kernel with all the full desktop bells and whistles installed.   If its a server, you dont need a full desktop.   and if you do. it can be added later via apt-get.


3.  Could you run your site from 256M of RAM and a low end processer? 
Absolutly.   If you install server without a full desktop you could run it from even less than that.  I run a forum site with apache and mysql on 96MB of RAM.  Along with a mail transport agent with spam filtering and a 
Teamspeak Server.    It all depends on what you install and really need.


Honestly,  I don't see much here that would require dedicated hardware.  I personally gave up on the dedicated hardware for this and moved my stuff to a Zen based hosting site like [http://www.quantact.com](http://www.quantact.com)   $14/per month and someone else gets to deal with the headache of owning the hardware.  This is just my two cents though.

---

### Post by Phases on 2008-11-13
Thanks for the reply. I've been toying with the idea of hosting elsewhere but, I dunno.. something inside of me wants me to do it all myself.. 

It would be nice to have GUI installed because sometimes I do last minute editing to comics right on the current server instead of on my desktop, then ftping it, then copying back to the www, etc... But I can certainly do without. 

So I wonder if I should just throw a couple hundred dollars into a low end computer. 

I believe the hard drive is failing but I've had problems in the past with this box, so I don't know if more components are giving me trouble.. I fail hdd after hdd every year or so.  As old as it is I figure I might be better off just springing for all new parts.

---

### Post by oneloveamaru on 2008-11-13
> **Nostalos said:**
> Alot of what you are asking depends entirely not on just what you are running but how often it is used.   These are my personal opinions and I am sure some will disagree with me on points, but this is how I see it.

1.  Should you buy a server or another desktop?
Personally if its going to be anywhere near my personal living space.  Desktop.  Servers are typically loud and obnoxious.  Unless you need something with a hardware Raid 5 controller and craptons of datathroughput there is no real point to buying a true server hardware.


2.  Ubuntu Server vs Kubuntu
The difference is kernel and the amount of stuff installed.  Server Kernel has some added features to ensure compatibility with true server hardware that you would not need in most desktops.   But it will run just fine on most desktops.  Kubuntu is a desktop kernel with all the full desktop bells and whistles installed.   If its a server, you dont need a full desktop.   and if you do. it can be added later via apt-get.


3.  Could you run your site from 256M of RAM and a low end processer? 
Absolutly.   If you install server without a full desktop you could run it from even less than that.  I run a forum site with apache and mysql on 96MB of RAM.  Along with a mail transport agent with spam filtering and a 
Teamspeak Server.    It all depends on what you install and really need.


Honestly,  I don't see much here that would require dedicated hardware.  I personally gave up on the dedicated hardware for this and moved my stuff to a Zen based hosting site like [http://www.quantact.com](http://www.quantact.com)   $14/per month and someone else gets to deal with the headache of owning the hardware.  This is just my two cents though.

_Ubuntu Server vs Kubuntu._ Ubuntu Server is just like the Ubuntu Desktop, minus all of the desktop crap. Kubuntu is Ubuntu Desktop in many ways, EXCEPT.... IT RUNS KDE and NOT GNOME.

Don't install any desktop version as your server version, unless you want a nice GUI you can get on to. Then you will need to decide between KDE or Gnome for that.

---

### Post by Phases on 2008-11-13
So I guess for what I need, which is a webserver for one website, possibly a few more in the furture, I can get away with just a minimal standard desktop?

Is there any hardware you would suggest should I consider beefing up for a 24/7 webserver?

---

### Post by Nostalos on 2008-11-13
Absolutly.  If you need a GUI desktop, personally would recommend 512MB RAM.  Or using XFce as your desktop as it is far lighter than Gnome or KDE.  Web Pages are IO and require little processing power so a low end processor would be fine.   Pretty much anything would do i would imagine.  Plenty of Dell/HP refurbs on overstock.com, any of them would probably do you well.

---

### Post by CrucifiedEgo on 2008-11-13
Dell's got a helluva deal on low end servers right now:

[http://www.dell.com/content/products/productdetails.aspx/pedge_sc440?c=us&cs=04&l=en&s=bsd](http://www.dell.com/content/products/productdetails.aspx/pedge_sc440?c=us&cs=04&l=en&s=bsd)

Pentium dual core 2Ghz
512MB RAM
2x80GB 7200RPM SATA disks
$299

I'm tempted myself, and I don't need a server.

---

### Post by Phases on 2008-11-13
I'd like to build it, and built my rockin' desktop a couple years ago - but I'm in a rush. My box is crashing out nightly. I wake up to a crashed computer, see that it crashed around 10 or midnight. 

Screen blank.

Reboot ... blinking cursur, or really strange [XXX.XX 0x0 etc etc] msgs, or Grub 21. 

First time I live booted and the cd ran a check on the HDD and found errors it 'fixed'. and it worked.

The next night my fix was:

Leave off a minute while unplugging and replugging hard drives and cables on MOBO and what not and flip back on and...  it was okay.

Does that sound hardwareish to you? I only installed ubuntu 8.04 server on it like 3 months ago and have done very little since.

---

### Post by CrucifiedEgo on 2008-11-13
eww.  Yeah, that sounds like a disk controller.  you may be able to just swap out the motherboard on it and be okay, but, hey, any excuse to build a new machine.  Realistically, i'd throw a gig of ram in any box because it's so damn cheap, and apache (which it looks like you're running) likes to use quite a bit of ram.  processing time is moot unless you're doing encoding of some kind or huge database transactions.  buy as much storage as you think you'll need, and something to back it up on, and i'd say you're good.

---

### Post by Phases on 2008-11-13
Yeah that system is:

2.8 GHz
1 Gig
120Gig

.. ok so. looks like I'll be runnin out and buying a cheapo.. Or maybe hit up newegg if I think it can make it a couple more days..

---

### Post by Phases on 2008-11-13
I just wish I could get a decent server server for the same price I could a desktop. It'd be nice to have something that's designed for 24/7 usage, but they're so expensive for the same specs.. ya know?

---

### Post by MJN on 2008-11-13
I've had a number of 'desktop' PCs running 24/7 for years now with barely a moan between them so I really wouldn't worry. Reliability of all hardware has vastly increased over the years to the point where the differences against dedicated machines is virtually non-existent for general purpose use.

Stick with the desktop PC route - more choice, greater value for money, more than enough power and flexibility for your needs. I cannot think of a box it doesn't tick.

Mathew

---

### Post by flashgc on 2008-11-13
Those are pretty good deals, but if we're keeping an eye on the ducats (most of us are these days) it's not hard to find Dell desktops coming off corporate lease. These usually are XP pro installed with 512 meg ram and 40 or 80 gig HDD installed. Small towers allow you to exercise some options in adding storage. These deals can usually be found in the $120~$180 range. I can usually upgrade memory to a gig for ~$20.

---

### Post by Nostalos on 2008-11-14
> **Phases said:**
> I just wish I could get a decent server server for the same price I could a desktop. It'd be nice to have something that's designed for 24/7 usage, but they're so expensive for the same specs.. ya know?


Think you are worrying too much over a server.  It is not that servers are designed for 24x7 running.  They are designed for running in a datacenter where they have to deal with not only their own heat but that of hundreds of other servers as well.    The only added benefit to running a server over a desktop is pretty much the hard drives.  Servers use more expensive SCSI drives that have a longer MTB than SATA or IDE.   Which, you can put one of those in a desktop as well.

---

### Post by Phases on 2008-11-14
Ah, well - too late! I found a 2 or 3 year old [PowerEdge SC430 ]("http://reviews.cnet.com/soho-servers/dell-poweredge-sc430/4505-3125_7-31453136.html")that seemed like a good deal. 200 bucks:

2.8Ghz Pentium D dual core 64bit
1GB DDR2 ECC 533Mhz
80Gig Sata
Raid 1 card

Supposedly runs great so.. instead of continuing to search, considering my rush, and try to figure out what to do I said eff it, I'll pick it up tonight.

Hope I made the right choice - it seems like a pretty decent deal. 

I just made a new thread here regarding it, and how to set up the RAID 1, here:

[http://ubuntuforums.org/showthread.php?t=981945](http://ubuntuforums.org/showthread.php?t=981945)

Thanks for the advice guys. If you think I did okay, let me know, if you think I made a poor, poor, stupid choice, let me know!

---

### Post by MJN on 2008-11-14
It seems perfect.
 
Stop worrying, and crack on with the task ahead!
 
Mathew

---

