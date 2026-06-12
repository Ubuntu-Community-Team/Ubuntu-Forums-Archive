---
title: "If you could choose your hardware first..."
date: 2007-08-24
forum: The Cafe
---

### Post by Baby Uranus on 2007-08-24
Hello Gang,

This is my first post here. I've built a decent amount of linux boxes but I'm new to Ubuntu as of a few months ago. I was impressed with how easy it was to get mediawiki up and running on a lamp server.

Now I am going to build a new machine to run another lamp server. But before I get on newegg, for a change I'm going to ask people who have already been around the block (i.e. you), which chipsets to avoid on the motherboard and on the video card, and which chipsets have been good actors. That's the gist of this post.

To narrow things a bit, I'll say that I'm currently thinking of running 7.04 server, getting php/apache/mysql/mediawiki, bind, postfix, mailx, vsftpd, and ssh configured, then adding the ubuntu gui/desktop environment. Everything worked well with 6.06, but I have no idea about 7.04. I'm sure I'll find out. I'm a little worried about php in the 64-bit environment.

For hardware, I'm thinking intel, core 2 duo (most of my existing machines are AMD, but it seems time for a switch back). OTOH if the consensus was to go with amd because of chipset issues, I'd be fine with doing so. The only thing I'm rather militant on is I want to stick with nvidia for the graphics chipset, but I very much would like feedback reg. which specific nvidia graphics chipsets work and which ones don't work well, especially with twinview. Ideally I'd like to avoid stuff like the xorg.conf changes necessary to get my mx4000 card running with twinview, etc. So far my favorite linux video chipset has been the FX5200.

Thanks for any info, in advance!

---

### Post by bdoe on 2007-08-24
I haven't actually done much with it yet other than turn it into a file server for my LAN (I tried configuring it as a PDC until I realized that the versions of Windows running on my other computers weren't capable of connecting to domains), so I don't know how well it would perform in the real world, but...

I recently built my Ubuntu 7.04 LAMP server box out of old, long-obsolete parts I had lying around the place - namely, an ASUS K7V266-E mainboard, an AthlonXP+1500 CPU, a Radeon 8500LE, a generic NIC, and 1GB of PC2100 CL3 memory.  The parts came from the monster gaming rig I built six years ago and had since replaced.  Ubuntu installed without a hitch.  I installed GDM on it (I'm not afraid of CLI environments, I just prefer being able to do many things at once), set up Samba, and got it all running.  Just for kicks, I even installed Beryl on it, and was pleasantly surprised with how well everything worked!

Currently it's running headless, so I should probably get back in there sometime and get SSH set up on it.

Not sure if that really answered your question or not, but...  If what you are building is going to primarily be a server, you really don't need much in the way of video cards.  If you have an old Radeon 7500 lying around somewhere, you can use it.  More than likely, you're going to run it headless anyways, remotely accessing it via SSH, then the choice of video hardware becomes pretty much irrelevant.

I don't know about Intel and its chipsets, but I've had nothing but good experiences with Ubuntu on AMD and both Via and SiS chipsets, using ATI GPU's.

---

