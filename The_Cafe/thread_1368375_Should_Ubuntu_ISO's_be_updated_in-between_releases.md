---
title: "Should Ubuntu ISO's be updated in-between releases?"
date: 2009-12-30
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-30
I was thinking. Whether you agree with this policy or not, the reason why Ubuntu is designed to fit onto a single CD instead of a DVD like almost every other modern OS is so that people living in areas where broadband Internet connections aren't the norm can more easily download the ISO file and use the OS.

If this is the goal, wouldn't it make more sense to periodically update the ISO images between the standard 6 month release cycle? Say you have dialup and just downloaded Ubuntu a month before the newest stable release is going to be released. You just spend a large chunk of time downloading the ISO image with outdated software. Only to be faced with "you have 100,000,000 updates waiting to be installed" the first time you boot up the system. So the person just spent all that time and bandwidth downloading all of the software package that come with Ubuntu only to have to re-download a whole bunch of them all over again. Seems pretty redundant.

Wouldn't it make more sense to have weekly or monthly builds with all of the updates (or at the very least, the security updates) pre-built into the ISO? It would even benefit people with broadband Internet because they would be able to get the OS up and running a little faster. I doubt it would take very much effort to implement something like this, if could probably even be automated.

---

### Post by FuturePilot on 2009-12-30
They *do* do that for the LTS releases. It doesn't seem too practical for the standard releases though.

---

### Post by ugm6hr on 2009-12-30
The problem is:

1. Updating mirrors worldwide with the current iso.

2. Torrents would be even messier.

LTS iso's are updated every 6 months for exactly the reason you give.  What's the right frequency?  Who knows...

---

### Post by SuperSonic4 on 2009-12-30
No, I don't think it goes with the ubuntu way of updating to be honest. It is well known that ubuntu updates every 6 months and if you download a week before a massive upgrade you've only yourself to blame as releases are publicised well in advance

---

### Post by Roasted on 2009-12-30
It'd be nice, but not overly practical.

I say no because updating all of the mirrors, as mentioned above, would integrate a nightmare.

However, I say yes because the default kernel in Karmic seems to hate multiple hard drive systems. I know some people had luck with this, but a lot of people couldn't install Karmic due to it being problematic. After booting up GParted LiveCD (the version using the Karmic kernel) I had the same issue.

Thing is, this won't change. I can't get Karmic to play nice on my rig. I suppose I could rip the drives out but the main, install Karmic, update the kernel, and gamble on it working then, but eff that. If the ISO's were updated, I'd have a chance at running Karmic on my main rig.

But anyway, it's not a big deal to me since Jaunty was a real solid release. 

But I really wouldn't think this would be practical in terms of the amount of time and man power needed to refresh the ISO images on the mirrors around the world. It would be a painful process, because then you know people would be complaining that they got an old image off of a mirror that wasn't updated yet, etc.

---

### Post by Shibblet on 2009-12-30
I would say "Yes." But only if there is an actual problem with the loading of the ISO.

My MSI Wind U100 wouldn't load the Ubuntu NBR ISO, at all.  Hung at a black screen.  So, after the fixes are in place, it'd be nice to have a functioning ISO.

---

### Post by blur xc on 2009-12-30
What about known bugs in the current iso's installer?  I had a problem w/ my Dell Mini 10's braodcom wifi deal- I googled about and found a simple solution, the drivers were on the live usb, but the installer had a known bug that improperly identified my wifi hardware and failed to install the proper drivers. Imo, the iso should be fixed so the next time someone dowloads it and tries to install it on a dell mini 10 doesn't have the same problem. 

BM

---

### Post by blueshiftoverwatch on 2009-12-30
> **ugm6hr said:**
> The problem is:

1. Updating mirrors worldwide with the current iso.

2. Torrents would be even messier.
I hadn't thought of that.
> **SuperSonic4 said:**
> It is well known that ubuntu updates every 6 months and if you download a week before a massive upgrade you've only yourself to blame as releases are publicised well in advance
A person might need to have an OS in their computer a week before the newest release and waiting that extra week to acquire the new version might not be practical.

