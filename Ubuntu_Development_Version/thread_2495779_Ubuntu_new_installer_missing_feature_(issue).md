---
title: "Ubuntu new installer missing feature (issue)"
date: 2024-03-01
forum: Ubuntu Development Version
---

### Post by sirblacksheep on 2024-03-01
In the Ubuntu Ubiquity legacy installer when selecting manual partitioning I had the freedom to not only select endless partition tables but more importantly create a separate boot partition for where my new Ubuntu install places my efi/boot. In the new Flutter version I can only select  which drive to place my boot but doesn't allow me to create or select a specific boot partition where I want my Ubuntu boot partition to be. 

I run multiple distros in one system for testing purposes. In my current Alienware X17 I run 4 distros. To competently separate and quick swap one of my distros in rotation I have one separate small boot partition for each distro I use for example: Ubunt: Boot partition / System Partition + Fedora Boot partation / system partation, Arch: Boot Partition / System partition ...........    and so on. If i quickly want to change let's say to Garuda Linux all I do is replace Fedora Boot partition / System Partition to Garuda Boot partition / System partition  then hit a quick grub update on the existing running distros. Makes this quick hassle free and never messes up my boot sector when replacing one distro to the other. 

When I installed Ubuntu 23.10 I had to use the legacy installer for it not to mess up the rest of my distro setup by manually placing my ubuntu boot partition (not just the drive) where I want it.

Can the Ubuntu development team transfer this feature to the new installer so we once again able to manually create and select not just the drive but also the partition where we want the Ubuntu boot sector to go?  

I fear that the legacy installer will be dropped by Ubuntu 24.04 and I won't be able to Install Ubuntu without messing up the rest of my boot sectors if I can't manually place my boot partition anymore.

---

### Post by MAFoElffen on 2024-03-09
My concerns also... Of that and other things that we are not ale to do in the new partitioner.

The place to discuss those things is here in this Forum. But discussing here, does nothing to change that. Sorry. No one here works for Canonical. We are just a group of volunteer Users, albeit with experience and skills. I am just another User, who tries to help other Ubuntu Users.

I help test in Dev Cycles, so we might be able to affect changes in what is released. I'm not sure what we discuss here does in those changes, but other tthings we do in that process, I hope does... (Discussed below.)

The two places to bring it up "Change" are at Launchpad.net and the installers GitHub. 

I am a bit passionate about trying to keep our abilities to do things in our distribution. If I feel a change needs to happen, for example with the partitioner in the new Flutter Installer--- This is what I try to do:

I filed bugs against the installer at Launchpad.
RE: 
[https://bugs.launchpad.net/~mafoelffen](https://bugs.launchpad.net/~mafoelffen)

Specially, For example:
[https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

Then I file issues and recommendations at their Installer GitHub:
[https://github.com/canonical/ubuntu-desktop-installer/issues](https://github.com/canonical/ubuntu-desktop-installer/issues)

Specifically, for example:
[https://github.com/canonical/ubuntu-desktop-installer/issues/2383](https://github.com/canonical/ubuntu-desktop-installer/issues/2383)
[https://github.com/canonical/ubuntu-desktop-installer/issues/2361](https://github.com/canonical/ubuntu-desktop-installer/issues/2361)

If not answered then I file a question at Launchpad. For example:
[https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132](https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132)

Those are places members of Canonical live. Another is the Ubuntu Discourse, but honestly, I think mostly Canonical's  Marketing people live there, and I haven't found the right audience their where it would make the right difference.

Is is not an easy process. But I think it works if you work the system in your favor and get enough people to join in on it, so they (members of Canonical) can't ignore it.

EDIT: Even in DEV Testing Dailys... We test things "they want" tested. I have to admit, when a release is released, they first freeze the repo's for a period, then release the final ISO of that release. I am still surprised on how some of those pieces are put together into what becomes the Final Release. We are not deciders of how that is done.

---

### Post by sirblacksheep on 2024-03-21
Thank you for the clarification MAFoElffen. The bureaucracy of Ubuntu is what disconnected the users from the decision makers. Seems like they have endless layers of departments making sure to never hear the Ubuntu " Humanity " community at the top.  It's kind of like 21st century politicians. I love the design of Ubuntu but the disconnect gap is widening on a yearly basis. Just to name a few: Garuda, Manjaro, Arch, Mint, Pop Os! even Fedora responds to it's users to the forum. I'm very impressed how quickly Garuda team responds with bugs reported not just with a replay but with a quick bug fix update. It's good to see that there are more people concerned about the new Flutter installer. I'm not sure why even replace ubiquity if all you do is cut out features. Your story doesn't seem too promising if this have been reported for over a year and fell on death ears. Specially if no one cares at Canonical to respond to users concerns unless there are enough outrage from enough people to force them to make a change. Like I said, sounds like politicians. Looking forward to see what steps Canonical will take before 24.04 goes live. Will they fix it? Will they keep Legacy installer as option B? If neither the option will be to keep an image of 22.04 or/and 23.10 so you can install with ubiquity and then make an upgrade to 24.04, 24.10, 25.04..... that sounds crazy. Once again I love Ubuntu but they working very hard to disconnect more and more of it's user base the last few years.

---

