---
title: "Dear Canonical"
date: 2009-11-14
forum: The Cafe
---

### Post by qualtch on 2009-11-14
I've been using Ubuntu from version 6.06 and I really have to admit that there has been a HUGE development from those days. 

But still there exists really serious and actually true criticism that makes the Ubuntu and Ubuntu philosophy tremble in it's pants. So to create some serious discussion considering not only the user experience but developing Ubuntu too I'll quote and link few texts.

This developer has been maintaining the eee-control application for Ubuntu, but starting from October he stopped the development due to various reasons that were not of his personal life matters but considering the Ubuntu as a distro itself. He has some good points and critisism.

[_LINK: I give up_]("http://www.fewt.com/2009/10/i-give-up.html")

And also his letter to the Ubuntu developer community and Canonical...
[_LINK : Dear Mr. Shuttleworth, Canonical, and Ubuntu developers._]("http://www.fewt.com/2009/10/dear-mr-shuttleworth-canonical-and.html")
> **Dear Mr. Shuttleworth, Canonical, and Ubuntu developers.**

I am writing this article today in hopes that I may compel you to reconsider your release cycle. There is far more value to users, developers, vendors, and OEMs to know that the software product that you provide to them is stable, and mature. While there is absolutely value in a release cycle I believe that more harm is being done than good with your current process as bugs remain unfixed for extended periods of time and in my opinion the quality of your releases have never been lower.

I have spent many years using your product, and as a proponent of Linux in general, and now I find myself questioning my ability to really say that Ubuntu is a mature stable operating system for the masses. I see bug after bug after bug sitting in launchpad for months on end which directly impact users ability to perform simple functions like turning on bluetooth or WIFI. Problems like this give your operating system black eyes in the form of users spreading word that your operating system is no good, that it doesn't work right, and that it is not ready for prime time. Not only that, but it gives end users a distaste for Linux distributions in general because they don't know any better.

You know, they aren't wrong. They are absolutely right to complain when an end user turns off their WIFI only to find that their system halts with a kernel panic and they have lost anything that they were working on that was unsaved. This level of performance would kill a company like Microsoft or Apple if it was met with the types of answers that we receive from members of your teams whom are responsible for repairing these problems.

Currently users are expected to know how to get to bug reports, file bug reports, and install kernel packages from PPAs to fix or workaround issues. These are not functions for consumers, and until Ubuntu matures to the point where an end user can rest assured that when they suspend their computers that they will be returned to the work they were performing before closing their lids, they will never trust Linux on their consumer systems at home or for business functions.

You have recently made statements that your mission is to deliver benefits of free software to the consumer ecosystem, however without a complete change in process shifting to quality being your first priority you can only be expected to fail. In the eyes of the end users that you are targeting, bugs that impact users ability to enjoy and use their computers are not acceptable even to the smallest degree.

I would like to provide a small set of examples of a few of the bugs that I have been following personally which impact thousands of users. These bugs remain unrepaired in almost all cases in Jaunty, and yes in some cases they will exist in Karmic on release day because your release schedule is more important than end user experience.

**Bug #404626**; Turning wifi "off" using Fn+F2 on Eee PC with Ralink rt2860 results in kernel panic

This bug reported July 25, 2009 impacts at a minimum all Eee PC 901 users. When a user turns off their WIFI using any of the available utilities including those integrated into Karmic, the user receives a kernel panic. The user is unable to save any data from open applications, and they are forced to reboot their computer. Unfortunately, this bug will still exist in Karmic upon release. When asked by a user if it could possibly be fixed in the release, it was stated in the bug: "No, it doesn't work that way. An "exception" here would set back the release by a whole week, due to the time involved in integrating kernel changes and validating the resulting images. We aren't going to do that for a single piece of hardware that's supported on a best effort basis - this is entirely suitable for fixing in a post-release update."

Expect thousands of kernel panics upon release day because users computers don't work properly. Expect them to erase Ubuntu immediately afterwards because "Ubuntu sucks".

