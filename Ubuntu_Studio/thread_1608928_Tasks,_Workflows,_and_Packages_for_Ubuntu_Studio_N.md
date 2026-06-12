---
title: "Tasks, Workflows, and Packages for Ubuntu Studio Natty"
date: 2010-10-29
forum: Ubuntu Studio
---

### Post by Scott L on 2010-10-29
Hello again.

We are almost a month from the first Alpha image for Ubuntu Studio and I  wanted to share an update about Ubuntu Studio Natty Narwhal 11.04.

I had mentioned before on the mailing list that in an effort to make  Ubuntu Studio more effective and proficient we were identifying tasks  that a user might want to accomplish with Ubuntu Studio.  Additionally  workflows were developed to support these tasks which include which  packages might be required  a general set of actions required to  accomplish said tasks.  Developing these workflows helps us in numerous  ways, including identifying a package set, providing framework for user  documentation, and providing a path for testing.  This email will focus  on identifying a package set.

For those who are interesting, and I would hope most would be, you can  find the task and workflow wiki page at:   [https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)

All users are encouraging to peruse this page and add their  contributions!  We only ask that if you have a differing workflow that  one that is already extant, please add yours as an "alternative" and do  not remove the other.

Before going further I want to explain more about what I mean when I use  the term "package set".  This term is a reference to the applications  installed by default with Ubuntu Studio.  These packages are NOT being  removed from the archives.  You can always install these packages at any  time, by any method of choice.  We are only discussing the inclusion of  these package on the Ubuntu Studio ISO.

Right.  Now that we have that out of the way, I want to inform you how  the currently installed package set will change for Natty.

These will be "new" packages (or applications) installed by default when installing Ubuntu Studio:
 * guitarix
 * hydrogen-drumkits
 * lashd
 * mscore (to replaces denemo and lilypond)
 * phasex
 * qtractor (to replace seq24)
 * specimen
 * whysynth
 * yoshimi (to replace zynaddsubfx)

These are packages (or applications) that are currently included with Ubuntu Studio, but will no longer be:
 * aconnectgui
 * audacity
 * beast
 * bitscope
 * bristol
 * csound
 * denemo (replaced by mscore)
 * freebirth
 * freqtweak
 * genpo
 * jackeq
 * jacktools
 * jdelay
 * lillypond (replaced by mscore)
 * lmms
 * mixxx
 * muse
 * qamix
 * seq24 (replaced by qtractor)
 * terminatorx
 * timemachine
 * timidity
 * tk707
 * xwax
 * zynaddsubfx

Again, the goal is to make Ubuntu Studio more effective and proficient,  in essence more useful.  Users want to accomplish a task (e.g. mix a  song), not just run an application.  The current status of the package  set ([https://wiki.ubuntu.com/UbuntuStudio/PackageSelectionDevelopment](https://wiki.ubuntu.com/UbuntuStudio/PackageSelectionDevelopment))  was developed to assist users accomplish tasks.

If an application is listed to no longer be included with Ubuntu Studio  but you want it to be, then please identify a task that requires it and  develop a workflow at: [https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)

This is your chance to directly influence which applications are included with Ubuntu Studio.

To consolidate the discussion I would ask if people can respond to this email (which is essentially this post): [https://lists.ubuntu.com/archives/ubuntu-studio-users/2010-October/006769.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2010-October/006769.html)

ScottL

---

### Post by Gordonjcp on 2010-11-04
Looking at that, you won't actually include any synthesizer packages of any kind, or any viable sequencers.  Is it really a good idea to remove all the useful packages?

---

### Post by Scott L on 2010-11-12
> **Gordonjcp said:**
> Looking at that, you won't actually include any synthesizer packages of any kind, or any viable sequencers.  Is it really a good idea to remove all the useful packages?

Gordon,

Not all synthesizers and sequencers are being removed, you might [read]("https://wiki.ubuntu.com/UbuntuStudio/Workflows#Sequencing%20music%20using%20MIDI") the wiki page.  Note that this is just one place on the page.

But let's be clear, if it is important enough for you to complain here, then it should be important enough for you add to the wiki page and make sure the applications you care about are represented in Ubuntu Studio.

Also keep in mind, the packages not listed are* only* not shipped by default in Ubuntu Studio, they are _not_ removed from the archives.  You will continue to be able to install any of the applications not shipped with Ubuntu Studio.

Lastly, please use the mailing list to keep all the comments in a single place.

Regards,
ScottL

---

