---
title: "Ubuntu X.org Guru Calls for Desktop Help"
date: 2009-11-30
forum: The Cafe
---

### Post by Ric_NYC on 2009-11-30
Nov 25, 2009

**Bryce Harrington is agonizing over the nontrivial task of delivering a working X server for Ubuntu. On the Ubuntu desktop mailing list he speaks of a flood of bug reports and appeals to improving the situation**.

The X server must ideally cooperate with with open and closed ATI, NVIDIA and Intel cards, but not forget those from smaller providers, a fact that becomes most noticeable to users when they're sitting in front of blank screens instead of the desktop. The call for help from Ubuntu users keeps coming to Harrington as bug reports on Launchpad.

**Now Harrington is calling for help himself. His graph of bug reports for Karmic Koala in recent weeks "literally went off the chart," which prompted him to recommend concrete steps to avoid future X.org problems**.

Where do these bugs come from? The increase in bug reports is for Harrington not so much an indicator that X.org is qualitatively poor, but that lately more users are reporting bugs. S**ome of the bugs are truly emerging from the new GDM2, the dynamic kernel module support (DKMS) and upstart, which most recently took over coordinating the Ubuntu boot process**. The new features didn't cause altogether that many new bugs so much as make existing ones worse, although there were enough stable release updates (SRUs) to deal with the worst cases.

Suggestion 1: hold off on upgrades. Harrington offers the possibility for the future of waiting for the first wave of patches to come in before having the update-manager recommend upgrades to users. At least users who are trying to keep their systems up to date can then enjoy some stability. He suggests the same for LTS as for Lucid.

Suggestion 2: a new testing model. The volume of bug reports is also causing Harrington headaches in terms of his workload. He's had to concentrate on Ubuntu 10.04 for time and personal reasons, even though X.org work is still continuing on the current Ubuntu. Although he'd like to be conservative with X.org, major changes to the X infrastructure are probably needed. HAL will be dropped, Radeon is getting kernel mode setting (KMS), and NVIDIA and ATI driver installations are being rearchitected. There is also a move underway from -nv to -nouveau+kms drivers.

[B]Harrington therefore suggests putting together a desktop testing team, with "a smaller number of people who just
commit to running the same sequence of test steps say once a week." The results will then clearly show where improvements and degradations are emerging. Once the number of successful tests starts decreasing is when bug reports should be written at high priority so as to fix the problems. For Harrington, the solution would be better than filling an already overloaded bugtracking system[/B].

Will this help? Harrington's idea makes sense if indeed a fixed release cycle doesn't allow a large spectrum of users to test the system effectively. To find bugs at all, the project needs tons of users testing the finished Ubuntu. Harrington thus wants new users and early adopters to take a crack at it so that the general Ubuntu user will have an SRU to work with.

Experimental users are responsible themselves for moving early to a "stabile" Ubuntu version. New users don't notice any problems because they don't run into them, or when they do, they currently send in bug reports and repair their systems via updates. Better yet, they uninstall Ubuntu and revert to Windows/Mac or another Linux version. As it currently stands, the Ubuntu project in the worst case might run into both scenarios.

In view of these changes, the project has to ask itself, however, "is it really impossible to thoroughly test the Ubuntu version to avoid these problems before its release?"

(Kristian Kissling)

---

