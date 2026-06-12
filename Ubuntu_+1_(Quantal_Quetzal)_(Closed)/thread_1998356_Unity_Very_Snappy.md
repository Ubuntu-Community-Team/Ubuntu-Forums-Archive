---
title: "Unity Very Snappy"
date: 2012-06-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-06
Just observing Unity 3D behaving very snappy with qq-alpha1. Nice work.

---

### Post by SpaceCeph on 2012-06-06
I wanna observe this too... Where to get alpha1?

---

### Post by jpeddicord on 2012-06-06
> **SpaceCeph said:**
> I wanna observe this too... Where to get alpha1?

When the alpha is official, you will find it on:

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

If you want to upgrade now, press Alt+F2 and type "update-manager -d". Heed the warnings and the stickies on this forum -- don't do this on a production system!

---

### Post by sammiev on 2012-06-06
> **jpeddicord said:**
> When the alpha is official, you will find it on:

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

If you want to upgrade now, press Alt+F2 and type "update-manager -d". Heed the warnings and the stickies on this forum -- don't do this on a production system!

Been test Alpha since yesterday. Those dates seem a little old.

---

### Post by balloons on 2012-06-06
> **sammiev said:**
> Been test Alpha since yesterday. Those dates seem a little old.

Good catch! I'll try and get this updated properly. Thanks guys.

---

### Post by balloons on 2012-06-06
> **jpeddicord said:**
> When the alpha is official, you will find it on:

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

If you want to upgrade now, press Alt+F2 and type "update-manager -d". Heed the warnings and the stickies on this forum -- don't do this on a production system!

If you do upgrade [report it]("http://ubuntuforums.org/showthread.php?p=12004643") using the isotracker (success or failure) ;-) Both the milestones and dailies have upgrade testcases, which are tested using update manager, not isos.

---

### Post by SpaceCeph on 2012-06-06
I don't want to update 12.04. I need a running system. I want to install QQ in a free partition and want to install it "clean".
But don't know where to get it NOW...

---

### Post by balloons on 2012-06-06
> **SpaceCeph said:**
> I don't want to update 12.04. I need a running system. I want to install QQ in a free partition and want to install it "clean".
But don't know where to get it NOW...

We're testing what will become the alpha1 iso release; you can try installing it right now and then report success fail if you would. The links are here -- on that page of tests, click the 'link to download information'. Download and install, and report according to how you installed (most likely Install (manual partitioning)).

amd64
[http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16976/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16976/testcases)

i386
[http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16978/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/221/builds/16978/testcases)

FYI, the images are always up on cdimage.ubuntu.com also if you wish.

---

### Post by sammiev on 2012-06-06
> **SpaceCeph said:**
> I don't want to update 12.04. I need a running system. I want to install QQ in a free partition and want to install it "clean".
But don't know where to get it NOW...

Use at your own risk. Works great so far. [Here]("http://iso.qa.ubuntu.com/qatracker/milestones/221/builds")

---

### Post by ventrical on 2012-06-07
I have been just updating the daily builds - quantal-desktop-i386.iso- using zsync and I had assumed that yesterdays build was alpha 1?

---

### Post by zika on 2012-06-07
> **ventrical said:**
> Just observing Unity 3D behaving very snappy with qq-alpha1. Nice work.You made me to take a shot in Unity after some time. Thank You... ;)

---

### Post by jpeddicord on 2012-06-07
> **ventrical said:**
> I have been just updating the daily builds - quantal-desktop-i386.iso- using zsync and I had assumed that yesterdays build was alpha 1?

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule)

I think Alpha 1 freeze has been in effect, so you were seeing the preparations for it. A1 is officially available sometime today, assuming no hiccups.

---

### Post by jerrylamos on 2012-06-07
Well, maybe if you're into 3D.  On an older laptop that doesn't do generic-pae hence can't test quantal on it, I put slitaz on it with midori and flash.  Runs entirely in memory.  Internet video is fastest on that laptop than I've seen in any ubuntu on any of my pc's (and I'm an ubuntu bigot).

