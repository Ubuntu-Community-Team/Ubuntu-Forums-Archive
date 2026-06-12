---
title: "Lack of response to critical issues on launchpad"
date: 2012-06-14
forum: The Cafe
---

### Post by reuben on 2012-06-14
As somebody affected by [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096), I've lost faith in Canonical's process. I fully understand that software ships with bugs, but a) critical bugs (i.e. those which entirely crash Ubuntu, making it unusable) should be fixed as quickly as possible as they come up; and b) Canonical should be dedicating resources to responding to Launchpad tickets (at the least a "we're aware of this" or "we're working on it" would go a long way.) 

This bug has 17 dupes, and 166 affectees. The relevant people in Canonical HAVE to be aware of it. And yet no comment at all, aside from an initial comment from Bryce asking for more details.

What gives, Canonical?

---

### Post by Vaphell on 2012-06-14
canonical is not responsible for nvidia drivers in any way, nvidia is.

---

### Post by reuben on 2012-06-14
Fingerpointing is not the answer here. Canonical ship the "stable version" of the driver. If it's crashing, they should pull it and revert to stable via an update. And at the least they should post workarounds in launchpad tickets.

---

### Post by deadflowr on 2012-06-14
If Canonical were to pull the drivers that affect perhaps a small ,percentage-wise, base of users, it could have serious affects on the larger percentage-wise user base, who have benefited from the newer drivers. Putting all users at that risk is logically unreasonable. (Sorry if my wording seems weird, I'm having a rather off day)

---

### Post by jbyvosges on 2012-06-14
Canonical is not responsible? Other Linux distributions are also affected by this bug?

---

### Post by Mark Phelps on 2012-06-14
Personally, I would disagree with the statement that Canonical is "not responsible" for the quality of stuff they distribute with their product.  IF they aren't, then who is?

But on a practical basis, other than opening a bug report, what are you going to do? Not buy the next version of their product?  Since it's FREE, they're not going to lose any revenue on that front.

Switch to another distro?  Remember all the whining when (1) Unity came out, and (2) Mint got higher numbers on distrowatch than Ubuntu?

Well, Canonical is still there, still cranking out new Ubuntu releases -- and still pushing Unity, harder than ever!

But seriously, lots of other good distros are available for FREE from distrowatch.  You should try some and see if they have the same problem.

---

### Post by Jurjen de Vries on 2012-06-14
> **jbyvosges said:**
> Canonical is not responsible? Other Linux distributions are also affected by this bug?

I am not sure about Canonical responsibility, but the Nvidia bug also affects other Linux distributions.
See [www.nvnews.net/vbulletin/showthread.php?t=176404](www.nvnews.net/vbulletin/showthread.php?t=176404) where the bug is reported to Nvidia, and where Nvidia Employer 'Sandipt' reported that the bug ID is '970240'. Their last response is from April 19th.

---

### Post by Vaphell on 2012-06-14
> Fingerpointing is not the answer here. Canonical ship the "stable version" of the driver. If it's crashing, they should pull it and revert to stable via an update. And at the least they should post workarounds in launchpad tickets.

stable is what nvidia calls stable, not canonical.

What if the problem exists because the code base of 12.04 is too new for the drivers nvidia calls 'latest stable' and there is no way around it? Do you expect Canonical to roll back the whole stack, kernel, X and whatnot?

in that launchpad entry one guy (post #111) claims that drivers from [http://www.nvnews.net/vbulletin/showthread.php?p=2557224](http://www.nvnews.net/vbulletin/showthread.php?p=2557224) fix the problem (beta not stable).

---

### Post by ctg on 2012-06-14
Fingerpointing absolutely is the answer here. Canonical most certainly is responsible for the impression that people get of Ubuntu, and if the impression of 12.04 is that it is unreliable, ugly and a waste of time, then it is up to Canonical to fix that problem or else suffer the consequence of people deserting Ubuntu. Perception is everything. Simply shrugging the shoulders and saying "someone else's problem" is not what a professional software organisation does.

I had been using 10.10 for the last two years with no problems whatsoever. Switching to 12.04 has been a nightmare that has wasted a lot of my time over the last couple of months. Even matters seemingly trivial as scrollbars have been a huge timewaster - those overlay scrollbars ruined my work on a graphics application - every time I was drawing near the side of the screen, the scrollbar would pop up and get in the way of my mouse. Took me ages to find the trick to disable them. 

Something as serious as the desktop crashing, losing hours of work, is something that Canonical should be taking very, very seriously indeed, no matter where the problem actually lies. It is childish just to say "it's nVidia's fault". Fix the damn problem, and grow up.

---

### Post by Vaphell on 2012-06-14
So you compare design choices of in-house desktop environment that can be disabled/uninstalled/have annoying parts removed by the user (have you tried? overlay can be disabled/uninstalled, global menu can be disabled/uninstalled) with the proprietary drivers you have no control of? Canonical can say 'nvidia fix your drivers, pretty please' all they want but when nvidia answers 'we'll do it when we feel like it' that's the end of story. Canonical is no 900lbs gorilla called Microsoft that asks the vendor 'nicely' for drivers 'or else...' and gets them right off the bat with a pretty smile.

If you don't want crashing drivers, go with open source nouveau for a while and wait for nvidia to wake up.

---

### Post by sffvba[e0rt on 2012-06-14
*Thread moved to **The Community Cafe**.*

Not a support request (might even be a recurring theme...)


404
[I]
edit: Oh my 2 cents worth, Linux dev's can only do so much without the assistance of the hardware manufacturers, and if they decide to rather make their own drivers than assist the Linux community what can the Linux community do?  Sure there are the free drivers created by the community but they are sorely lacking because the hardware manufacturers are not giving up information needed to make the hardware work properly... And their own drivers aren't getting the same amount of attention then the drivers for say Windows etc... All Ubuntu can do is give the user the choice of which driver they want to use.

Maybe Canonical can try to do more to drive the free drivers, or maybe they can do more to drive the proprietary drivers to work better... but I doubt it would have much impact as they are not the problem.[/I]

---

### Post by Clint_Thomas on 2012-06-14
I have installed from scratch several different distros all based on the 12.04 LTS and all of them crash with intense video usage back to the login screen.  Oh, and I dont have an Nvidia card.  I have the Intel 945 on board video with 1.5g of dedicated memory.  I finally gave up and went back to 11.10.  I will be switching to LMDE when I purchase my new laptop this month.

Distros tried:

Ubuntu 12.04
Kubuntu 12.04
Xubuntu 12.04
Linux Mint Maya 13 cinnamon and mate (both based on 12.04)

---

### Post by ctg on 2012-06-14
Thanks for proving my point so neatly.

And yes, I did try disabling the overlay scrollbars. The clue was the part where I said "Took me ages to find the trick to disable them", the point being this was not an option that was clearly labelled and easily switched off, I had to do a lot of research to find the solution and then it was a tweak in some config file - hardly a user-friendly approach.

I have been using many flavours of linux and OSS professionally and privately for many years now, so your condescending tone is inappropriate, and symptomatic of the immaturity of the linux space, and Canonical in particular. Like I said, grow up.

---

### Post by Irihapeti on 2012-06-14
I do not get this.

If you have a problem with Canonical, **take it up with Canonical**. Same applies to any other organisation.

---

### Post by cprofitt on 2012-06-14
A couple of points:

1. Canonical is a sponsor of the Ubuntu OS
2. If you did not buy support from Canonical then you can not point a finger at Canonical
3. The issue is affecting other Linux distributions - because the issue is with Nvidia's driver

--- what can you do ---
Try going back to an older driver and install it manually
Try going to a newer driver and install it manually

--- why can't Ubuntu release an update ---
This is a two part answer.

1. It can and does. In fact the driver published with 12.04 is 295.40 and they have published a new updated driver in 295.49
source: [https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/982710](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/982710)

2. Producing an update for a released product is much more difficult -- because it could 'break' other things... and 'break' things that are not broken for others. (it does happen though -- see above)

--- a bit of honesty  ---
You would have the same issues and options if this happened on Windows. On more than one occasion I have had a driver published by MS Update break an installation... I then had to either manually install an older or newer version directly from the vendor.

[Alberto Milone]("https://launchpad.net/%7Ealbertomilone") is fantastic and very responsive. Help him figure out the problem and he will get it fixed if a fix is possible.

--- a final word ---
We understand your pain... but the process is a community process... not a Canonical issue.

---

### Post by zombifier25 on 2012-06-14
So the NVIDIA driver doesn't work and Canonical is to blame? NVIDIA never cared about the drivers on Linux - it's buggy and its performance is terrible. When you install the driver from Additional Drivers, I'm pretty sure you get some warnings like "This driver is closed source", "Canonical is not responsible for bugs", "It all depends on the manufacturer", etc etc...

I don't really care anyway, since Nouveau is way better. Last time I used NVIDIA-provided drivers, everytime I tried to play games on Wine the monitor gave an "Out of Range" error. That did not happen on Nouveau.

---

### Post by josephmills on 2012-06-14
> **cprofitt said:**
> 
2. If you did not buy support from Canonical then you can not point a finger at Canonical


That about sums it all up, 
Support is less then the cost of other operating systems 
and is Great!

---

### Post by seenthelite on 2012-06-15
> **Clint_Thomas said:**
> I have installed from scratch several different distros all based on the 12.04 LTS and all of them crash with intense video usage back to the login screen.  Oh, and I dont have an Nvidia card.  I have the Intel 945 on board video with 1.5g of dedicated memory.  I finally gave up and went back to 11.10.  I will be switching to LMDE when I purchase my new laptop this month.

Distros tried:

Ubuntu 12.04
Kubuntu 12.04
Xubuntu 12.04
Linux Mint Maya 13 cinnamon and mate (both based on 12.04)

I am currently getting freezing, crashing and report messages on 2 Laptops with 12.04 installed. I occasionally boot these and keep them updated to see if anything has improved, not yet maybe one day.
I do not like to be too critical as 12.04 is free.
Fortunately I also have other Linux distros installed on these Laptops. I think that sometimes one just has to try other distros and find one to suit your needs and hardware.

---

### Post by Vaphell on 2012-06-15
> **ctg said:**
> Thanks for proving my point so neatly.

And yes, I did try disabling the overlay scrollbars. The clue was the part where I said "Took me ages to find the trick to disable them", the point being this was not an option that was clearly labelled and easily switched off, I had to do a lot of research to find the solution and then it was a tweak in some config file - hardly a user-friendly approach.

I have been using many flavours of linux and OSS professionally and privately for many years now, so your condescending tone is inappropriate, and symptomatic of the immaturity of the linux space, and Canonical in particular. Like I said, grow up.

Sorry, it's you who is condescending. You are not doing anybody a favor by using ubuntu/linux. The fact of life is that linux is not served on a silver platter and the user is required to do some homework to make sure his experience will be a smooth sailing. Entitlement is a road to disappointment.

Do i like ubuntu unity design choices? hell no, but i sure got more than i paid for and i did my homework. I know what my options and alternatives are (uninstall few packages/modify config files, migrate towards kde, xfce, lxde, ...)


The 'better' is the enemy of the 'good', you don't have to have the latest and greatest if your current setup just works and the new one might not.
Don't go blindly head first if there is a distro upgrade. Distro upgrade means new kernel which means potential problems with proprietary drivers. Kernel vs drivers is an eternal struggle, one would think you'd know that already (years of linux experience).
Have smallish partition dedicated to new releases to see if the hardware compatibility is ok, if the defaults chosen by the distro creators suit your needs and if it's ok to migrate to that from something that is already customized and works.

---

### Post by reuben on 2012-06-15
> If Canonical were to pull the drivers that affect perhaps a small ,percentage-wise, base of users, it could have serious affects on the larger percentage-wise user base, who have benefited from the newer drivers. 

```

if (chipset in [x, y, z]) {
...
} else { 
...
}

```

> But seriously, lots of other good distros are available for FREE from distrowatch. You should try some and see if they have the same problem.

If I had the time I would. Canonical are explicitly aiming to take a significant portion of the desktop market. Last time I checked, Launchpad #1 is still open. Shuttleworth is aiming for "quality".

I settled on Ubuntu 7 years ago because it "just worked" to a greater extent than anything else that was around at the time, and although there have been rocky upgrades since, nothing they've shipped has had such a serious bug (at least on my machine) which they've left unaddressed for so long.

Like I said, I've lost faith in their process. If a bug that makes their default install effectively unusable for hundreds/thousands of users languishes unresponded to in Launchpad for months, where's the focus on quality?

> Fingerpointing absolutely is the answer here. Canonical most certainly is responsible for the impression that people get of Ubuntu

I fully agree. I was responding to Vaphell (evidently of the see no evil school of QA) who said it was nvidia's fault, not Ubuntu's, and that there was nothing they could do about it.

> go with open source nouveau for a while and wait for nvidia to wake up

Tried it. It's not nearly ready.

> If you have a problem with Canonical, take it up with Canonical.

And how do you suggest I do that? I emailed the person this bug is assigned to, and I emailed Mark Shuttleworth. Unsurprisingly no response from either. This forum is about Ubuntu, the commercial (but free) offering from, yes, Canonical. It's absolutely the right place to discuss this issue.

> If you did not buy support from Canonical then you can not point a finger at Canonical

That's inane. Canonical claim to be concerned with _quality_. Something about the entire quality process is clearly broken.

> We understand your pain... but the process is a community process... not a Canonical issue.

Where does the Canonical process stop and the community process begin? Surely Canonical's entire model is to coordinate the process?

> Alberto Milone is fantastic and very responsive. Help him figure out the problem and he will get it fixed if a fix is possible.

That may be, but he hasn't commented on this bug (despite 100+ comments, several people emailing him, and several people commenting in that bug asking for updates from him.)

>  When you install the driver from Additional Drivers, I'm pretty sure you get some warnings like "This driver is closed source", "Canonical is not responsible for bugs", "It all depends on the manufacturer", etc etc...

When you install Ubuntu, a dialog pops up shortly after you log in _recommending_ the Nvidia drivers. The Nvidia drivers are thus made "part of" the Ubuntu brand in all but the most nitpicky of ways.

> Don't go blindly head first if there is a distro upgrade. Distro upgrade means new kernel which means potential problems with proprietary drivers. Kernel vs drivers is an eternal struggle, one would think you'd know that already (years of linux experience).

That's fair. But do Canonical offer 11.10 for download from their site? No. So they are shipping a product that they have to know is broken, in default configuration, for a percentage of users. If the idea was that a release wouldn't be properly tested until it had been unleashed on early adopters (post RC) for several months, why do they a) announce it and b) change the links on their sites (where most new users will find it)? Broken process. And yes, I've been at this (with Ubuntu) for 7 years; I've had my share of distro upgrade issues. Most have been immediately obvious, however; this one is particularly pernicious, as it can be 6 or 12 hours before it shows; the X reset can happen when you're not even using it, so if you leave your computer on overnight it's not even necessarily obvious that anything happened.