### Post by Exodist on 2009-11-30
I would be all about helping if I wasnt starting back to college in January and honestly will not have the time. :(

I really hope some users with experience can assist him tho.

---

### Post by quinnten83 on 2009-11-30
The only thing I could help with is bug reporting and I believe he already got enough of that.
But I hope he get's some help soon, @ least he was honest in saying that he can't handle this alone.

---

### Post by argie on 2009-11-30
How does one join this experimental testing group? I have just the computer for the job. It currently functions fine on Karmic but will be sitting idle for a while until I get a HTPC case for it.

Is there some sort of automated testing suite which will do certain things with the graphics hardware or will I have to repeat certain tasks every day? I don't mind doing the latter, but naturally the former would be better.

---

### Post by u.b.u.n.t.u on 2009-11-30
I emailed Bryce the other day to offer to variously test xorg, but I haven't heard back yet.

In the meantime I have submitted two xorg related brainstorm ideas, links to which can be found my signature.

---

### Post by u.b.u.n.t.u on 2009-11-30
> **argie said:**
> How does one join this experimental testing group?

This is Bryce's launchpad page with contact details.

[https://launchpad.net/~bryceharrington](https://launchpad.net/~bryceharrington)

---

### Post by cariboo on 2009-11-30
> **argie said:**
> How does one join this experimental testing group? I have just the computer for the job. It currently functions fine on Karmic but will be sitting idle for a while until I get a HTPC case for it.

Is there some sort of automated testing suite which will do certain things with the graphics hardware or will I have to repeat certain tasks every day? I don't mind doing the latter, but naturally the former would be better.

Install Lucid Lynx and then started posting problems and solutions [here]("http:///ubuntuforums.org/forumdisplay.php?f=377").

---

### Post by u.b.u.n.t.u on 2009-11-30
Lucid Lynix Schedule
[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

Alpha 1, 10 December 2009.

---

### Post by phrostbyte on 2009-11-30
The move to KMS is exposing a ton of problems (remember Jaunty + Intel?), but it's essential to the modernization of the Linux video stack.

---

### Post by u.b.u.n.t.u on 2009-11-30
* KMS, Kernal based Mode Setting.

[http://www.h-online.com/open/features/Revamped-Graphics-746915.html#graphics](http://www.h-online.com/open/features/Revamped-Graphics-746915.html#graphics)

Rather an indepth article. Basically KMS is a "better" way of doing things when it comes to a GPU (graphics processing unit) interacting with Linux.

That is my understanding anyway.

---

### Post by phrostbyte on 2009-11-30
> **u.b.u.n.t.u said:**
> * KMS, Kernal based Mode Setting.

[http://www.h-online.com/open/features/Revamped-Graphics-746915.html#graphics](http://www.h-online.com/open/features/Revamped-Graphics-746915.html#graphics)

Rather an indepth article. Basically KMS is a "better" way of doing things when it comes to a GPU (graphics processing unit) interacting with Linux.

That is my understanding anyway.

Currently X.org does mode setting and actually has control over the video hardware. KMS is to give control of the video hardware to the kernel, and leave X.org to do windowing and network transparency. Consequence is X.org can be made simpler (and run in user mode). Also it means you can do a lot more video related stuff without X.org, which is nice for embedded devices which do not require windowing.

---

### Post by u.b.u.n.t.u on 2009-11-30
> **phrostbyte said:**
> Currently X.org does mode setting and actually has control over the video hardware. KMS is to give control of the video hardware to the kernel, and leave X.org to do windowing and network transparency. Consequence is X.org can be made simpler (and run in user mode). Also it means you can do a lot more video related stuff without X.org, which is nice for embedded devices which do not require windowing.

Thank you for explaining that. Are you on a related Ubuntu team and or project?

---

### Post by argie on 2009-12-01
Thanks ubuntu and cariboo, I will download the Lucid Lynx now.

---

### Post by handy on 2009-12-01
Matters aren't helped when proprietary drivers come out (ATi currently) that aren't compatible with the current version of X.org.

Anyone using Arch, & an ATi GPU have had to block 5 packages from upgrading to keep the old xorg-server 1.6, as catalyst 9.10 & 9.11 are incompatible with xorg-server 1.7.

Many people are looking forward to the completion of the transition to both great 2D (as exists already) & great 3D via the open-source solution. (which we are all hanging out for)

I can't offer any help, I don't run Ubuntu.

I take my hat off to Bryce, he really has got a tough job at the moment.

---

### Post by toupeiro on 2009-12-01
This is what FOSS is all about.  We've all gotten a lot from Xorg, I encourage anyone with hardware lying around to help.  I'm going to try to piece a PC together over the next few days for LL and help out.  Can't really use a VM for this kind of testing.  This affects all of us, ubuntu users or not.  Xorg extends much, much further than ubuntu.

---

### Post by u.b.u.n.t.u on 2009-12-01
handy, well said indeed and my thoughts exactly. Bryce is doing a herculean job for Ubuntu on the xorg front. 

I am unable to use Ubuntu freely at this time as I require 3d graphics and flash before I can commence the transition process from the Windows environment. So my Ubuntu installation is largely for testing purposes.

---

### Post by u.b.u.n.t.u on 2009-12-01
> **toupeiro said:**
> This is what FOSS is all about.  We've all gotten a lot from Xorg, I encourage anyone with hardware lying around to help.  I'm going to try to piece a PC together over the next few days for LL and help out.  Can't really use a VM for this kind of testing.  This affects all of us, ubuntu users or not.  Xorg extends much, much further than ubuntu.

Good call. I will being testing the Alpha releases of 10.04.

---