So I'm chasing a bug on quantal with widescreen notebook and external monitor - systems settings, Display, "apply" seg faults bug #1007588.  If there's a fix I could try 3D but do note I'm into applications not eye candy.  Meanwhile because of the bug I'm stuck at 1024x768.

Have fun,

Jerry

---

### Post by balloons on 2012-06-07
> **jpeddicord said:**
> [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule)

I think Alpha 1 freeze has been in effect, so you were seeing the preparations for it. A1 is officially available sometime today, assuming no hiccups.

Yep, by the time your read this the announcement should have gone out. The iso's from yesterday turned out to be the final for alpha one. The release notes have some goodies on bugs and etcera in them; have a gander.

[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1)

---

### Post by Dlambert on 2012-06-08
> **ventrical said:**
> Just observing Unity 3D behaving very snappy with qq-alpha1. Nice work.

Installing just because of this!

---

### Post by fjgaude on 2012-06-08
Well, snappy, no. gtkperf shows as about 7 in 12.10 while in 12.04 it's about 5.

---

### Post by MG&amp;TL on 2012-06-08
> **fjgaude said:**
> Well, snappy, no. gtkperf shows as about 7 in 12.10 while in 12.04 it's about 5.
Unity isn't Gtk. 

Although I do appreciate your point, I haven't seen a lot of difference. Maybe it's people's clean installs?

---

### Post by Dlambert on 2012-06-08
Just tried partial upgrade as stated previously in this thread install failed.

---

### Post by kaldor on 2012-06-08
I have not seen any difference between 12.04 and 12.10 here. Anything in particular to pay attention to?

---

### Post by balloons on 2012-06-08
> **kaldor said:**
> I have not seen any difference between 12.04 and 12.10 here. Anything in particular to pay attention to?

<OFF-TOPIC>balloons has spotted a wild Kaldor! Missing you on the #u+1 channel mate. I'm even running (and loving!) the nouveau driver thanks to you.</OFF-TOPIC>

Mostly the changes are updates all around -- beta builds of ffox, all the new gnome 3.4/3.5 bits, and the incoming slew of debian updates. Behind the scenes, work is being done to port everything to python3 (some of which has landed), and openjdk7. Also, 

Libreoffice 3.6.0-beta1 is coming
Update Manager got updated, with more to come
GTK 3.5 is coming

---

### Post by kaldor on 2012-06-08
> **guitara said:**
> <OFF-TOPIC>balloons has spotted a wild Kaldor! Missing you on the #u+1 channel mate. I'm even running (and loving!) the nouveau driver thanks to you.</OFF-TOPIC>

Oi! Yeah, I'll be around a lot more once development picks up/after this semester ends. And good to see that my open source driver evangelism has worked on someone ;)

Regarding the changes between Precise and Quantal, I was referring to Unity. I meant that I'm noticing no difference in performance/changes whatsoever.

---

### Post by mc4man on 2012-06-08
> **kaldor said:**
> I have not seen any difference between 12.04 and 12.10 here. Anything in particular to pay attention to?

Really not much has changed as yet in compiz/unity, the latest unity update was mainly a workaround to a gcc-4.7 build fail.

compiz-0.9.8 will have a number of bug fixes & a significant change to rendering, whether that impacts performance good, bad or not at all remains to be seen

