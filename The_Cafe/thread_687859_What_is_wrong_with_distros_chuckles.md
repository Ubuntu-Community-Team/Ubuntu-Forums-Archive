---
title: "What is wrong with distros? *chuckles*"
date: 2008-02-04
forum: The Cafe
---

### Post by Seven of Cups on 2008-02-04
OK.  I didn't think this was an appropriate post for the actual support pages... so I picked you folks to pose this to.

I am very happy with Ubuntu, don't get me wrong.  But with trying to get Ubuntu to work with my new Dell Inspiron 1525, I ran into some issues with trying to get the Compiz to work.

You folks at Canonical did a great job getting the newest Gutsy I downloaded to actually detect and configure my Marvell Yukon ethernet on install.  But since I really REALLY like the eyecandy of Compiz I got very disappointed in the dearth of easy access to get it to work.  After doing what I could (and several reinstalls afterwards) the less complicated hints and procedures on the web just didn't work.

I bit the bullet and decided to try out other distros.

Suse...  no go.  Wouldn't configure for the ethernet, and with the interface I didn't want the install to continue.  If I can't update and access the repositories online, it's kinda useless.

Debian?  Text mode installation?  When it wouldn't find my Marvell, I gave it the old Shutdown and reboot and didn't look at that disk again.  So I have no clue as to whether Compiz would work.

But then I tried Mandriva....

Compiz was working from the moment I rebooted into the installed OS!  Perfectly!  No check boxes, nothing.  Only problem was (again)  No drivers for Marvell.

I wept.

Now with what I used to think I understood about Open Source, and the willingness to learn from th success of other distros?  I wonder why I can't have both?  Why can't Ubuntu figure out what Mandriva did right with Compiz Fusion?  ANd why can't Mandriva/OpenSuse,and the others figure out what Ubuntu/Canonical did to get the proper drivers for a new laptop (Even is it isn't the neates/spiffiest/hottest laptop Dell makes?)

THis is more a rhetorical question than anything...  just making the point that I had to spend a lot of bandwidth and time reinstalling and reinstalling and reinstalling.

For now I am of the opinion that sooner or later one of the Ubuntu experts will do a Gutsy-themed tute to get compiz fusion functioning in Ubuntu before someone like Mandriva will bother with an internal Ethernet card.  So I am back with two ubuntu boxes and one xp box.

I just wish that there was a LITTLE more uniformity in the BASICS... and leave the individuality to the interactive portions of the OS Distros.



Debian?  Again, no joy

---

### Post by AdamWill on 2008-02-04
Well, we do. All distros take patches and code and things from each other all the time, and we all frequently work together "upstream". There are always going to be differences, though. Sometimes this is as simple as something one distro notices and another doesn't.

From Mandriva's side, we can certainly work to make sure your network card works in future editions. Can you give the PCI ID (lspci -n can give you this; there may be an easier way in Ubuntu, but I don't know about it) and what driver Ubuntu uses for it? (It will be listed in the output of 'lsmod' as root, if you can't tell which of these is the network driver, just post the whole output and I'll figure it out). Then I can check if the driver will be in Mandriva 2008 Spring and later.

We don't do anything *fantastically* complicated for Compiz. We really just have a few scripts that let you turn it on and off, and a bit of detection as to whether the current graphics card driver should support it or not. I could maybe hazard a couple of guesses at what happened if you say what graphics card the system has, though.

---

### Post by fwojciec on 2008-02-04
Commercial OS user attitude -- complain that things don't work as they should.
FOSS user attitude -- identify the problem and either fix it yourself or report a bug to the appropriate bug tracker and help developers fix it by providing info and testing patches (see post above).

---

