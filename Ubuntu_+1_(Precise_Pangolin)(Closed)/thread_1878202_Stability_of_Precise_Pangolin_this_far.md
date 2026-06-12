---
title: "Stability of Precise Pangolin this far"
date: 2011-11-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sports fan Matt on 2011-11-09
I've said in the past that I wasn't going to upgrade every 6 months in the past but after my desktop was hosed by Windows (Needed my Dragon Naturally Speaking) and with Precise being supported for 5 years, this may be the 1st release ever since I started with Gutsy that I just leave and update

-how stable is it for those running on Intel graphics?  Any major issues?
-If now isn't a good time to upgrade, when would be (before final release)

---

### Post by ranch hand on 2011-11-09
As long as you have absolutely no intention of using it as a production OS there is no problem.

It is pretty stable right now.  This will probably change rather quickly now that real work on it has begun.  

A1 will probably still be pretty usable.

A2 usually starts getting "interesting".

That condition will last pretty much up to the release of the RC.

If you are not adventurous I would not install until the RC.  If you are, now is as good a time as any.

---

### Post by cariboo on 2011-11-09
The developers are still getting over their UDS hangover :). it is expected that we will start seeing real changes around the 15th of the month

---

### Post by sports fan Matt on 2011-11-09
Good to know.  I just had to install over the last month 3 to 4 upgrades (all flawless) just to get to Oneric.  I'll probably wait until the RC.

---

### Post by effenberg0x0 on 2011-11-09
This cycle is the first time I installed it to my main machine/HDD. So I'm taking all the risks. I don't recommend it to anyone, but it is _extremely_ stable in 16hours/day very heavy use. No difference from running a stable version so far (of course, no extreme development going on). But I think this looks like it will be a less dramatic cycle (not much to change if you think about it). It always is a lot of fun anyway.

---

### Post by Harry33 on 2011-11-09
> **sox fan Matt said:**
> I've said in the past that I wasn't going to upgrade every 6 months in the past but after my desktop was hosed by Windows (Needed my Dragon Naturally Speaking) and with Precise being supported for 5 years, this may be the 1st release ever since I started with Gutsy that I just leave and update

-how stable is it for those running on Intel graphics?  Any major issues?
-If now isn't a good time to upgrade, when would be (before final release)

Believe me it will not stay stable. It will break.
So, there are no big problems if you have a working ISO (may also be Oneiric release) around in order to chroot when the system will not boot at all. Of course you need to be familiar with working with the plain console and wget, dpkg ...

---

### Post by grahammechanical on 2011-11-09
If you do not believe in upgrading every six months why are you even thinking about installing 12.04 before it is ready for distribution?

You are on 11.10. So stick with it until the middle of May 2012 and then go against your principles and upgrade to Precise Pangolin and then you will not need to upgrade for another five years. And further more you will have much less to moan about.

Regards.

---

### Post by seeker5528 on 2011-11-10
> **sox fan Matt said:**
> -how stable is it for those running on Intel graphics?  Any major issues?
-If now isn't a good time to upgrade, when would be (before final release)

Stable, no.
Crashy, no.
Crashy with Intel, don't know, but my past experience with Intel video, it often seems a bit quirky.

If you are comfortable dealing with problems, now is as good a time to upgrade as any.

If you prefer not dealing with problems, you probably want to wait until the beta cycle, or at least closer to the beta cycle.

This *is* an LTS development cycle so on the one hand the developers want to get things a little more polished, but on the flip side they need to choose versions of stuff that they feel comfortable with supporting for 5 years, which sometimes means going with some version of something that is a little raw.

Later, Seeker

---

### Post by matt_symes on 2011-11-10
I'm getting a kernel panic when i shutdown around 80% of the time. 

It's fglrx causing the crash.

Nothing shuts it down apart from a power off.

This install went from 11.04->11.10 (briefly)->12.04. I will investigate at some point soon.

Apart from the crash, it's fine. I'm using it now.