Look, the point is not that it sucks that bug was shipped; that's inevitable. The point is that nobody has responded to the Launchpad ticket, despite a large amount of traffic in there, and despite the high severity of the issue. There are workarounds, and that's fine, but if Shuttleworth is serious about quality then there are some fundamental process issues to resolve.

---

### Post by philinux on 2012-06-15
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096)

Comments 106,107 and 108 are telling.

Incidentally I have 12.04 and nVidia 8600GT with no issues.

---

### Post by Paqman on 2012-06-15
> **ctg said:**
> 
And yes, I did try disabling the overlay scrollbars. The clue was the part where I said "Took me ages to find the trick to disable them", the point being this was not an option that was clearly labelled and easily switched off, I had to do a lot of research to find the solution and then it was a tweak in some config file - hardly a user-friendly approach.


You're disabling a signature component of the desktop, it's not supposed to be something you can just switch off any more than you could switch off window decorations or your mouse pointer.

Probably the easiest way to do it is to simply remove the appropriate packages. Takes about 30secs and is a method found on the first page of results when Googling "disable overlay scrollbars".

I don't like overlay scrollbars either, and don't use them. But they are really easy to switch off.

---

### Post by helix_r on 2012-06-15
This is the worst kind of problem to deal with. It is an **intermittent** failure that occurs on **specific models** of hardware when running newer drivers provided by NVidia.

