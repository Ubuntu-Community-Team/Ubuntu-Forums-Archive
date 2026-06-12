---
title: "Ubuntu, I need stability!"
date: 2014-02-02
forum: Ubuntu, Linux and OS Chat
---

### Post by morsedl on 2014-02-02
Dear Ubuntu Dev Team,

I need stability!  The lastest round of updates (I updated around January 29, 2014) really messed up the video on all of my machines.  I have four devices running Ubunutu and they all have AMD/ATI video cards.  I am well aware that AMD/ATI drivers are a constant sore spot and routinely problematic, but the problem had to do with update-alternatives and took quite some time and 5+ reboots on each machine and multiple re-attempts to get working (involved purging fglrx and forcing a re-install of libmesa and a couple of others).

I am mentioning this just as the lastest example that cost me at least 5 hours of time to fix.  Some other, non-video-driver related issue cost me multiple hours a month ago.  Indeed, it seems that over the last year, the frequency with which updates either fail outright during update (est. 15% of the time) or require significant amounts of time (est. approaching 35% of the time) has increased greatly.

Thus, in general, it does seem like nearly half the time I update, I'll spend on an average at least an hour dealing with probems.  It did not use to be this way.

I purposely run the latest LTS versions for their stability, which has traditionally been sound.  Over the last six to nine months, I have probably spent at least 100 hours on just these four machines dealing with Ubuntu update problems.

 I'm a senior IT guy who's been administring nearly all major Unix and Linux variantas  for nearly two decades, so I can only imagine the frusturation less experienced users might be experiencing.

I am not mad or angry.

But I am concerned.

It just seems like testing that updates don't break things is much less throrough than in that past.  Often, too, the problems seem involve really simple fixes, but also ones that (a) can be incredibily diffifult to locate the true source of the problem, (b) quite difficult at times to find an acceptable fix, (c) even if the fix(es) are simple, a fix for one person in the forums / launchpad does not work for another person, at least more often than in the past, and (d) seem like they should have never been needed in the first place.

If I were to put a negative spin on it:

It just seems like work on the updates has gotten sloppy.

I realize developing a free and open source operating system is non-trivial, and not just on the technical side. I imagine market forces are pushing Ubuntu to get Mir and Mir-based apps done and out as soon as possible, along with other "one OS for all devices" efforts, which I fully endorse and believe is the key to Canonical and Ubuntu's long-term success.

So I get that there are intense forces in different directions to be balanced here.

My purpose in this post, then, is simple to encourage a bit more oversight, energy, and effort be kept on ensuring that existing releases don't become an utter frustration.  I am at the point of considering dropping Ubuntu for other distributions, but I take time to decide such things, so that won't happen for at least six months.  The last thing Ubuntu wants, I would imagine, is to finally have Mir up and running with plenty of applications and on all many mobile and of course nearly all non-mobile ones, only to find may long-terms users have left because of stability issues and are hesitant to come back for the same reason, or just the time and effort in doing so might be prohibitive (if I leave, I certainly won't be able to come back quickly, due to the time invovled if nothing else).

Thanks for listening,
Doug

---

### Post by howefield on 2014-02-02
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum, where the the intended audience are as unlikely to read it as they are in General Help.

---

### Post by oldos2er on 2014-02-02
If you want to get in touch with the developers, best way is to subscribe to their mailing list: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel)

---

### Post by mastablasta on 2014-02-03
an option would be to enable and use only security updates. those should be safe.

still i agree that having things break is not good. i had similar experience on 13.10 when AMD drivers update went messy and dropped me to CLI. purging and reinstalling worked. btu this is not something ordinary user should be doing (messing with CLI after system update).

---

### Post by buzzingrobot on 2014-02-03
I wonder if potentially problematic updates like video drivers might be partitioned off during an update, much as proprietary drivers are during an install. 

If the updates are not mandatory for security or dependency reasons, splash a notice to the users and make those updates opt-in.

(Mint, of course, takes this approach to the extreme, dividing updates into 5 categories of trustworthiness and, by default, banning the last two.)

It's been some time since an update cobbled things here, especially since I've been on Intel video.  Updates involving Nvidia drivers were sometimes a problem. (Nvidia-xconfig didn't run, more often than not, and I would need to do it manually to prevent rebooting into a black screen.  Maybe there's a parallel gotcha in the AMD world?)

---

### Post by nomenkultur on 2014-02-03
your first mistake was buying amd/ati hardware
your second mistake was doing a kernel update while using a proprietary driver...

 I'm not a 'senior it unix admin for 20 years', I've been dual booting ubuntu for only 2 years and even I know that

---

### Post by mastablasta on 2014-02-04
> **buzzingrobot said:**
> I wonder if potentially problematic updates like video drivers might be partitioned off during an update, much as proprietary drivers are during an install. 

If the updates are not mandatory for security or dependency reasons, splash a notice to the users and make those updates opt-in.

(Mint, of course, takes this approach to the extreme, dividing updates into 5 categories of trustworthiness and, by default, banning the last two.)

It's been some time since an update cobbled things here, especially since I've been on Intel video. Updates involving Nvidia drivers were sometimes a problem. (Nvidia-xconfig didn't run, more often than not, and I would need to do it manually to prevent rebooting into a black screen. Maybe there's a parallel gotcha in the AMD world?)

yes you can. you can load just security updates.

> **nomenkultur said:**
> your first mistake was buying amd/ati hardware
your second mistake was doing a kernel update while using a proprietary driver...

I'm not a 'senior it unix admin for 20 years', I've been dual booting ubuntu for only 2 years and even I know that

dkms should handle this. it is not an issue usually. so far it happened to me only once.

---

### Post by buzzingrobot on 2014-02-04
> **mastablasta said:**
> yes you can. you can load just security updates.


Most non-security updates are going to be non-problematic.  By avoiding them to avoid one or a few that may or may not be problematic, users are doing themselves a disservice. 

This kind of categorization would have to be implemented by Canonical.  Users can't be expected to know about potential update  issues, the purpose of the files being updated, etc.  When you click the 'update' button, you are engaging in an act of trust:  You trust Canonical to alter your system. If the update goes awry, even if it's the user's fault, that trust is broken.

---

### Post by ventrical on 2014-02-06
> **nomenkultur said:**
> your first mistake was buying amd/ati hardware


  I have an ASUS AMD/ATi HD5450 Silent working just fine here. Even older ATi cards have fared well with my installs.

---

