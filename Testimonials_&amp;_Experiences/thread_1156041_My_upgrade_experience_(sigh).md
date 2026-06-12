---
title: "My upgrade experience (sigh)"
date: 2009-05-11
forum: Testimonials &amp; Experiences
---

### Post by lazyart on 2009-05-11
I usually wait no less than a month before I upgrade to the next version of Ubuntu.  Gives the developers a little more time to fix things and that strategy works pretty well.  I've read too many stories from Feisty forward that there is little to gain from upgrading the day of the new release.  Stay behind and at least if something is broken when you upgrade, there is likely a workaround posted to keep you productive.

This time around I didn't wait quite as long.  I ran the updates, then hit the switch on Jaunty.  My system is a Pentium Dual Core with a GeForce 8500 GT driving dual monitors.  The OS runs from a RAID 1 array of 250 GB SATA drives.  It hosts 3 VMs-- Debian for Apache, Ubuntu for Zimbra mail server, and one running Win XP.  I also run an FTP server on the desktop which facilitates remote backup for my daughter's Windows machine while she is away at college.  And yes, I run 64 bits.  Allows me to run 6GB of memory.  Plenty of room for the virtual machines and still not use the swap file.

So, the upgrade begins.  I'm busy doing other things around the house and come back to see it wants to confirm updating a configuration file.  Seeing that I need it still, I tell it to leave the file alone and things continue on.

Sometime later I see it wants to reboot.  I close my files, take a deep breath and reboot.  I get the new splash screen as it shuts down and of course again when it comes back.  First thing I notice is the resolution is correct on both monitors (sometimes after the rare reboot one of them is incorrect, but it's easy to fix).  Nice login screen btw.

I log in and get the usual music.  Good sign.  Launch Thunderbird and Firefox.  Check.  I head over to youtube and I'm happy to see Flash is working again.  What a headache that used to be.  For kicks I try to access VMWare Server but naturally it's not responding.  After most kernel updates (and definitely after an OS update) you have to run```
sudo /usr/bin/vmware-config.pl
``` to rebuild the modules for the new kernel.  That's quite old hat for me... don't even have to think about it.  The virtual machines start up but one gives me an error.   I restart it and mail is flowing again.

(sigh) No excitement.  Just a shiny new OS upgrade.  I like some of the changes and tweaks I see.  But yikes, I was expecting something to break here. [sarcasm]:([/sarcasm]

---

### Post by Niniel on 2009-05-11
Damn, that really sucks, no problems. 
Poor you.

---

### Post by Crafty Kisses on 2009-05-11
Haha good read my friend. I really don't like doing dist-upgrades because there's always a chance that it might break your system. I always backup my data of course, but I did a "dist-upgrade" to Jaunty and everything went flawless like your story. I was really amazed to tell you the truth. Everything was still in place surprisingly. To the OP I see you use RAID1, I was thinking about it since it mirrors the HD so it is failsafe, as of now though I'm going to stick with RAID0. Anyway again, nice read.

---