---

### Post by keithpeter on 2011-11-11
> **effenberg0x0 said:**
> But I think this looks like it will be a less dramatic cycle (not much to change if you think about it). 

I hope there are many changes 'under the hood' now the front end has been stabilised. wifi drivers, power management, all those tweaky things.

Cheers

---

### Post by Ichtyandr on 2011-11-25
Can pre-released lts Ubuntu get less stable than Debian testing?

---

### Post by Harry33 on 2011-11-25
> **Ichtyandr said:**
> Can pre-released lts Ubuntu get less stable than Debian testing?

I do not think that is a relevant question.
Ubuntu is not Debian after all.

---

### Post by Ichtyandr on 2011-11-25
> **Harry33 said:**
> I do not think that is a relevant question.
Ubuntu is not Debian after all.

I have no intention for flaming or anything. 
My understanding was that Ubuntu LTS imports from Debian Testing and then starts polishing and making it more stable. If that is true, can it really bork your system, because Debian Testing is perceived as a workable option by lots of individuals?

---

### Post by Harry33 on 2011-11-25
> **Ichtyandr said:**
> I have no intention for flaming or anything. 
My understanding was that Ubuntu LTS imports from Debian Testing and then starts polishing and making it more stable. If that is true, can it really bork your system, because Debian Testing is perceived as a workable option by lots of individuals?

The Debian Import phase is in the beginning of the cycle.
For Precise this LTS Debian Import Freeze will be on 12th January 2012.

---

### Post by jerrylamos on 2011-11-25
> **Ichtyandr said:**
> I have no intention for flaming or anything. 
My understanding was that Ubuntu LTS imports from Debian Testing and then starts polishing and making it more stable. If that is true, can it really bork your system, because Debian Testing is perceived as a workable option by lots of individuals?

From the viewpoint of a several year tester, from time to time ubuntu will make a change in install - ubiquity for example, which might render new installations borked.  Now even on oneiric ocelot Beta 2 I got an install borked.  Simple, well into install long after the partitioning changes apt-get got an update failure which left Grub all screwed up so I couldn't even boot the other partitions.  Grub "rescue" would come up but half the documented "rescue" commands wouldn't work.

Several hours and CD's later I managed to find a CD (lucid lynx) which would re-do grub successfully.  Updated the beta 2 and then install worked.

Whether Debian gets this kind of failure I don't know.  Only Debian I've run is a cut down CD live version which worked, it was "stable" not in development.

Reading through the precise pangolin advertising the main push for precise pangolin is to be a several year LTS long term service so I would "assume" the push is for stability instead of radical new features (like unity-3D) which could upset the stability. 

Also there is a conscious push in ubuntu leadership to abandon older pc's.  Example wireless hasn't worked on my Thinkpad T40 since Narwhal.  Yes there's a launchpad bug no development's not interested.  I keep a lucid lynx (fast! easy!) partition when I want to do wireless work.

Another push is to grow ubuntu past a 700 MB CD.  Now I don't have a real problem with that since there is likely to be a minimal CD boot which loads the rest from the internet (with a wired connection for my T40).

Plus there are "lightweight" versions around example lubuntu which might still fit on a CD, and other linux's based on ubuntu such as bodhi.

Anyway as Alpha's and Beta's roll by expect crashes....with people all over the world throwing package changes daily into the pot there's bound to be some screw - ups.  Let the breakages begin...

Jerry

---

### Post by OrangeCrate on 2011-11-25
> **jerrylamos said:**
> From the viewpoint of a several year tester, from time to time ubuntu will make a change in install - ubiquity for example, which might render new installations borked.  Now even on oneiric ocelot Beta 2 I got an install borked.  Simple, well into install long after the partitioning changes apt-get got an update failure which left Grub all screwed up so I couldn't even boot the other partitions.  Grub "rescue" would come up but half the documented "rescue" commands wouldn't work.