Is there a way to make this intermittent problem reliably reproducible? Anybody who is in a position to do anything about this FIRST needs to be able to reproduce the problem. I am thinking that if there were a script that could run and reproduce the problem with high certainty within a short period that might be tangible enough to get someone interested in a fix. 

I doubt that canonical or nvidia is going to spend any effort to deal with this if there isn't an easy way for them to actually reproduce the problem.

---

### Post by kamiller42 on 2012-06-15
Found this thread through the original issue filed at launchpad.net. I received an update via the Update Manager for the nVidia driver. I've been using for Unity 3D for 4 hours so far with heavy video usage and no forced log offs. It's looking good so far. <fingers crossed>

I'm using the nVidia driver at the x-swat PPA.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by kamiller42 on 2012-06-15
It made it 8 hours before having a hard crash. I won't give up on this version yet as I performed a warm restart after receiving the update. Maybe, just maybe I needed a cold start.

---

### Post by wilee-nilee on 2012-06-15
[COLOR=White].[/COLOR]

---

### Post by kamiller42 on 2012-06-15
That didn't last long. Just logged me. Grrr.... wish someone would fix the bug. Didn't have this problem in 11.10.

---

### Post by Reason NL on 2012-06-16
For all people affected try using 290.10 driver for now.
I've been running this driver for almost a month now and it hasn't crashed on me since (And it did almost certainly within a hour of usage).
It's my daily workstation so I use it a lot.

