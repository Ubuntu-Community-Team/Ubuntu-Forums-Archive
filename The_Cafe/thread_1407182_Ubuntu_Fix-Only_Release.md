---
title: "Ubuntu Fix-Only Release?"
date: 2010-02-15
forum: The Cafe
---

### Post by dmaxel on 2010-02-15
I've been wondering this, and I know I'm not the only one, but what if we had a fix-only release, or something extremely similar to it.

Here's my thinking: Ubuntu is overall an excellent operating system. You can do so many things that Windows can't, and then some. Although Windows programs don't run on Ubuntu/Linux (forget about WINE & Co. for now), it's no fault of Linux's. Too many developers just don't care about making programs that can run on Linux, although this trend is starting to change. So all of this isn't really a concern.

What IS my concern is the fact that although Ubuntu can run flawlessly without any problems on some systems, it has problems on others. For example, I tried to run Ubuntu on my dad's computer, and it works fine with the exception of sound. No matter what I tried, it never came. Not only is sound one of the few major problems in Ubuntu, but wireless is too. Compared to Windows, the wireless is pretty mediocre. Where I get full bars in Windows, I constantly drop out in Ubuntu.

So again, to repeat my question: Why not have a release that takes the focus off of new features and more at fixing many hardware (and a little bit of software) problems by either finding/developing new solutions to them or just to simply implement known fixes? I believe this would help the most for any Linux user, whether new or veteran, to get a "it just works" feeling. As far as I know, Lucid isn't really changing the current focus.

---

### Post by SilverDragon on 2010-02-15
It's not a bad idea. This post reminds me of this.

[http://www.tannerhelland.com/commentary/ubuntu-linux/ubuntu-1004/](http://www.tannerhelland.com/commentary/ubuntu-linux/ubuntu-1004/)

People would just end up complaining about not having new features and it be a boring release though.

It might be better in the long run but from a marketing perspective I'm not sure how well it would do.

---

### Post by Gallahhad on 2010-02-15
+1
A fix only release or 3 would be very good.

---

### Post by Seq on 2010-02-15
If you use the LTS releases, they do get fix-only updates. The current version is 8.04.4

---

### Post by juancarlospaco on 2010-02-15
LTS got fix only releases 8.04.1, 8.04.2, 8.04.3, *(...) *

Use Windows drivers on Ubuntu.

---

### Post by dmaxel on 2010-02-15
> **Gallahhad said:**
> +1
A fix only release or 3 would be very good.
Yes, I would think so too. How I imagine them, it could be the same thing as the Mac OS X update from Leopard to Snow Leopard.

Sorry for not quoting the others, as I am currently on my phone, but even if those are fix only releases, they only include fixes as far as the normal releases go. They won't have any fixes that the regular releases don't. Therefore, there is still a lot of time devoted to new features in the normal releases. I was thinking of having a release that concentrates on just fixes, as a lot more will get done that way.

Finally, I tried using ndiswrapper, but but every time I tried to get it to work it said it was invalid.

---

### Post by jken146 on 2010-02-15
Run Debian stable if you want something that works consistently.

---

### Post by dmaxel on 2010-02-15
> **jken146 said:**
> Run Debian stable if you want something that works consistently.
How is it different than Ubuntu if Ubuntu is based on Debian?

---

### Post by forrestcupp on 2010-02-15
One problem is that the Ubuntu team doesn't do a lot of the developing.  They just take things that other people develop and package it all together into a neat distribution.  So if something doesn't get fixed upstream, it probably isn't going to be fixed in Ubuntu either.

---

### Post by snowpine on 2010-02-15
Hi dmaxel, in my opinion :) the best way to get hardware support is to use the latest release. Each new version of the linux kernel has support for the newest hardware, and in my experience, Ubuntu gets better and better at recognizing my hardware with each release.

> **dmaxel said:**
> How is it different than Ubuntu if Ubuntu is based on Debian?

The two projects have different goals. Debian is focused on stability and the free software philosophy; Ubuntu is more concerned with desktop usability.

---

### Post by juancarlospaco on 2010-02-15
But hardware problems sometimes are not easy to fix, 
is just like if you try to run Windows on ARM, PowerPC, and such.

Drivers and specifications need to be open source...

---

### Post by dmaxel on 2010-02-15
True, I do believe that hardware support is getting better bit by bit. I am running Karmic, and I have to say that sound (minor) and wireless are the only problems I've had. I also had to do some configuring to get my printer and scanner to work, but it's fine now. However, I have tried Ubuntu on other systems, and it doesn't work as well.

As far as development, I understand now. How long do people predict will Linux (desktop) come to a point where it "just works"?

---

### Post by markbuntu on 2010-02-15
If you want stability and OOB workability then stay away from the latest hardware and the latest distro releases. It takes some time for new hardware drivers to get written and it also takes time for a new distro to get tested on enough hardware to get the bugs fixed.

Generally an LTS is updated for bugs and to add support from upstream for new hardware where possible. 8.04 is extremely stable and supports far more hardware OOB than when it was first released. Applications are not generally upgraded to new versions so there is that trade off. 

There are also some remixes aimed at hardware like the UNR for netbooks and Xubuntu for older machines and a few aimed at very specific hardware, like kuki linux for the Aspire One which has now been extended to work with the EE.

---

### Post by stmiller on 2010-02-15
Yeah Debian stable is what you are after. Releases take 2-3 years of bug squashing before they are ready.

It's boringly stable. :P

---

### Post by dmaxel on 2010-02-15
> **markbuntu said:**
> If you want stability and OOB workability then stay away from the latest hardware and the latest distro releases. It takes some time for new hardware drivers to get written and it also takes time for a new distro to get tested on enough hardware to get the bugs fixed.

Generally an LTS is updated for bugs and to add support from upstream for new hardware where possible. 8.04 is extremely stable and supports far more hardware OOB than when it was first released. Applications are not generally upgraded to new versions so there is that trade off. 

There are also some remixes aimed at hardware like the UNR for netbooks and Xubuntu for older machines and a few aimed at very specific hardware, like kuki linux for the Aspire One which has now been extended to work with the EE.

> **stmiller said:**
> Yeah Debian stable is what you are after. Releases take 2-3 years of bug squashing before they are ready.

It's boringly stable. :P
Hmmm, well, to bring forth a truthful story, I am currently running a webserver. However, I fairly recently switched from Debian to Ubuntu because I was impressed by the fact that Ubuntu used kernels that seemed to be a couple years ahead of Debian, as well as newer versions of apps like PHP. But I'm learning from this thread, and have set our server to now only update to LTS releases....at least until I might start getting jealous of the bling of newer normal releases and just say What the heck and switch it back to normal distribution upgrade.

PS: @Comment about Debian being boringly stable: Well, I guess that would be important too if the absolute newest software isn't required. I once read in an article somewhere that a robotic submarine (don't look for accuracy here) was able to go through a horrendous obstacle course, or do something majorly important. That robotic sub happened to be running Debian at its core.

---

### Post by markbuntu on 2010-02-17
For a server and mission critical applications stability is critical, that's why so many use Debian, updates in Debain fix only bugs and do not break other things. Ubuntu supports their LTS server for 5 years so, by the time you need to upgrade to a lucid server it will be well stabilized.

---