### Post by Seven of Cups on 2008-02-04
[COLOR="Red"]Commercial OS user attitude -- complain that things don't work as they should.
FOSS user attitude -- identify the problem and either fix it yourself or report a bug to the appropriate bug tracker and help developers fix it by providing info and testing patches (see post above[/COLOR]

First, to the individual with the less than helpful response...

'Leet Forum poster attitude -- Comment snarkily about any posting that reveals a poster's utter ignorance about the Techno-Arcana hoarded by the Leet User over the years.

The Actual Real-world Helpful Forum poster attitude -- Even when told that help was unneccessary, the Helpful Poster STILL offers assistance, advice and info.

Read Replies above to spot the differences, 'Leet-chum.
In the words of the Wyld Stallyns "Be excellent to each other!" :guitar:


Now, as to the good samaritan, I don't want to turn this into a request/support thread...  Especially for a different Distro.  I did post here just to get something off my chest, and to actually learn whether there IS-cross pollination going on between distros.

I will watch to see if there are developments in the Compiz Fusion compatibility issues with Ubuntu...

If nothing is forthcoming, I can always go into the Mandriva forums and post a support question there.  Thank you very much for the offer, my friend!:)

---

### Post by LaRoza on 2008-02-04
> **Seven of Cups said:**
> 
Now, as to the good samaritan, I don't want to turn this into a request/support thread...  Especially for a different Distro.  I did post here just to get something off my chest, and to actually learn whether there IS-cross pollination going on between distros.

If nothing is forthcoming, I can always go into the Mandriva forums and post a support question there.  Thank you very much for the offer, my friend!:)

There is nothing wrong with asking for assistance with another distro, use the "Other OS Talk" forum.

Almost everything is shared, but not everything comes with every distro, so each distro has their differences out of the box.

---

### Post by Peyton on 2008-02-04
[http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36](http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36)

Have you tried that?

---

### Post by gn2 on 2008-02-04
Why not just uninstall Compiz and manually install Beryl and Emerald instead?

They're still available on the Beryl Project website.

Don't like any ready made distro? 

Simple answer: create your own, there's nothing stopping you.

---

### Post by xArv3nx on 2008-02-04
You DID install the proprietary graphics driver, right?

CF is only activated AFTER you install those drivers through the restricted driver manager.

---

### Post by Seven of Cups on 2008-02-04
> **LaRoza said:**
> 
Almost everything is shared, but not everything comes with every distro, so each distro has their differences out of the box.

Ahhh THERE is the "Quote thing-a-ma-bobbie"  :)

It is a relief to hear that.  It is so easy for some to slip into the "be the better Distro" mindset so that they all go in directions that leave folks more confused by all the options.  As you saw from the tone of my post.  I was seriously getting that idea.

For myself, the concern is that even with my limitted knowledge, there is still a sense from my non-computer savvy acquaintances that I am still a bona-fide techno-savant.  Even though I can do some basic things to get most stuff working in Linux, there is still a lot of arcana that needs to be learned to wrest the most out of the OS.

This laptop is going to work with me.  If I have all the bells and whistles working seamlessly, I can get some folks to think outside the Gates/Jobs boxes like they do.

But to actually get Linux into the mainstream, Hardware detection and drivers will need to be more uniform/automatic, I think.  Don't get me wrong...  I remember first trying out Linux years and years ago... Windows 98 was still fairly new...  and the leaps and bounds since then have been astounding to me.  But if it is problematic for folks to get functioning... *shrugs*  Linux will still be a niche to the vast majority of potential users.

But then... that would mean the HARDWARE makers really need to get on board, no? :lolflag:

---

### Post by pieisgood4589 on 2008-02-04
MEPIS. Install compiz from synaptics. 'Nuff said.

---

### Post by Seven of Cups on 2008-02-04
As for the porpriaetary drivers, installation.. that was what surprised me so much about Mandriva...  That I didn't have to jump through the Restricted Manager hoop to get the cube working from first bootup.  I know there are legal issues, and each distro publisher jumps through several hoops to get things legal "enough" to satisfy their individual risks..  Buut Mandriva got my Intel onboard graphics ships drivered and cooperating at install.  Ubuntu seems to need the intel drivers installed manually.

---