[https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)
This machine was running perfectly fine before 12.04.
This bugs basically makes it  useless and I was piratically forced to reinstall my machine with a  previous version of Ubuntu.
It isn't reliable enough to work with it and I lost hours of work because of this.
I've also tried using 295.40 and 302.07, both contain the same bug (assuming it's the nvidia driver). Haven't tried any of the newer drivers yet.

 Still baffled that this bug isn't being addressed yet. There are 17  duplicate bug reports and more than 200 people are mentioning being  affected by this bug and still nobody from Canonical, as far I can tell,  is looking into this.
 Besides the trouble it's causing me, regular desktop people are  ditching Ubuntu (and Linux) and give this potential great desktop a bad  reputation which it cannot afford.

You can't expect people who just want a working machine to hack into  there system just because they upgraded to the newest version. Even if  they tried to be save by using a LTS version for the sake of stability.
 The fact that the bug exists within a LTS release is questionable,  but the fact it's not being addressed after a almost 2 months (Even before the  actual release), even for a free OS, is regrettable.
 This really should be top priority not for my sake but the general acceptance of Linux as a great Windows and OS/X alternative.
Even though it might not be something Canonical caused, it's still being blamed on Ubuntu as it's the failing product no matter what's causing it.

Canonical has taken this burden upon them and shouldn't let it slip.

