---
title: "I've figured out how to stabalize ubuntu/kubuntu"
date: 2012-06-22
forum: Testimonials &amp; Experiences
---

### Post by TomB19 on 2012-06-22
I've discovered a way to have a working installation that will be stable for quite some time.  The trick is to never take updates.  Ever.

Important security updates - don't take them
Application updates - don't take them

:D


I know I'll get flamed for this but I find the base install of 12.04 to be completely stable.  One of my Ubuntu systems has taken 5 updates since installing 12.04 and it's now down but three of the other four upgrades caused problems.  Between CUPS, rpcbind, and dovecot, the system was in a state that would not allow it to take new updates without removing a bunch of packages (like: CUPS, rpcbind, etc.).

I have a Kubuntu system that has been running Kubuntu 12.04 for a month and it's been perfect.  It's screaming at me to take updates but I happily ignore it.

I'd rather be hacked than have to reinstall every 45 days.


To be more specific, I intend on reinstalling every 12 months, or so.  I might even reinstall the same version, just to freshen the packages.  Of course, I'll set aside a day to get do the work.

Also, it's clear that not taking security updates will pose a risk.  Back up all documents regularly and retain backups for some time. I think it's also important to stay behind a pretty tight firewall.


It's a great feeling to know your system works properly and will continue to do so for months on end.  I can't imagine playing the update lottery again.

---

### Post by |{urse on 2012-06-22
Interesting, on how many different hardware configurations do you find this to be true?

---

### Post by oldos2er on 2012-06-22
Moved to Ubuntu Testimonials & Experiences.

---

### Post by TomB19 on 2012-06-22
I'm not surprised this got moved.  lol!


An old nVidia nForce 4 system with dual core AMD (3800+).  4GB.

An AMD 790 / Phenom II system (quad core). 8 GB.

An Intel i5 (quad) / H67 (I think).  4GB.


My brother has an AMD 870 / Phenom II (quad) with 4GB.


My brother finds exactly the same upgrade issues.  We call each other if one of us feel we are forced to upgrade so the other one will know if it will work, or not.

I know this has been moved to "experiences".  If you're having trouble stabilizing your system and you have discovered this thread, it's not just you.  It's everyone I know.  Taking upgrades will knock you down after only just a few.  It's always one of a handful of packages, like CUPS.

... just clean install your system once per year or so and enjoy a totally stable system.


By the way, the zfs arrays have been moved from my primary system to the old nForce 4 system that I use as a server.  They're working great down there.  Those arrays are up to 22 of those 2TB drives now and every single one of those consumer grade drives has failed and been replaced at least once over the years.  Recently, I started replacing failed WD20EARS and WD20EARX in favor of Seagate 2TB drives.  We'll see how that goes.  ZFS has made the whole thing possible and kept it stable.

---

### Post by vidtek on 2012-06-22
It depends how you use your system.  I have a system which I use for my HTPC and once it's working and running I ghost the image and turn all updates off.  With Mythtv it's an extremely fragile environment and I have learned over the years not to indulge the urge for the latest and greatest.

My laptop I use as a test bed to find the "perfect O/S"  Perfect for me that is, that's the beauty of Linux and why I love it so much, there are just so many options out there.

Tony.

---

### Post by TomB19 on 2012-06-22
I'm a myth guy too, vidtek.  I like the integration that has gone into Ubuntu but my TV system was down more than it was up.  Once the backend database updates, you're pretty much toast and have to upgrade the front end too or restore the database.

I didn't mention that because that fragility comes from Myth.  I wish there was a lighter PXE boot media player but minimyth does a good job for me.

---

### Post by Myrddin Emrys on 2012-06-23
I've never had an Ubuntu update break the system. If I did, and it kept happening, I'd probably conclude it was time to change distributions - I really need a system that's both secure and stable!

---

### Post by coffeecat on 2012-06-23
> **Myrddin Emrys said:**
> I've never had an Ubuntu update break the system.

+1.

@TomB19, do you have the proposed repository enabled, or did you have it enabled when you experienced these problems? How many PPA repositories have you enabled?

---

### Post by TomB19 on 2012-06-23
```
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main 
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main
```

---

### Post by KBD47 on 2012-06-23
You sound like someone who would love Debian Stable :-) I like Debian  Stable with backports, you basically keep a system that is the same with  some newer apps. I usually boot Debian Stable alongside one of the  Buntu's for the reason you are using Ubuntu without updates.

---

### Post by Elfy on 2012-06-24
> **TomB19 said:**
> ```
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main 
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main
```

I've never had issues with updates - other than during a dev release cycle.

I don't though use PPAs for the wrong release.

Is your system stable before you add PPAs? 

But I digress as this is not the place for support.

---

### Post by Cheesemill on 2012-06-24
> **Myrddin Emrys said:**
> I've never had an Ubuntu update break the system.
+1
And this is on a machine running Quantal Quetzal.

On my current machine  I've been running 12.10 since the day that Precise came out and was running 12.04 for 6 months before that whilst it was still in development. The only time I've had an issue it was resolved with the next set of updates a day later.

---

### Post by whatthefunk on 2012-06-24
The only time I ever had an update break my system was when I forgot to disable a beta ppa.  Theres a nice tool called ppa-purge that will undo updates from select ppas.  Its in the repos.

---

### Post by cariboo on 2012-06-26
Just to add my experience, I always run a development version, the majority of updates don't break the system even on the dev versions. I have a system in my shoprunning Precise that only gets updated once a month or so, as I don't get out there as often as I'd like, the last time, last week, there where over 80 updates waiting, and the previous time there were 200+ updates.

If security updates, are breaking your system, then there must be some underlying problem, that needs to be fixed, as they are only changes to existing installed packages, and small ones at that.

---

### Post by lento_ on 2012-06-26
I run Kubuntu in a VM and did my first set of updates in ages yesterday. Result: it's dumped me back down to a low resolution, as if the guest plugins have stopped working. Looks like fiddling around time then. I should have resisted the temptation to update!

On the other hand, I use Ubuntu as the main O/S on another computer and rarely have any problems at all.

---

### Post by Cheesemill on 2012-06-26
If you've had a kernel update then the 'guest plugins' need to be recompiled.

What VM software are you using?

---

### Post by lento_ on 2012-06-27
That makes sense.

I'm using Virtual box. I'm not overly bothered though as it's a good excuse to do a fresh install upgrade!

---

### Post by Cheesemill on 2012-06-27
If you install the VirtualBox Guest Additions using the Additional Drivers application rather than mounting the iso through VirtualBox then they will recompile automatically every time a new kernel is installed.

---

### Post by lento_ on 2012-06-28
Interesting, thanks, I'll give that a go.

---

