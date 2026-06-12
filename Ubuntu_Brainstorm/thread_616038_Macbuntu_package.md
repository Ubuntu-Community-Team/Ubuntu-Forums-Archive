---
title: "Macbuntu package"
date: 2007-11-17
forum: Ubuntu Brainstorm
---

### Post by slyn on 2007-11-17
Rather than making new users mess with the terminal and config files (such as [here]("https://wiki.ubuntu.com/MacBookPro/SantaRosa")), Ubuntu should try and make moving from Mac to Linux as easy as possible. Mac users tend to be pampered (and I say that as one) because their software is specifically built for their hardware. Rather than having to support hundreds or thousands of different computer hardware components and configurations, Mac's have relatively very few possible hardware configurations.

If someone could write an app/script/whatever that detects what type of hardware you were running and then figure out what type of Mac you have based off of  that data, then you could have that same app run through a simple series of driver installations and .conf edits based off of what type of Mac you have to get things like wireless support, accelerated GPU, trackpad support, keyboard support, webcam support (if they have a macbook or macbook pro), etc. 

Preferably it would have minimal options such as FOSS drivers only or an Anything goes setting.

By making it as simple as installing a package to get a fully working Linux desktop on Apple hardware, I think you could attract a number of users, especially those with hardware that no longer supports the newest OS X release/apps.

---

### Post by raynevandunem on 2007-11-18
What about [mac4lin]("http://sourceforge.net/projects/mac4lin")?

Of course, that only takes care of theming and superficial stuff. 

Here's a [list of other FOSS replacements for Mac OS X features]("http://thelinuxvault.net/wiki/List_of_FOSS_alternatives_to_Mac_OS_X_utilities").

Also, incorporation of Klik, which uses a similar feature for application usage like OS X's disc images, would be a plus.

---

### Post by slyn on 2007-11-18
> **raynevandunem said:**
> What about [mac4lin]("http://sourceforge.net/projects/mac4lin")?

Of course, that only takes care of theming and superficial stuff. 

Here's a [list of other FOSS replacements for Mac OS X features]("http://thelinuxvault.net/wiki/List_of_FOSS_alternatives_to_Mac_OS_X_utilities").

Also, incorporation of Klik, which uses a similar feature for application usage like OS X's disc images, would be a plus.

Thats not a bad idea, but I'm one of those people who thinks Ubuntu/Linux in general should exceed the functionality and features of Windows and OS X by being technically superior and innovating more rather than emulating a "look and feel". Thats not to say that successful features from each platform can't be taken over to Linux (I would probably use AWN, and CFusion for its Expose like feature if I did use Linux), but I think that automating the detection of hardware and installation of necessary drivers would far exceed the current capabilities of Windows and bring Ubuntu to feature parity with OS X (in the driver installation sense) while still allowing for the mass of hardware customization that you can't have with Apple hardware.

And this concept doesn't necessarily have to only apply to Apple hardware. If someone could come up with another program for Dell, for HP (to prevent things like [this]("http://ubuntuforums.org/showthread.php?t=582220") from happening again), for Acer, etc. then it would greatly facilitate user-friendlyness and "out-of-the-box" functionality of Ubuntu.

---

### Post by Auria on 2007-11-19
Well so i think we could sum up with "improve detection and support of Apple hardware", your topic almost made it sound like a seperate distro and i don't think that's needed

---

### Post by slyn on 2007-11-20
> **Auria said:**
> Well so i think we could sum up with "improve detection and support of Apple hardware", your topic almost made it sound like a seperate distro and i don't think that's needed

A separate distro was certainly not what I had in mind. All this proposes is an application that does all the work of gathering drivers for various pieces of hardware, so that you (or I, or whoever) don't have to.

The restricted driver manager somewhat does that now, except that it is limited in its scope. And again, this idea doesn't necessarily have to be limited to Apple hardware, thats just what I was thinking of when I first made the thread.

---

### Post by aysiu on 2007-11-20
I agree with this proposal.

Every guide I've seen to getting Ubuntu working on the Mac is at least fifty different terminal commands or config edits. Why couldn't one metapackage take care of all that? There are only a handful of Mac models out there.

---

### Post by amonsul on 2007-11-22
I agree!!!!!!!!

---

### Post by frup on 2007-11-22
Start a bounty :P

---

### Post by climatewarrior on 2007-11-23
+1 great idea

I friend of mine wa going to try Ubuntu on his mac but stopped because it was quite a pain.

---

### Post by thegnuguru on 2007-11-24
Good idea a very good idea

---

### Post by dmber on 2007-11-25
> **raynevandunem said:**
> What about [mac4lin]("http://sourceforge.net/projects/mac4lin")?

Of course, that only takes care of theming and superficial stuff. 

Here's a [list of other FOSS replacements for Mac OS X features]("http://thelinuxvault.net/wiki/List_of_FOSS_alternatives_to_Mac_OS_X_utilities").

Also, incorporation of Klik, which uses a similar feature for application usage like OS X's disc images, would be a plus.
someone should add Gnome-Do to that list as a QS alternative.

---

### Post by OCTOG3N on 2008-02-04
It would be great if it not only detected what Mac you have but offered to migrate settings from OSX on install rather than windows.

---

### Post by hellion0 on 2008-02-05
I like this proposal as well. It shouldn't be too hard for the system to see a specific hardware config, realize "This is *x* kind of Mac", then download a specific package for it, since the number of Mac configs are indeed finite.

---