---

### Post by kamiller42 on 2012-06-17
Linus addressed nVidia.
[http://news.cnet.com/8301-1001_3-57454815-92/linus-torvalds-is-livid-directs-middle-digit-at-nvidia/](http://news.cnet.com/8301-1001_3-57454815-92/linus-torvalds-is-livid-directs-middle-digit-at-nvidia/)

---

### Post by smellyman on 2012-06-17
> **kamiller42 said:**
> Linus addressed nVidia.
[http://news.cnet.com/8301-1001_3-57454815-92/linus-torvalds-is-livid-directs-middle-digit-at-nvidia/](http://news.cnet.com/8301-1001_3-57454815-92/linus-torvalds-is-livid-directs-middle-digit-at-nvidia/)
 
bravo!

---

### Post by alphacrucis2 on 2012-06-17
Anyone tried this?

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

New nvidia blob fixed a few issues for me after this latest update.

---

### Post by kamiller42 on 2012-06-18
> **alphacrucis2 said:**
> Anyone tried this?

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

New nvidia blob fixed a few issues for me after this latest update.
Yes, 7 messages ago.
[http://ubuntuforums.org/showpost.php?p=12029357&postcount=24](http://ubuntuforums.org/showpost.php?p=12029357&postcount=24)

---

### Post by Reason NL on 2012-06-19
> **alphacrucis2 said:**
> Anyone tried this?

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

New nvidia blob fixed a few issues for me after this latest update.

I've been using the 302.* beta driver to fix this issue, which did help but still suffered from it.
Instead of within the hour it occured within a day. I'll be waiting till people are using this driver for at least a month without any issues. Can't afford loosing work because of this again.

---

### Post by madjr on 2012-06-19
devs are having discussions about these type of problems:

[http://iloveubuntu.net/ubuntu-developers-discuss-future-graphic-drivers](http://iloveubuntu.net/ubuntu-developers-discuss-future-graphic-drivers)

and yea we can't forget Linus addressing nvidia :)

---

### Post by Reason NL on 2012-06-22
Tested 302.17 for about an hour until it crashed on me again. Back to 290.10 it is.

Download the driver here:

**32Bits**
Driver: [http://launchpadlibrarian.net/90396104/nvidia-current_290.10-0ubuntu2_i386.deb](http://launchpadlibrarian.net/90396104/nvidia-current_290.10-0ubuntu2_i386.deb)
 Runs this command from within the download location: "sudo dpkg -i nvidia-current_290.10-0ubuntu2_i386.deb"

**64Bits**
Driver: [http://launchpadlibrarian.net/90395807/nvidia-current_290.10-0ubuntu2_amd64.deb](http://launchpadlibrarian.net/90395807/nvidia-current_290.10-0ubuntu2_amd64.deb)
  Runs this command from within the download location: "sudo dpkg -i nvidia-current_290.10-0ubuntu2_amd64.deb"


**Note:** Keep in mind to uncheck the nvidia-current in the update manager until this is fixed, it will try to update your driver because a newer one exists resulting in a unstable system again.

---

### Post by blujay on 2012-07-07
I'm afraid Ubuntu's bug handling has left a lot to be desired for years.  I finally began collecting an "Ubuntu Hall of Shame", listing serious bugs that Ubuntu has failed to handle competently.

I think there are a few things that contribute to the problem, in no particular order:

1.  Popularity.  Ubuntu is probably the most widely used distro, so it probably receives more bug reports than other distros.  

2.  Newbie-friendly.  It tends to attract new Linux users more than other distros, and these users are often less experienced in bug reporting, leading to more dupes, less-useful reports, and a lower signal-to-noise ratio.

3.  Poor policies.  Debian, in spite of its inertia, does it right: a bug may languish for years, but it will not be marked 'done' until it's done.  Reporters will not be repeatedly asked to test new versions when no effort has been made to fix the bug in question.  

In contrast, Ubuntu reports are frequently addressed with this "spray and pray" method, hoping that somehow, because of unrelated changes, a bug has coincidentally become fixed.  This frustrates users who competently file useful reports; since no effort was made to fix the bug, their report was a waste of time--and testing new versions would be, also.  When this happens over and over, it feels disrespectful to the reporter and discourages further participation.

4.  Unwise automation.  This doesn't seem to be as bad as it once was, but I have seen some very unhelpful, yet always politically correct, bug-updating bots that needlessly mark bugs Incomplete.  Then if the original reporter doesn't respond in time, the bug expires, regardless of whether even an attempt has been made to fix it, causing the bug to effectively disappear into a useless purgatory of neglected bugs.

Bottom line: Ubuntu is, by volume, a volunteer project.  However, it's also a product, even though it can be had free of charge.  Being a product, there comes a certain expectation of quality, which includes experiences with the vendor, such as interaction with the bug tracker.

Regardless of my preferences about Unity, I'm glad Shuttleworth is leading with vision--he will accomplish far more than a CADT model would in the same amount of time, and make some actual progress.  However, I wish he would hire just one full-time developer to work on nothing but critical bugs in the distribution as a whole, or at least in main.    

Because that's the fifth major problem I see: quite often, there is no one who is responsible for a particular bug.  That's fine if it's just an average bug, but for critical bugs like crashes and data-loss bugs, it just doesn't cut the mustard.

If even one person was actually responsible for critical bugs, that would make a big difference.  Even if he was spread rather thin, for the users, knowing that there was actually a real human being taking responsibility for handling their critically important bug would make an immeasurable difference in their experience and their feelings about Ubuntu.  And inspiring confidence in that way only encourages more volunteer participation and helps the project grow.

In the end, Ubuntu is far better than Windows for my needs and for the average human's daily computing needs.  But I wouldn't be surprised if I return primarily to Debian someday.

---

### Post by buzzingrobot on 2012-07-08
This Nvidia driver problem is a perfect example of an issue that has always affected Linux. I.e., hardware vendors have no financial incentive to ensure that their drivers work with Linux.  And, from their perspective, Linux is a wildly fragmented target.  Should they target drivers for Ubuntu or Fedora?  OpenSuse or Debian?  Which version of Debian?  Etc., etc.

The driver situation today is much, much better than it was even a few years ago. It is only in recent years that most users can have a reasonable expectation that they can install and use a Linux distribution without spending at least several hours chasing down drivers.

Canonical's decision about which Nvidia drivers to offer, particularly in Additional Drivers, isn't clearcut.  If Nvidia releases a buggy driver, should they not offer it?  What if the new driver solves old bugs for more users than are impacted by the new bug? 

Plus, users without problems don't report that fact.  For every user reporting this specific Nvidia bug,  hundreds or thousands might not be affected by it.

Why should kernel developers try to add fixes to cope with, we hope, transitory vendor bugs in closed products?

Users of proprietary drivers are dependent on the vendor for fixes, as Additional Drivers clearly states.

And it could be a lot worse:  Machines with a number of Nvidia cards *will not boot* with any 3.2 or 3.3 series kernel if an attempt is made to load the Nouveau driver. This affects installation CD/DVD's and LIveCD's as well as installed systems. This means that, in an affected machine, any graphical install routine that discovers the presence of an Nvidia card and tries to load Nouveau will crash and lock the machine *before* Grub runs.  I have one of those cards.  Trust me, that's an annoying problem.

The only specific recommendation I can make is that Ubuntu consider flagging, in Additional Drivers and Software Manager, those specific vendor drivers that have triggered some threshold of duplicate and verified bug reports.

---