---

### Post by wilee-nilee on 2009-12-30
You can get daily builds usually until the build for the next release is put on line.

---

### Post by Shibblet on 2009-12-30
> **blueshiftoverwatch said:**
> A person might need to have an OS in their computer a week before the newest release and waiting that extra week to acquire the new version might not be practical.

Besides, you have to release the product at some point.  ;)

The more I think about this question... "Should Ubuntu ISO's be updated in-between releases"  The more I start thinking the answer to that is a rolling release distro, like Arch.

---

### Post by autonomy on 2009-12-30
> **blueshiftoverwatch said:**
> Should Ubuntu ISO's be updated in-between releases?No, but they should come as a netinstall option in addition to the current ISOs. That would shorten the download and post-installation update time.

---

### Post by wilee-nilee on 2009-12-30
You can always install the minimal which will install the latest builds and install what you want on top of that.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by autonomy on 2009-12-30
> **wilee-nilee said:**
> You can always install the minimal which will install the latest builds and install what you want on top of that.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)thanks

---

### Post by ctrlmd on 2009-12-30
bugs,security updates yeah

---

### Post by SuperSonic4 on 2009-12-31
> **Shibblet said:**
> Besides, you have to release the product at some point.  ;)

The more I think about this question... "Should Ubuntu ISO's be updated in-between releases"  The more I start thinking the answer to that is a rolling release distro, like Arch.

I thought along those same lines, to borrow a concept from maths it's like approaching a limit to infinity of *(1+[1/n])^n* which tends to *e* - the more frequently they're released the closer it gets to being a rolling release distro - I like rolling release (heck, I use SVN and git to get daily updates on my favourite programs) but I don't think it is right for ubuntu.

> 
A person might need to have an OS in their computer a week before the newest release and waiting that extra week to acquire the new version might not be practical.

Perhaps but releasing an ISO a week or two before a release would be pointless, if they wanted an OS for that week it would be more efficient to get the RC of the new version and simply use update manager to update when the time comes although I admit that may be confusing for a new user.

---

### Post by hellion0 on 2009-12-31
Leave it as it is. Maybe, *maybe* in the case that a final gets released that has a fatal flaw in a non-trivial number of cases, should the ISO be pushed back out with a fix, but I imagine they wouldn't let that happen.

---

### Post by ratcheer on 2009-12-31
Not just "No", but "Hell No!". Multiple different CD's of the same "release" would be chaos.

Tim

---

### Post by Gizenshya on 2009-12-31
> **ugm6hr said:**
> The problem is:

1. Updating mirrors worldwide with the current iso.

2. Torrents would be even messier.

LTS iso's are updated every 6 months for exactly the reason you give.  What's the right frequency?  Who knows...

My main problem with the idea is the mirrors as well, but a little different.  I'd consider it a 3rd reason.

3.  With updated releases, people would download the ISO's far more often, squeezing bandwidth.

There would be many people, for good reason, who would want to keep the newest ISO version handy for installs.  I bet a monthly revamp would cause the median mirrow bandwidth useage to double.

So it would be nice, but not at all practical.

However...

I think something like a small update patch ISO released every month or so would be practical and nice.

This would be great for updating multiple systems with little bandwidth, and for system installs in the field.

The patch ISO would be like 9.04.9.05, 9.04.9.06, 9.04.9.07, ...  9.04.10.01, etc., until the end of support for that release.  Year and month of distro release, then year and month of patch release.  Patch ISO's would probably start off being several MB, and I doubt they would get more than 100 mb at end of support.

I think the best way to do that would be to make the patches replace the previous one.  There might be reasons to keep the later versions, though, for rolling back if need be.