### Post by pieisgood4589 on 2008-02-04
> **Seven of Cups said:**
> As for the porpriaetary drivers, installation.. that was what surprised me so much about Mandriva...  That I didn't have to jump through the Restricted Manager hoop to get the cube working from first bootup.  I know there are legal issues, and each distro publisher jumps through several hoops to get things legal "enough" to satisfy their individual risks..  Buut Mandriva got my Intel onboard graphics ships drivered and cooperating at install.  Ubuntu seems to need the intel drivers installed manually.

MEPIS is even better. The driver support is AMAZING.

---

### Post by Seven of Cups on 2008-02-04
> **gn2 said:**
> Why not just uninstall Compiz and manually install Beryl and Emerald instead?

They're still available on the Beryl Project website.

Don't like any ready made distro? 

Simple answer: create your own, there's nothing stopping you.

Oh yes there is... *snickers*  it's called "Ig-no-rance"...  Although I am still human enough that Ignorance NEVER stops me from thinking I could run the world better than those more knowledgeable than I  :popcorn:

I may just try the Manual installation thing though.  *scratches head and ponders*

---

### Post by Seven of Cups on 2008-02-04
ugh.  Spelling mistakes are getting worse.  Gonna go to bed, friends...  Thanks for the input and discussion.  Night to ya all!

---

### Post by AdamWill on 2008-02-05
There's no legal issues at all with Intel graphics card drivers. There's one driver for all current Intel graphics cards ('intel'), and it's fully open source and part of the X.org project. Both X developers and Intel staff contribute to it.

What I'd hazard as a guess is that, if you were using recent Ubuntu betas, you got version 2.2.0 of the driver. The thing about 2.2.0 is that it's crap. I had tons of problems with it, and I saw others report quite a lot of problems too. Mandriva 2008, as it came out last year, has a slightly older version of the driver, 2.1.3. This version works rather better for most people. So I'd *guess* that may be the source of your problem.

Or, just some kind of Ubuntu idiosyncracy relating to Compiz; I wouldn't know about that.

But there shouldn't be any real big difference in the driver in use, only a version difference if anything.

it'd be interesting to see what happened if you tried a recent Mandriva beta. These use version 2.2.0 of the driver too, so it's possible you'd have a problem there as well.

The good news is that a newer version of the driver will be out before either Ubuntu or Mandriva release a new stable version of our distros, so this shouldn't be a problem.

As far as other graphics card drivers go, there are no legal problems per se with including them in distributions. The two major proprietary drivers - NVIDIA and ATI - are explicitly licensed in such a way that distributors can integrate them if they choose to.

However, Ubuntu have a policy of not allowing any non-free software in their release discs, so they don't include these drivers. It's not that it would be illegal for them to include it; they just choose not to, on the basis of Free Software principles.

At Mandriva, we have one edition - Free - which follows the same principles; it contains no non-free software. However, we also have editions - One and Powerpack - which include some non-free software that we can legally bundle. It's not a legal issue, more of a philosophical one.

On the general topic of cross-pollination, what I can say from my point of view is that when I'm working on packaging something in Mandriva and I come across a bug, the first thing I do is look for a fix for it upstream. Then I look for a fix in Fedora. Then I look for a fix for it in ALT or PLD. Then I look in OpenSUSE, then in Gentoo, then in Debian, then in Ubuntu.

If I find a fix in any of these, I check it out, then integrate it into our package, with appropriate credits to the distro / upstream coder.

Only if I can't find a fix in any of these do I (try and) write one of my own.

The reason for the ordering is simply that that's the order of closeness to Mandriva - Fedora is far more similar to MDV than Ubuntu is. Also, due to the way Debian and Ubuntu packages are generally built, isolating patches from them is a tremendous pain, though there is an alternative system for .deb packaging which some maintainers are starting to adopt which makes it a lot easier.

Also, as I hinted at earlier, distro maintainers are often involved in upstream development of major components (like X.org, HAL, GNOME, KDE, kernel, all that good stuff), so we all work together in that kind of forum to come up with ways to do as many things as possible in a way that works across, and benefits, all distributions.

