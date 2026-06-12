---
title: "Hardy is wonderful..."
date: 2008-05-03
forum: Testimonials &amp; Experiences
---

### Post by prshah on 2008-05-03
Well I just finished upgrading all my systems to Hardy. I approached it with trepidation, considering all the negative comments on the forums, and the fact that both X and Firefox are betas, but for all that... it's wonderful and troublefree for me!

I was running Gutsy on both my notebook (Fujitsu LifeBook P5010) and my desktop (home-brew Intel Core 2 Duo 1.6/1Gb/160Gb SATA/2xDVDRW) and decided to upgrade using the alternate CD, rather than download from the net on each system.

The notebook installation went without a hitch, and except for a couple of issues (one of which resolved itself with subsequent updates), works fine, right out of the box.

On the desktop, I ran into trouble, because the electricity went off while the upgrade was in process. This dumped me to a command prompt on reboot. However, it was fixed easily, by restarting in "Recovery Mode", then ```
dpkg --configure -a
``` which started off where the upgrade was interrupted.

This didnt complete successfully, and after a bit of research (and ignoring important warnings), I used ```
dpkg --configure -a --force-all
``` to complete the job.

While this did give me a working system, it was one with a broken sudo, which a little research required a change to /etc/hosts file (changed "localhost" to the name of my machine before the update).

Once that was done, when logging in, I was required to install 700Mb (!!) of upgrades; luckily, most were from the hardy CD itself. About 200mb+ was for other programs and compiz, etc., which had to be downloaded.

Considering the magnitude of the disaster, I was sure that I'd have to reinstall, but there was no difficulty at all; hardy recovered nicely inspite of an interrupted upgrade.

The recovery process for the interrupted upgrade is outlined here so that others who find themselves in the same boat can take heart that it's easy to fix.

All said and done, hardy is great, even better than gutsy. Cheers to all who have worked so hard on it.

[edit]
forgot to mention; that el-cheapo bluetooth stick which refused to do anything in gutsy except display an icon; it working great now!
[/edit]

---

### Post by diaz028 on 2008-05-03
Yep, have to agree with you here. It seems like a multitude of people are complaining, but really its more like satisfied people are not praising.

I prefer this version of ubuntu over gutsy just because of the less amount of debugging required to get my system going 100%. I actually had no problems at all!

Installed fresh, set up my desktop flashy dashy compiz/emerald, then installed a few updates and programs that I use, and within 1 hour I was right back on EVE online from a fresh install.

I'm impressed anyways... The thing fits on a 700mb cd! Clicking the update notice will surely get rid of most initial problems IMO, since anything not included in the 700mb cd will be included in the repos.

Anyways, hope everything goes well for all you caffeine addicts out there ;)

-D

---

### Post by abuakel on 2008-05-03
Yes, I agree.. Hardy has been wonderful!
I'm usually one who changes the default wallpaper once I get it, but I especially love the default wallpaper :biggrin: I've based my whole gnome environment around it ;)

---

### Post by shazbut on 2008-05-04
I've updated 4 of my systems so far, no problems with the install process. Slight hiccups with the local (au) repo being shite (causing problems with restricted drivers), changed to the one provided by my isp and things are really good now.
My main system is way quicker than before, but it did have a some baggage from previous upgrades and a bodged mythtv install.  Also I can leave compiz on now and run opengl games in windows without any trouble, couldn't do that before.
Haven't seen the random crashes others have been talking about at all.
Only thing I could suggest to change would be the option to pick a repo mirror during install to avoid updates etc timing out.

---

### Post by buntunub on 2008-05-04
Gotta agree here. Hardy is indeed a giant leap forward despite the Samba and domain (etc/hosts) bugs which seem to be quite pervasive. There has been some restructuring that was done to bring better security and tighter networking integration which, I think, was bound to bring some bugs with it. These things are essential to an enterprise level release, and most people just don't understand the significance of this so they complain. That, in conjunction with the X server changes that occurred from Gutsy, make for quite the progressive Desktop experience. One could even say now that Hardy is far superior to XP, because Ubuntu brings all the best that that the Open Source/FOSS community has to offer in an extremely user friendly environment, all nicely packaged together all in all.