*Update: [ 2009-10-28 13:23:01 errata for bug #404626 ]*

**Bug #371434**; PCI ExpressCard hotplug requires pciehp.pciehp_force=1

This bug reported May 3, 2009 impacts a wide variety of systems. With this bug, the kernel hotplug driver is unable to hotplug certain devices forcing a user to have to reboot their computer and in some cases enter the BIOS to re-enable a device that has been turned off in the operating system in order to turn it back on. There are multiple work-arounds however all of them are more complex than should be expected of an end user. This issue will impact Karmic users on release day.

**Bug #337199**; eeepc-laptop patch missing in Jaunty Alpha 5

This bug reported March 5, 2009 impacted all Eee PCs. In May after waiting several months for a patch to be released I issued a patch for Eeebuntu repairing the Eee PC Laptop kernel module and released it in a DKMS package which overwrote your module. This corrected the problem for thousands of my users, and any of yours that stumbled across my website. This is simply unacceptable as it still is not fixed in Jaunty and only marked as repaired because the kernel your team pulled downstream for Karmic corrected it. Jaunty users are left without a fix even though you still support their platform. This isn't even basic O&M support in my opinion.

**Bug #349314**; Slow performance and tiling issues on i915

This bug reported March 26, 2009 was fortunately flagged as repaired in Jaunty August 17th, 2009 long after most users fumbled through forum posts and upgraded or downgraded their Intel drivers to drivers that worked. This bug fortunately does not exist in Karmic, however users were left to figure out how to fix it themselves (even if they read the release notes) for several months. A consumer would never except this.

I strongly urge you and your team to reconsider your release cycles and to integrate better with upstream maintainers while releasing patches faster for your users to minimize their pain with your operating system. Mature Linux distributions issue patches for issues to correct them for users quickly rather than sitting on them in hopes that they will be fixed upstream for the next release. They then work to merge their changes upstream after solving issues for their customers improving the Linux ecosystem as a whole. End users will never accept the current process in which patches are ignored, categorized as low priority when they impact multiple users, or the difficulty in finding resolution and guidance to issues that they continue to face. Continuing down this path only further blemishes my favorite platform. So, please do us all a favor. Shift your focus to quality, integrate better with upstream, and please remember that you can't sell something to common consumers that does not work right.


Thank you for your time,

-Fewt

WARNING: Do not install 9.10 with EXT4, there are known data corruption issues with it [ 453579 ]. They released with it as the default filesystem though it has been known to be an issue for 2 weeks. Be sure to switch to EXT3 during the installation to be safe. There's an Ubuntu one bug too that causes data loss. WOW, really great stuff there Canonical. 

---

### Post by 3rdalbum on 2009-11-14
I think this developer might have a different perception of "what affects most users". Having said that, I agree that it's unacceptable that the Intel driver is broken in Jaunty, and has never been fixed - when you think about it, it's broken in Jaunty for 18 months. If Canonical says they are supporting Jaunty for 18 months, why have they not fixed this very big issue that has already been fixed in a later version of the distribution?

The warning about Ext4 is a classic case of "Read the release notes":

> Possible corruption of large files with ext4 filesystem

There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. (453579)

I don't think they've even confirmed that there is an issue. This was the first I'd heard about it, so it's certainly not widespread. As a test I just copied a 30 gigabyte file from my ext3 drive to my ext4 drive - the hash checks out, I still have full confidence in Ext4. Even if there is an issue, it's an issue that exists in an upstream kernel.org release.

The ralink wifi issue is also mentioned in the release notes, and has been fixed in a post-release update.

---

### Post by hanzomon4 on 2009-11-14
I agree with the OP, Ubuntu works great for me but I've been using linux for years. I know my way around and, for some reason, am willing to work out bizarre problems. No one should be expected to jump through the hoops I've had to jump through to use a computer, thats part of the reason why I file bug reports. But if bugs are not being addressed, as I've wondered before reading this, then what's the point?

Linux is a really good system when it works and apps don't crash left and right. However in my experience you hardly ever get such an experience as things are always breaking. I've downloaded so many apps from the repos that flat out don't work and probably shouldn't be in the repos. Even when I installed KDE on karmic changing themes caused the workspace to be dead upon the next login. Most of the computer using population would have taken the machine in to be serviced. As it turned out some widgets can't coupe with anything but Oxygen, removing them(ublog, open-social) or changing the theme back to Oxygen was all that was required.

 I could go on, firefox crashing and not being able to relaunch it because "it's still running", gnome-do crashing at login causing 100% cpu usage, kopete disconnecting every 5 mins.. But, urgh.. whatever

---

