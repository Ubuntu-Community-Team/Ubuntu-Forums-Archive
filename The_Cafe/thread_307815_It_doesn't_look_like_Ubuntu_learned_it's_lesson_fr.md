---
title: "It doesn't look like Ubuntu learned it's lesson from the broken xorg update fiasco"
date: 2006-11-27
forum: The Cafe
---

### Post by greggh on 2006-11-27
I was readin this review of 6.10...

[http://www.softwareinreview.com/cms/content/view/59](http://www.softwareinreview.com/cms/content/view/59)

> I'd been evaluating the beta builds of Ubuntu 6.10 before the release, and didn't have much success with them on most of my test machines. That trend continued with the actual release, unfortunately -- on most machines that use ATI graphics chips, 6.10 was unable to boot into the graphical live CD or install from the same no matter what boot options it was passed. The issue ended up being a problem with the X.org video driver for which there was a bug report that the development team apparently ignored for a long period of time. Though it could easily be fixed by changing the default "safe video mode" X.org driver from ati to vesa, as of this writing the fix still has not been implemented. This is not only sloppy development, but sloppy release testing as well, and it's these things that separate the commercial operating systems from the free-of-charge.

Also...

> ATI driver problems aren't limited to the live disc. Though the ThinkPad would boot and install, getting the proprietary ATI driver installed and properly configured was somewhere between a hassle and a headache. Actually the ThinkPad was a walk in the park compared to the desktop test machine with a Radeon X700. First I needed a different version of GCC (4.0) to install it, then had to hack the symlink to /usr/bin/gcc to point to it, then hack the /etc/X11/xorg.conf to change the driver to fglrx and turn off the composite extension, and after all that it still didn't have direct rendering enabled because the kernel module wouldn't load. This isn't how desktop operating systems are supposed to behave, and desktop operating system users shouldn't have to go through this crap just to get their video cards working properly.

And...

> Better release testing. It's a sad state of affairs when almost every operating system I test these days has the same initial post-review recommendation. How could you possibly miss the fact that your operating system installation disc doesn't work with most of the video cards produced by one of the two top video card manufacturers in the world? Do Canonical, Ltd.'s release testers not have a $100 ATI card to test with?

It still looks like there is a serious problem with the developers not testing on a sufficient variety of hardware before they commit code. Come on Mark, you have a Billion $. Pull out your credit card, surf on over to Newegg and order some different video cards, sound cards, motherboards, etc... and have it shipped to the lead Ubuntu developers. These kinds of unecessary silly mistakes are just embarassing.

Ok, rant over, I still love Ubuntu, but there are some crazy, sloppy, and risky development and testing procedures going on that need to change. I would have though this stuff would have been corrected after the broken X update a while ago.

---

### Post by frodon on 2006-11-27
I think there's still a problem with users which don't choose hardware which are compatibles for linux.
Nvidia users almost never get gaphic problems because nvidia develop drivers for linux for a really long time, so this user would better complain to ATI for not providing good drivers and for not giving information to develop good ones.

Seriously no one can expect linux to work out of the box without even taking the time to see what hardware is linux friendly before buying a computer.
As for edgy it was made in 4 month so we can expect it to be at the same level of quality than dapper, i'm sure you will see this thing impoved on feisty fawn.

---

### Post by givré on 2006-11-27
They have learned a lot of this problem :
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

The point you raised have nothing to do with the xorg fiasco.

---

### Post by adam.tropics on 2006-11-27
Since the fellow pointed out he has been trying it for a while, I can't help but think he reviewed using an ATI machine just to make a point!!

In all fairness though, I don't take these reviews that seriously, especally when the reviewer can miss the point on a scale as huge as:
> 
On a final note, I think there is a serious flaw in Canonical Ltd.'s business model. Any company that provides a free product and intends to make money primarily from support services for that product is not financially motivated to offer something that works well. Ubuntu Linux will never be perfect because if it were, Canonical, Ltd. would have no support services to sell. Why spend money on release testing when you can make money telling customers how to fix bugs instead? Perhaps that is what truly separates commercial distros from the free-of-charge ones; with commercial operating systems you pay for the company's best effort at creating a perfect software distribution, not a company's best attempt to create a product that requires paid support services. The better Ubuntu gets with its desktop configuration tools and user documentation, the less money Canonical, Ltd. will make. Doesn't quite make sense, does it?
:-k

---

### Post by greggh on 2006-11-27
> **givré said:**
> The point you raised have nothing to do with the xorg fiasco.

I disagree. When you have a new release that doesn't work with some common and widely used ATI cards, and only requires a simple change to fix, means you probably didn't adequately test it. This is part of the lesson that should have been learned from the previous X problem. Is it exactly the same situation? No. But I'm not going to assume a level of stupidity that wouldn't allow them to extrapolate a lesson to similar situations.

---

### Post by darkninja on 2006-11-27
Edgy was really damn buggy. Seriously, Feisty's current early development state is much more reliable.

Also I am annoyed that they haven't backported a more recent fglrx driver, as the latest in Edgy does not support XVideo on Radeon X1000 hardware.

Hence users have to choose between unofficial repos or waiting for Feisty.

---

### Post by argie on 2006-11-27
Haha, I'll be amazed if some home user buys the support packages.

> I disagree. When you have a new release that doesn't work with some common and widely used ATI cards, and only requires a simple change to fix, means you probably didn't adequately test it. This is part of the lesson that should have been learned from the previous X problem. Is it exactly the same situation? No. But I'm not going to assume a level of stupidity that wouldn't allow them to extrapolate a lesson to similar situations.
Dude, if it's a problem with the "proprietary" driver, you're fighting the wrong enemy.

---

### Post by frodon on 2006-11-27
> **darkninja said:**
> Also I am annoyed that they haven't backported a more recent fglrx driver, as the latest in Edgy does not support XVideo on Radeon X1000 hardware.They are thanks to tseliot's work :
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by greggh on 2006-11-27
> **argie said:**
> Haha, I'll be amazed if some home user buys the support packages.


Dude, it's a problem with the "proprietary" driver. You're fighting the wrong enemy.

Again, I disagree. That's part of the problem that caused the problem I'm pointing out... which is that developers still aren't testing on widely used hardware before they release. It seems they settled on the Russian Roulette model of test on a few varieties and release.

---

### Post by adam.tropics on 2006-11-27
> **greggh said:**
> Again, I disagree. That's part of the problem that caused the problem I'm pointing out... which is that developers still aren't testing on widely used hardware before they release. It seems they settled on the Russian Roulette model of test on a few varieties and release.

Correct me if I am wrong, I may be, but I always assumed the idea was that the devs develop, whilst 'the community' test and report bugs, which the devs can then fix, and continue developing. So maybe the fault lies with all of us.

---

### Post by 23meg on 2006-11-27
The reviewer has no credibility with what he's saying, and basing your assumption in the thread title on his words will not yield a fruitful discussion. If you have some other evidence that Ubuntu hasn't learned from the update disaster, give us that.

---

### Post by maniacmusician on 2006-11-27
this is true, if you think about it. Most of the Ubuntu using populace did not test Edgy during its development phase to help out. A lot of people flocked to try it when the RC's came out, but it's too late to do big things by then.

To be quite frank, it is not the responsibility of the developers to support hardware, it is the responsibility of the hardware manufacturers to support its users. If it is indeed true that "ati" was the fallback driver for ati users instead of vesa on edgy, then that was a silly mistake. vesa is a much safer option. But that can't be translated to "bad hardware support."

---

### Post by givré on 2006-11-27
> **greggh said:**
> I disagree. When you have a new release that doesn't work with some common and widely used ATI cards, and only requires a simple change to fix, means you probably didn't adequately test it. This is part of the lesson that should have been learned from the previous X problem. Is it exactly the same situation? No. But I'm not going to assume a level of stupidity that wouldn't allow them to extrapolate a lesson to similar situations.
Sorry guy, but this is a TOTALY different situation.

The lesson to learn from the xorg fiasco was how to do update a stable release without encounter the risk of regression. And if you read the link i provided, you'll see that the procedure they implemented is rather good.
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

They point raise by jem review (and people should know that jem is probably the most difficult reviewer on the linux planet, you should read some of his reviews) is different. It's rather, "how to get attention of developer on an important bug report", or "how to be sure that a default installation will work on common hardware before we ship a release"

The difference between the two situations is simply the frontier between a development version and a stable version.

---

### Post by greggh on 2006-11-27
> **givré said:**
> The difference between the two situations is simply the frontier between a development version and a stable version.

Sorry guy, but I think you're a little wacky to be calling Ubuntu 6.10 nothing more than a development version.

---

### Post by Zenmind on 2006-11-27
My one cent worth of thoughts.  As someone absolutely new to linux and trying to buy a basic laptop that will work and get tyhhe wifi running too, I am bummed out about this whole issue. Mark and Ubuntu philosophy is that all people throughout the world should be able to load this software and most machines and it should work sweetly!  Things is it doesn't! Much tweaking is needed beyond the beginner's level. I have used computers for more years than many of you have been around, but I am no geek. And this is overwhelming to me. What about people that are in a worst place than me. Whgat about poor people form throughout the world that have what they have and want to use it or that Ubuntu/canonoical wants them to use it. everything has got to work easier and more computers have to be able to laod and have this working right out of the box.  That is what I would call Bug #2 re: Mark's Bug #1 mentioned in the official Ubuntu book.

I am struggling to buy a basic IBM thinkpad to try to get linux Ubuntu to work with wireless. but the issues and the hundreds of hours I have sepent - maybe thousands to learn of all of the isses and problems and HASSLES to may get this to work is a problem...I do not want or need a windows machine - I love macs. hate windows - so if I buy this basic unit to try linux and this is fot nothing I spent $$$ on a windows machine that makes me want to throw up!  That is a waste.

and the mac ubuntu coimmunity is rather a joke if you look at that area of the ubuntu or even kubuntu forum so the mac route seems to not be the best way either...

thanks for your patience in this rap.

---

### Post by frodon on 2006-11-27
So why don't you buy a fully linux compatible laptop instead of spending hours of tweaking ?, example :
[http://www.system76.com/](http://www.system76.com/)

So if you're willing to use linux as first OS you will save your time spending a bit of time searching compatibles laptops before buying. It's what i did before building my computer and i never got any hardware problems.

---

### Post by givré on 2006-11-27
> **greggh said:**
> Sorry guy, but I think you're a little wacky to be calling Ubuntu 6.10 nothing more than a development version.
Did you really read my post ?
The bug point by jem was something that needed to be solve during a developments phase.

I repeat it if it's unclear, 
THIS HAS NOTHING TO DO WITH THE XORG FIASCO.

If you want to know what they learn from this problem, read [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) instead of trolling.

If you are confuse by stable and developpement version, i can't help you more.

---

### Post by drphilngood on 2006-11-27
It´s not Ubuntu´s developer´s fault, IMO.  I´ve seen ATI´s Windows drivers make grown men cry, too.  Furthermore, most people I´ve seen know this when they buy them and swear every time that this ATI purchase will be their last.  Subsequently, I believe that much of the problems are caused by people with ATI GPUs who push the eye-candy envelope before they even get a stable system to start with but, I digress.
WE can only hope that DAAMIT(AMD-ATI) will finally work toward improving their Linux drivers.  Thus, developers will no longer have to try to ¨make a silk purse out of a sow´s ear.¨

---

### Post by greggh on 2006-11-27
> **givré said:**
> Did you really read my post ?
The bug point by jem was something that needed to be solve during a developments phase.

I repeat it if it's unclear, 
THIS HAS NOTHING TO DO WITH THE XORG FIASCO.

If you want to know what they learn from this problem, read [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) instead of trolling.

If you are confuse by stable and developpement version, i can't help you more.

I did read your post and I'm not trolling. You think this has nothing to do with the xorg fiasco and I think it has alot to do with it. We disagree.

By the way Ubuntu 6.10 IS a stable supported release (not a development release), it's just not an LTS (long term support) release. I think you are the one who's confused.

---

### Post by Zenmind on 2006-11-27
because system 76 sucks!

and all of the other ones you seem to have to beg them to sell you one they have such an arrogant attitude!  That is why! and I can save $3400-500 too for a better system....belive it or not - and I have done my howmework. But also not knowing what you know I am at a disadvantage to unbderstand a lot of what i read!

you still did not address the main point of the worldwide userfirendliness of the ubuntu OS that Mark and canonical preach about.  But that is Ok.

I won't bug you anymore and I am sorry I posted my honest feedback and thoughts.

I was not trying to start sosmething just comment so that maybe the higher ups will understand one of the major issues that still face new users and ubuntu and other linux distros.

sorry.... next time I will remain silent and pass the thread!

---

### Post by greggh on 2006-11-27
> **Zenmind said:**
> sorry.... next time I will remain silent and pass the thread!

Nahhh... don't be so sensitive. The forums are here so you can speak your mind. Keep posting.

---

### Post by frodon on 2006-11-27
Keep in mind that edgy was developped in 4 month and is the beginning of a new cycle which will ends by another LTS version. Again you can't expect too much from edgy even if official release means rock solid in your mind.

I can easily understand the frustration of some users after dapper which is a damn rock solid version but that don't mean there's a problem. If you think about the whole process of creating a LTS version you will see that releases like edgy are an inescapable step.

---

### Post by givré on 2006-11-27
> **greggh said:**
> I did read your post and I'm not trolling. You think this has nothing to do with the xorg fiasco and I think it has alot to do with it. We disagree.

By the way Ubuntu 6.10 IS a stable supported release (not a development release), it's just not an LTS (long term support) release. I think you are the one who's confused.
Ok, let it make it clear.

Testing procedures for a development version and for the upgrade of packages for a stable release are totally different, and should be taken differently.

What they learn of the xorg fiasco is how to upgrade package in a stable relase without regressions.

What they should learn of the jem's point should be more, how to be sure that that we ship a stable release that can run rather well on a majority of hardware. And this is something that is pretty difficult to do.

It's not a matter of "i think, you think not, we disagree", it's just two different points.

---

### Post by greggh on 2006-11-27
> **frodon said:**
> Keep in mind that edgy was developped in 4 month and is the beginning of a new cycle which will ends by another LTS version. Again you can't expect too much from edgy even if official release means rock solid in your mind.

I can easily understand the frustration of some users after dapper which is a damn rock solid version but that don't mean there's a problem. If you think about the whole process of creating a LTS version you will see that release like edgy are an inescapable step.

For the most part I actually agree with what you are saying. It's just that some of the problems seem to be related to not having a well crafted testing procedure before release. I'm not expecting it to catch everything, but it still seems that there are problems in this process that still need to be fixed. Ubuntu is my favorite distro and I'm just hoping to see it get better.

---

### Post by doobit on 2006-11-27
> **adam.tropics said:**
> Correct me if I am wrong, I may be, but I always assumed the idea was that the devs develop, whilst 'the community' test and report bugs, which the devs can then fix, and continue developing. So maybe the fault lies with all of us.

I agree with this. 
Developers can not be expected to have every piece of equipment and test it all by themselves. Certainly the user base for Ubuntu is large enough that we can all download a testing phase live CD and run it on our machines to see if it works, and report the problems. That way  at least all of the major hardware configurations are tested.

---

### Post by frodon on 2006-11-27
> **greggh said:**
> For the most part I actually agree with what you are saying. It's just that some of the problems seem to be related to not having a well crafted testing procedure before release. I'm not expecting it to catch everything, but it still seems that there are problems in this process that still need to be fixed. Ubuntu is my favorite distro and I'm just hoping to see it get better.I understand, it's sure that edgy don't have the same level of quality and some bugs were missed because of the lack of time, dapper was made in 7 month so i think we can easily understand why it is that stable and with a really good harware support.

Thanks to edgy, most of the main bugs introduced by many new features, kernel, apps will be reported and i'm sure you will be more than happy to see how this will be useful for feisty fawn.

---

### Post by spockrock on 2006-11-27
I don't understand why people keep saying edgy is unstable......or buggy... the few bugs I ran into while using the betas were reported and fixed.  The only bug I have right now is beagle is a hog with my cpu, so I just turned it off....

---

### Post by tageiru on 2006-11-27
> **greggh said:**
> I disagree. When you have a new release that doesn't work with some common and widely used ATI cards, and only requires a simple change to fix, means you probably didn't adequately test it. This is part of the lesson that should have been learned from the previous X problem. Is it exactly the same situation? No. But I'm not going to assume a level of stupidity that wouldn't allow them to extrapolate a lesson to similar situations.

What is this "simple fix"? I have spent some time investigating this issue and there is no "simple fix".

I also disagree with you on your trivialization of the bug, it does not hit every ATI user, it seems to depend on a lot of factors and therefor easy to miss in QA. This bug is not restricted to Ubuntu, I have been able to reproduce it on both Debian and Gentoo.

---

### Post by drphilngood on 2006-11-27
> **spockrock said:**
> I don't understand why people keep saying edgy is unstable......or buggy... the few bugs I ran into while using the betas were reported and fixed.
++
The only thing I had problems with was Firefox so I switched to Iceweasel.

> **spockrock said:**
> The only bug I have right now is beagle is a hog with my cpu, so I just turned it off....
I thought it was in Dapper, too; thus I haven´t even bothered with it in edgy.

---

### Post by spockrock on 2006-11-27
> **drphilngood said:**
> ++
The only thing I had problems with was Firefox so I switched to Iceweasel.


I thought it was in Dapper, too; thus I haven´t even bothered with it in edgy.

ummm it very well could of but funny thing is it never happened to me in dapper.... so I am not all too sure, but in edgy beagle will randomly just all of a sudden use up one of my cores or runs a single cpu at 100%.....

---

### Post by drphilngood on 2006-11-27
> **spockrock said:**
> ummm it very well could of but funny thing is it never happened to me in dapper.... so I am not all too sure, but in edgy beagle will randomly just all of a sudden use up one of my cores or runs a single cpu at 100%.....
I experienced the same behavior in dapper.  CPU usage would skyrocket whenever beagle started indexing my drives at, what seemed to me to be, random times.

---

### Post by givré on 2006-11-27
> **spockrock said:**
> ummm it very well could of but funny thing is it never happened to me in dapper.... so I am not all too sure, but in edgy beagle will randomly just all of a sudden use up one of my cores or runs a single cpu at 100%.....
That's just because this is not the same beagle version. For exemple, feisty one (the latest) react quite differently.

---