---

### Post by netanakin on 2008-05-04
Hardy is cool.i agree!
It has less bugs and more easier to install from live cd since it has a geuine install only option which helps it install on system which have low ram such as mine.256mb.

---

### Post by NightwishFan on 2008-05-04
I concur. So far it's kde4 is very stable compared to Fedora's.

---

### Post by stinger30au on 2008-05-04
i love 8.04 it has been a god send. everything and i mean *EVERYTHING* works out of the box and rock solid as well.
i have been tinkering with KDE4 as well. only a few minor hickups, but nothing to worry about.

Way to go ubuntu team

---

### Post by imT on 2008-05-04
I wouldn't say it's wonderful but is the best os available, as a end user i don't find much differences 
between gutsy and hardy, nevertheless they are and they'r welcomed. 
Ubuntu is not perfect, just the best os available.

---

### Post by rcdeacon on 2008-05-04
Hardy has been good for me as well. Starting with beta 5 and now both desktop and laptop run primarily with Hardy! A very satisfying experience so far.

---

### Post by wycito on 2008-05-04
one thing I was not happy was the with gutsy was my graphics driver  was not as sharp as i wanted for my 22'' Acer, and the gui would get sluggish every so often, now without a glitch, all fantastic

---

### Post by tact on 2008-05-04
Yep my experience with Hardy has been nothing but pleasure.  I am finding it fast and rock solid.

I am running on a pretty low horsepower hardware, a Dell D410 laptop, single core 1.73GHz Pentium M, 1.5Gb RAM.

Since Edgy pretty much all the hardware has been detected and functioning, all the Fn-keys for screen brightness, turning wifi on/off, etc..  the separate volume and mute buttons etc. 

The only thing that has had its ups and downs has been suspend/hibernation.

Hardy has suspend/hibernate/resume all working for me nicely and repeatedly and reliably, something I have not seen since early feisty.

It maybe just imagination but I do think that Hardy is running smoother and faster than Gutsy.

I am finding compiz very smooth and responsive.  And I am loving pulseaudio.

I always have a spare HDD for this laptop as it is essential for my work.  The spare is in an external USB enclosure and is an identical clone to the working drive so that at any time I need to I can swap the spare into the laptop internal drive bay and boot and get back to work.
(After cloning I do incremental backups with grsync to keep datafiles up to date).

Having the spare HDD ready to "go live" at any time means I can be a little more cavalier when it comes to upgrading.

So my first taste of Hardy was when I did a dist-upgrade when it was still in beta.  Even beta Hardy was very good for me.   Of course there were some days in the beta period when some things were a bit broken (for a while there evince would not work properly - for example).  But these things are to be expected.

I kept updating until beta became RC and RC became Hardy Release version.

All the various updates/upgrades went through without issues and I was never left with a system that was unusable.

I have also had experience doing full clean install.  After Hardy went final release I downloaded the Live and Alternate installer CDs.

I swapped out the internal HDD (the one repeatedly updated/upgraded from Gutsy, to Beta, to Release) and kept it aside as my ready to boot back up.  Then installed the spare drive into the drive bay, deleted all partitions and installed clean and fresh from CD.   (This is what i am running now).

I must say that I do not notice much difference between the "upgraded" and the "clean installed" drives.  Both have been fast, stable, and a pleasure to use.

---

### Post by shazbut on 2008-05-12
Just did a clean, dual boot build with WinXP SP3 / Hardy on a Dell D830.  Over 1.5 hours to install XP, with much faffing about getting all the drivers necessary for XP to work (64MB for bluetooth? WTF?).
Ubuntu installed in <30 minutes, everything working wireless, connected to WPA2 Enterprise network in a few clicks.

Only fly in the ointment, the old laptop HDD Load_Cycle_Count problem bit me.
Used the fix here to stop the click-click-click:
[http://duopetalflower.blogspot.com/](http://duopetalflower.blogspot.com/)

Edit: And resume from suspend doesn't work, but I've yet to see it work on any laptop I've tried so far.

---

### Post by pacsum on 2008-05-12
With the update released this weekend the system is working how it should.

---