I think patch ISO's (some iteration) would be a best of both worlds approach.  They would take some dev time away from newer releases, though.  But the mechanisms for updating through repositories are already there, and any bandwidth increases would be minimal (because the updates will be downloaded immediately after install anyway).  It would save a lot of time, and may actually decrease bandwidth useage because the Disk can be used in multiple computers without each needing to download the patches through synaptic.

It also saves downloading the same thing over and over, as one would with a complete rebuild.  And 2, the original release CD's would still be used throughout the release's support cycle, eliminating that confusion and waste.

PS:  It might also be possible to make the patches very small in tar.gz files or whatever, instead of ISO.  And then just add something to synaptic to update from patch, so it searches there.  That way you could have 100 mb in patches in a very small file that would save bandwidth and increase availability for lower-bandwidth users.  I don't know much about this, though, and it might not actually make any sense lol ... but I'm sure someone here can comment :)

PPS:  I've wished for something like this for a while.  Sometimes I have access to fast internet and I would like to download the patches, but I can't because they are all individual and scattered around.  And I would have to know the version numbers that I have for them ALL, and download them all, and pray that I didn't need any new dependencies, and all sorts of other crap.  It just isn't practical to download patches and updates without a decent internet connection on the computer.  And I hardly have that.  Mine hasn't been updated in months.

And 2.  I'm stuck with one install atm.  It is a nightmare to backup or reinstall now, because I don't have a blazing internet connection.  I have all the patches as of a fe wmonths ago.. but there isn't a way for me to transfer them to a new system if I want to refresh my install.  I would very much like to, as I have half-installed things and other stuff that I couldn't get working right.  But I'd have to download it all again, and it just can't happen.

If there were a patch ISO or patch file regularly released, that would make it practical for my to do a fresh install, or another install on friends' computers without blazing internet.  I'm sure I'm not alone.

Because, lets face it, there are two options now, nd they aren't sufficient.

1.  Wait for up to 6 months to download the next release, and pray every aspect about it is better than your current one.  Then you'll only be up to 6 months behind at any time.

And 2.  Have the time and bandwidth to download many MB of files with every install, from scratch.

I hate to say it, but this is something that Microsoft actually has on Ubuntu, hands down.  They have Service Packs.  You can update online, or slip in a disk with a service pack on it, and use it however many times you want.  It's perfectly portable and practical.  Yeah, they are slow as Christmas and inconsistent with everything, but the idea and followthrough is nice.

---

### Post by Dark Aspect on 2009-12-31
I hate to say it but if your only have dial-up, windows is probably going to be a much better choice than ***any*** other Linux operating system. Lets face it, Linux partially requires a broadband connection.

If you disagree than you probably have never attempted to use Linux with dial-up, its just not worth the trouble.

---

### Post by ssam on 2009-12-31
right now should ubuntu devs be fixing remaining issues in karmic or working on lucid so it has less issues when it is released? if ubuntu had more manpower (your donations pay for developers) maybe both tasks could be done adequately.

there is already the infrastructure to to build daily CDs for the development version. so a couple of extra point releases would be possible. would be handy to have fresher CDs to install from.

---

### Post by Shibblet on 2009-12-31
> **SuperSonic4 said:**
> I thought along those same lines, to borrow a concept from maths it's like approaching a limit to infinity of *(1+[1/n])^n* which tends to *e* - the more frequently they're released the closer it gets to being a rolling release distro - I like rolling release (heck, I use SVN and git to get daily updates on my favourite programs) but I don't think it is right for ubuntu.
Did you just come up with a mathematical formula to predict what is right for Ubuntu?

You're my new hero.

> **SuperSonic4 said:**
> Perhaps but releasing an ISO a week or two before a release would be pointless, if they wanted an OS for that week it would be more efficient to get the RC of the new version and simply use update manager to update when the time comes although I admit that may be confusing for a new user.

Well, there already is the Release Candidate ISO available.  But for releases like Karmic that have so many problems, going back and re-releasing an ISO for those who can't even install it is a good idea.

---