---

### Post by lespaul_rentals on 2008-02-05
> **Seven of Cups said:**
> Why can't Ubuntu figure out what Mandriva did right with Compiz Fusion?

I hate Compiz-fusion, it slows my computer down and it's annoying.  I use Fluxbox or Kwin, without compositing window managers that add unneccesary eye-candy.  If I really have to use something like that, I use Beryl, I like it a lot better (yeah yeah, I know Compiz-fusion has the same features).  But that's only if I take my laptop to a LAN party or something.  That's why I love Kubuntu 7.04.  Doesn't throw a bunch of applications I will never use on my computer with the default install, runs well, and doesn't have anything like Compiz-fusion installed by default.

---

### Post by Seven of Cups on 2008-02-07
Back folks...  I do thank all for the constructive feedback... as well as the much needed info on the way things do work.

I have looked over the various suggestions, and am looking forward to trying some of them out over my upcoming vacation... (Why go someplace exptic when I can take a trip into linux land? :) )

While I may have confused the "Policy" with "Legal" issues, it still remained at it was at the decisions of Canonical that initially restricted my Eye-candy Joy.  And I MUST note that I am not so superficial as to turn away from a distro merely on the basis of Eye-candy.  To date I have had ZERO problem with the distro from a functional and ease of use standpoint.

I have very little doubt that sooner or later there will be a more permanent solution.