(some of the changes can be seen in 12.04 in a pre-proposed ppa for compiz. [https://launchpad.net/~vanvugt/+archive/compiz-preproposed](https://launchpad.net/~vanvugt/+archive/compiz-preproposed)

Was usable in 12.10 till just recently, now I wouldn't do so

---

### Post by cariboo on 2012-06-08
I'm not on my main system (sitting on the deck using my tablet) :-), but I found Quantal uses considerably less ram than Precise.

---

### Post by ventrical on 2012-06-09
My whole point is that after installing that -alpha-freeze- is that Unity (the dash and lenses) seemed more responsive and quicker to load on my Dell Dimension 3100 where Precise and Oneric took a lot longer to respond to mouse clicks (not by much mind you). So , whatever the performance increase .. it may be negligible to some.. it appears that the Unity Dash and Lenses are  snappier and punchy.  I am sure there ARE bugs and there will be more bugs and it will probably get more sluggish as it develops.  Guess we will have to wait and see.

---

### Post by fjgaude on 2012-06-09
> **cariboo907 said:**
> I'm not on my main system (sitting on the deck using my tablet) :-), but I found Quantal uses considerably less ram than Precise.

I tested your feeling and found the two to be near identical with an equal load of apps.

Also the same tests showed under gtkperf 12.10 to be about 6; 12.04, about 5. So... we have a ways to go to catch up.

Now 12.04 with kernel 3.5 is 4.23.

All these are on my main box, i5-2504S, 8GB RAM, SSDs, etc.

---

### Post by mcellius on 2012-06-09
Installed QQ here a day or two ago and it's doing pretty well.  I agree with Cariboo that it uses quite a bit less RAM than Precise, but Unity doesn't seem any snappier (or any slower, either).

---

### Post by Jimmyfj on 2012-06-10
I've been running 12.10 Pre-Alpha/ now Alpha1 after upgrading via Internet from 12.04. 

This is far from my first release-testing, I first did a testing-spin from good old 8.04, and have been on testing ever since. It's a lot of fun but make sure to have secondary storage for your most crucial data.

**Way to go. Both Unity AND Firefox must have been eaten steroids.**

---

### Post by jerrylamos on 2012-06-10
> **cariboo907 said:**
> I'm not on my main system (sitting on the deck using my tablet) :-), but I found Quantal uses considerably less ram than Precise.
What operating system are you using on your tablet?

Jerry

---

### Post by cariboo on 2012-06-10
> **jerrylamos said:**
> What operating system are you using on your tablet?

Jerry

I'm running Icre Cream Sandwich (V. 4.0.3), I'm having to much fun playing with Android apps. I haven't had the time or inclination to try Ubuntu on it yet.

---

### Post by jerrylamos on 2012-06-11
BTW, somewhat on topic, I upgraded precise lubuntu to quantal lubuntu and that's running snappy.  Do note this is a Pentium M no -pae flag so its got all of quantal that's update installable except 3.4.0-5.  The 3.2.0-24-generic kernel is running fine with the rest of quantal (so far).
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
Linux ThinkPad-T40 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i686 GNU/Linux

Now sudo aptitude full-upgrade tries to put on 3.4.0-5 which won't work, so sudo aptitude safe-upgrade works fine for picking up quantal updates that are appropriate for Pentium M and linux 3.2.0-24.

Maybe some of the snappy Unity is snappy quantal, although I have no measurements.  Working fine, better than I expected.  Until the infamous "next update"...

Jerry

---

### Post by balloons on 2012-06-11
> **jerrylamos said:**
> BTW, somewhat on topic, I upgraded precise lubuntu to quantal lubuntu and that's running snappy.  Do note this is a Pentium M no -pae flag so its got all of quantal that's update installable except 3.4.0-5.  The 3.2.0-24-generic kernel is running fine with the rest of quantal (so far).
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
Linux ThinkPad-T40 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i686 GNU/Linux

Now sudo aptitude full-upgrade tries to put on 3.4.0-5 which won't work, so sudo aptitude safe-upgrade works fine for picking up quantal updates that are appropriate for Pentium M and linux 3.2.0-24.

Maybe some of the snappy Unity is snappy quantal, although I have no measurements.  Working fine, better than I expected.  Until the infamous "next update"...

Jerry

Jerry, I'd be keen to see how this goes going forward with your pae kernel. Let me know if something ever break for you :-)

---

### Post by stoneguy on 2012-06-11
I'm with ventrical. I'm usually using fallback mode with my [testing] eeePC900 (Celeron 900/915GM), but just for a giggle, decided to bring up Unity2D for once. Don't know whether the latest gcc is in play, or what, but speed is impressive! Too bad it doesn't seem to carry back to Classic No Effects.

---

### Post by ventrical on 2012-06-12
Thanks Guy. I had just seen that with U2D. Especially when I click on the <installed> see more # results - and the icons appear instantaneously, not the top down, bottom up sort of raster of previous releases.  It  (U2D)works really well on this Dell Dimension 3100, 3.GHz This is the stuff that really gets me because these early alphas work like high speed super_computers, they are just beautiful.. but then come the updates and ....

---

