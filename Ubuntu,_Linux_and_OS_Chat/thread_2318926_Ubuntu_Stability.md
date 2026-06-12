---
title: "Ubuntu Stability"
date: 2016-03-30
forum: Ubuntu, Linux and OS Chat
---

### Post by ads4 on 2016-03-30
Hi!

I have tried ubuntu before, but nowdays when running 14.04 with updates it seems a bit unstable. For example shut down procedure does not power off computer, applications freezes sometimes (4gb ram amd x2 cpu, should not be a problem) etc. What are your experiences...?

---

### Post by RobGoss on 2016-03-30
Well I have been running Ubuntu 16.04 and for the most part it runs really well. I would give 16.04 a try.


For  some reason I thought 1404 LTS was ending I stand corrected.

---

### Post by QIII on 2016-03-30
16.04 is still in development and may still suffer significant breakage until the release date.

14.04 is supported until 2019 and is hardly near the end of its life.

What exactly, is the "instability" you have noticed?  Have you reported bugs?  Have you asked questions here?

---

### Post by QDR06VV9 on 2016-03-30
> **ads4 said:**
> Hi!

I have tried ubuntu before, but nowdays when running 14.04 with updates it seems a bit unstable. For example shut down procedure does not power off computer, applications freezes sometimes (4gb ram amd x2 cpu, should not be a problem) etc. What are your experiences...?
For myself it is the best OS I have run for quite a spell, reliable, stable, snappy.
I have tried my best to kill this OS(joking here) but it just keeps on keeping on.
Regards

---

### Post by HermanAB on 2016-03-30
In general, Linux is as stable or unstable as you want it to be.

For example, when it was working properly, why did you upgrade it?  If you left it alone, it would have remained perfectly stable.

Upgrading is only a good idea when something is wrong and you want it fixed.  If you upgrade a good system, then an upgrade cannot make it better, it can only make it the same, or worse.  Think about it.

My own systems I install and update and get to work properly.  Then I leave them alone for the next year or three.  I have on occasion left a machine with zero maintenance and zero reboots for almost 5 years - at which point the PSU blew up.  So how stable you want a machine to be, is completely up to you.

---

### Post by ads4 on 2016-03-30
Thank you herman, it might be a good suggestion.

---

### Post by ajgreeny on 2016-03-30
> **HermanAB said:**
> In general, Linux is as stable or unstable as you want it to be.

For example, when it was working properly, why did you upgrade it?  If you left it alone, it would have remained perfectly stable.

Upgrading is only a good idea when something is wrong and you want it fixed.  If you upgrade a good system, then an upgrade cannot make it better, it can only make it the same, or worse.  Think about it.

My own systems I install and update and get to work properly.  Then I leave them alone for the next year or three.  I have on occasion left a machine with zero maintenance and zero reboots for almost 5 years - at which point the PSU blew up.  So how stable you want a machine to be, is completely up to you.
Interesting comment, but potentially insecure and not one that I and most other users would agree with, I suspect.

I believe that ads4 was talking about normal updates of packages, not an upgrade of the distro to another version, which may be how you read the original post.  I would suggest that it is always correct to update all the packages in your OS regularly for security purposes, which could otherwise be compromised.

Distro upgrades to the next version are, however, definitely optional, right up to the point when the running distro version becomes EOL.  Many users are similar to me and stick with the LTS versions only, and I suspect many, also like me wait for a month or two (or more?) after the new LTS release, before moving from, for example 14.04 to 16.04

---

### Post by Retlol on 2016-03-30
> **RobGoss said:**
> Well I have been running Ubuntu 16.04 and for the most part it runs really well. I would give 16.04 a try.

I would be cautious into suggesting people to update without knowing what kind of hardware they have.

For instance fglrx is no longer supported in 16.04, which can be a deal breaker. There's most likely more.

---

### Post by RobGoss on 2016-03-30
> **Retlol said:**
> I would be cautious into suggesting people to update without knowing what kind of hardware they have.

For instance fglrx is no longer supported in 16.04, which can be a deal breaker. There's most likely more.

Well I think as long as you have a complete backup of your system it should be OK unless your machine a really old. I have old and new machines and Ubuntu runs fairy well on all of my machines.

Of course you need to do a bit of research to see if it's compatible with your machine.

---

### Post by Retlol on 2016-03-30
> **RobGoss said:**
> Well I think as long as you have a complete backup of your system it should be OK unless your machine a really old. I have old and new machines and Ubuntu runs fairy well on all of my machines.

Of course you need to do a bit of research to see if it's compatible with your machine.

If you're into gaming and you have an recent AMD card, upgrading will put you on inferior open source drivers as the proprietary ones are no longer supported (they will not work at all). In my case the open source drivers (who perform worse) also only support OpenGL 3.0 or 3.3 while the AMD ones have 4.5 support. This means half of your steam library will no longer be playable.

So yes, research is key and maybe a major issue like this should be better communicated before you attempt to upgrade.

---

### Post by RobGoss on 2016-03-30
Good point, I don't really game so I'm not expert it that field, but I do know gaming machines need special specs for better performance. I can understand the need for a system that will provide what you need..

---

### Post by mastablasta on 2016-03-31
> **RobGoss said:**
> Well I think as long as you have a complete backup of your system it should be OK unless your machine a really old. I have old and new machines and Ubuntu runs fairy well on all of my machines.


I bought mine in 2013, yet support for the AMD chip is being dropped. or rather the only available driver will be opensource. the opensource driver, while it works for day to day tasks (office work), has 20-30% worse performance and also it's power managemenet is not as good. the result is a lot worse battery time. and worse performance when watching high quality videos. so it's not all about gaming. 

the only thing we can hope is that the old radeon opensource will be a lot better in 16.04 (but I doubt it). the new opensource driver (amdgpu) does not support my chip.

---

### Post by Bucky Ball on 2016-03-31
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by vasa1 on 2016-03-31
> **ads4 said:**
> ... What are your experiences...?
Fully updated 14.04 here. No instability to talk of.

---

### Post by buzzingrobot on 2016-03-31
Well, it's impossible to talk about stability without also talking about hardware and changes made to the baseline system. Hardware does fail, and can begin to exhibit bad behavior as it starts down that slippery slope. It's possible for updates to introduce new problems. (Nothing can be tested on all hardware before release, even in Redmond and Cupertino.) Adding PPA's adds packages that may work fine now but not later. Little fixes garnered from some blog or web site can be easily forgotten about but come back to bite us.

---