And for those who are curious, the two problematic pieces of hardware in my laptop are the Intel Graphics card (I believe it was called the 965 family (???  Not sure, I edon'[t have the time to boot up and look) as well as the aforementioned Marvell Yukon ethernet.

I saw the downloadable linux driver... but from what I saw, I need to recompile the kernal.  Since ubuntu did that with gutsy already, I think I am gonna refrain from taking that dive into the Deep End of Linux. *winks*

At least for now...

I will, however give Mepis a try.  My last attempt to get the Intel Driver in ubuntu ended up breaking my configuration slightly.  Since I have to reinstall again...(and I am becoming a wizard at reinstalling.)  I'll take a look at Mepis just from curiosity.

Thanks bunches, folks!

---

### Post by k2t0f12d on 2008-02-07
> **Seven of Cups said:**
> Why can't Ubuntu figure out what Mandriva did right with Compiz Fusion?  ANd why can't Mandriva/OpenSuse,and the others figure out what Ubuntu/Canonical did to get the proper drivers for a new laptop (Even is it isn't the neates/spiffiest/hottest laptop Dell makes?)

Almost all hardware drivers are built out of the Linux kernel source code, either natively in the kernel image, or as modules loaded at runtime.  If the kernel version the distro is using is too old, it may not have support for devices that were added later.  This was the case with my Debian `Etch' discs and a family member's Dell desktop.  Although that installation media works fine with my computer, it failed to detect the ethernet on the other.  I downloaded the CD1 ISO image from the `Lenny' Testing branch and used it to perform the installation on the Dell and it worked perfectly.  The devil is always in the details.

My suggestion is to pick one distro and put stick it out and work on its nagging issue instead of bouncing around and finding *every* distro's nagging issue.

---

### Post by original_jamingrit on 2008-02-08
I Liked Sabayon, it's good for working out-of-the-box.  Although, I found it kind of became unstable when I wanted to configure it for myself too much.
[http://www.sabayon.org/](http://www.sabayon.org/)

Although, it's really not cool to have a kind of distro-shuffling attitude without trying to understand why a given distro (not just ubuntu) doesn't seem to work for you.  This isn't just a product, like most open source software it's an ongoing project that you become a part of (no matter how small a role you play) as soon as you start to take an interest.
Anyhow, good luck.

---

### Post by Seven of Cups on 2008-02-08
> Although, it's really not cool to have a kind of distro-shuffling attitude without trying to understand why a given distro (not just ubuntu) doesn't seem to work for you. This isn't just a product,

Unfortunately, This new computer is meant solely for work.  The Eye-candy is just to show off, and to make tedium more enjoyable.

For myself I have a 40+ hour a week job that is not IT related...  and when I do get home, I don't have as much energy to devote mentally to actually delving deeply into nuts and bolts.

As to trying to understand, this is why I made this post, and so far from the excellent postings to my thread I -am- getting an education far more succinct and informative than anything I got just searching, surfing, and skulking about in other threads/sites.

But I do have something of a time limit before I have to have the Dell ready for working.  So if that means I need to try different Distros, see if one out of the many ARE offering all I need "Out of the Box" then I shall resign myself to being "uncool" to the more Dedicated Linux users.

At the moment, even Mepis did not detect my Marvell Yukon "out of the box" like Ubuntu.

And with what I hear of Hardy vis a vis handling the "Intel Mobile Graphics 965" chipset... I am more than willing to wait on Ubuntu at this point. 

And I will tell you THIS much...  Until Gates and his Droogs get their heads out of someplace biologically impossible :)  ONLY Linux has the growth and willingness to change on a quick and responsive basis.  Any wonder why I don't bother with the M$ Vi$ta that came with the computer?  (Yeah I know Dell sells Laptops with Ubuntu installed... but this was a gift...  and the Giver didn't know about that *winks*)

---

### Post by jaytek13 on 2008-02-08
As far as uniformity is concerned, that has been a discussion in the Linux community since, well, the inception of Linux. The problem with it is that none of the people in charge want to come to an agreement about what exactly that uniform should be, to the detriment of the end user. 

As far as sticking with one distro, and if it doesn't work right, try another... that's a perfectly fine option. Linux is about choice, and that choice includes preferring distro's that just work over ones that require work. There are certainly distros out there that force people to throw themselves back to how Linux was 10 years ago, and for whatever reason they hold appeal for a small few, but most people just want something that works, and this is why ubuntu has been successful. There is always benefit in learning the basics, obviously, but most people, unless they are developers, don't want or need to know how something works behind the scenes (not to say editing config files explains that too well, either). 

And as far as a lot of the comments in this thread are concerned, they are very inappropriate. While Linux has always had a reputation of having very elitist users, Ubuntu for the most part has tried to get rid of that stigma, but there will still be some bad seeds in the bunch.

---

### Post by Seven of Cups on 2008-02-09
> While Linux has always had a reputation of having very elitist users, Ubuntu for the most part has tried to get rid of that stigma, but there will still be some bad seeds in the bunch.

Well...  Believe me.  The first time I ever went on a public forum was when you still had things called Prodigy and Compuserve.  Remember those?  Less-than-socially-acceptable responses and comments were common even then.  I just give back the attitude I get and move on.  I just try to keep my responses from getting too hot in those instances where the offense perceived may not have been actual offense offered. :)

But to a more critical point...
> 
As far as uniformity is concerned, that has been a discussion in the Linux community since, well, the inception of Linux. The problem with it is that none of the people in charge want to come to an agreement about what exactly that uniform should be...

That has been a factor since the industrial revolution I think :lolflag:
Anytime you have a group of raging and zealous innovators all jockeying for being the ones to hit the NEXT milestone, getting them to come together and build any kind of standard... whether Hardware, Software, or Mindware... is usually a process that gets steamrolled under.  Progress being what it is, in the time they do finally take to pause...  work out a solution... work out the kinks IN the solution... then start working together effectively?

Some arrogant whippersnapper comes in with THEIR neat new innovation that blows them all outta the water and they have to spend all theri time catching up to the new punk. 

One thing that has begun to boggle my mind with this latest foray into learning how you all do things...  How in the heck do you manage to even ATTEMPT to keep up with all the drivers for all the hardware with all the updates, and all the patches, and all the tweaks that all these people are pumping out?

I don't think you distro developers at ANY of the distros (mentioned and unmentioned exactly have a staff of thousands...) so for even trying?  Thanks a ton, folks.

*Returns to waiting for Hardy Heron*

---