Several hours and CD's later I managed to find a CD (lucid lynx) which would re-do grub successfully.  Updated the beta 2 and then install worked.

Whether Debian gets this kind of failure I don't know.  Only Debian I've run is a cut down CD live version which worked, it was "stable" not in development.

Reading through the precise pangolin advertising the main push for precise pangolin is to be a several year LTS long term service so I would "assume" the push is for stability instead of radical new features (like unity-3D) which could upset the stability. 

Also there is a conscious push in ubuntu leadership to abandon older pc's.  Example wireless hasn't worked on my Thinkpad T40 since Narwhal.  Yes there's a launchpad bug no development's not interested.  I keep a lucid lynx (fast! easy!) partition when I want to do wireless work.

Another push is to grow ubuntu past a 700 MB CD.  Now I don't have a real problem with that since there is likely to be a minimal CD boot which loads the rest from the internet (with a wired connection for my T40).

Plus there are "lightweight" versions around example lubuntu which might still fit on a CD, and other linux's based on ubuntu such as bodhi.

**Anyway as Alpha's and Beta's roll by expect crashes....with people all over the world throwing package changes daily into the pot there's bound to be some screw - ups.  Let the breakages begin...**

Jerry

I've been busy with other things, and haven't had much time to participate here, but, I was actively involved with testing several of the earlier versions. I always told people that if you find something that actually works during the alpha stages of development, count yourself lucky. Personally for me, the alphas are the fun part, I start losing interest when it gets to the Beta/RC stages.

---

### Post by MG&amp;TL on 2011-11-25
I would test-but I can never get it to install...maybe I need to keep a partition as 'development' and just keep doing the upgrades.

I find that from A3 onwards you can rely on it 90% of the time, but that's me. Only occasional borking.

---

### Post by ronacc on 2011-11-25
@ MG&TL if the problem getting it to is install is the partitioner crashing see here post # 6 [http://ubuntuforums.org/showthread.php?t=1874553](http://ubuntuforums.org/showthread.php?t=1874553)

my 2 installs Ubuntu  & lubuntu  have been rock solid so far , lubuntu keeps picking the wrong video driver and ubuntu just started doing it but other than that once past the installer partitioning  glitch they haven't crashed yet .

---

### Post by MG&amp;TL on 2011-11-25
OK, thanks for that, I've got partitioner working now. Lubuntu is just booting to black screen though. I guess I'll just have to keep trying.

---

### Post by ronacc on 2011-11-25
@ MG&TL if you have an nvidia card it may be  trying to install the wrong driver, it tries to install the 173 legacy driver for me ,I need nvidia-current, nvidia-current in the repos is broken right now (or was last night) get the 290.10 driver from nvidia and hand install it if you need the nvidia-current  , also see here post # 12 [http://ubuntuforums.org/showthread.php?t=1884150&page=2](http://ubuntuforums.org/showthread.php?t=1884150&page=2) .

---

### Post by MG&amp;TL on 2011-11-25
thanks. Give it a try once the latest image downloads. :D

---

### Post by TenPlus1 on 2011-11-25
Upgraded from 11.10 to 12.04's daily build (25th Nov) and everything went smoothly...  Rebooted to find desktop worked fine and fast, tested usual programs and they all ran, even my wireless speed went up...

AMD Athlon 2400+ XP
2GB Memory
Nvidia MX 4000 series (old yeah but works)
10gb filesystem, 66gb home

My only quam is too many windows when updating, how about a tab interface, beginner screen front, console behind showing what's really happening... saves having 2 separate windows...

Same could be said for ubiquity install, forget the drop down console, beginner screen with what Ubuntu can do screens and progress on front, a tab that switches to more advanced console view behind...

---

### Post by Jordanwb on 2011-11-29
Aside from my ath9k driver issue which hasn't been resolved yet I haven't had any long term issues. Everything is fast and pretty stable. For a version which hasn't hit Beta 1 yet it's very good.

---

