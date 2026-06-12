---
title: "Ubuntu / other distro's Upgrade sucks."
date: 2010-01-21
forum: The Cafe
---

### Post by markinf on 2010-01-21
How can we speak of stability if Ubuntu Upgrade System just **Doesn't Work** (TM)? Look at the huge amounts of problems in upgrading in the forum. And worst, clean install is/should not a solution and it's NOT acceptable.

I've used others distros from Solid Distros (CentOS, Debian) to RollingReleases (Arch, Gentoo) and upgrading IS a pain in Linux. Actually on Rolling Releases distros is a little better, due to a constant upgrading. How can we tell the user that he can't upgrade because it's going to break his sytem? Or worst, I've seen some bizarre user suggestions that user should stick forever with distros. Ubuntu IS by default a &#8220;Linux for Human Beings&#8221; distro and personally the main target is desktop users, peopple don't stick with a specific version of a software more than 6 months. Actually 6 months is a  lot in &#8220;computer&#8221; time, if we look back a lot of softwares has appeared/gained new stuff in this time, so how can we tell users to stick with old software forever if they can't easily upgrade their system? I'm kinda shocked that with the current horrible upgrade software no one has ever step up to try to fix it. [To list a few of the horribles problems from the upgrade to 9.04 to 9.10:]("http://www.ubuntu.com/getubuntu/releasenotes/910")

[LIST]
[*]Possible corruption of large files with ext4 filesystem
[*]Switching to ext4 requires manually updating grub
[*]Unable to activate Broadcom b43 after STA driver
[*]Evince PDF viewer does not work for nonstandard home directories
[/LIST]

Actually about the third problem is one of the most hilarious. The bug was repported on [Karmic Alpha 3,]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/411320") and it didn't get fixed. And guess whats the wifi driver that runs on netbooks and Mac's? It's Broadcom!

So enough smashing why Ubuntu upgrade Sucks. Here's my personal list of problems of why it sucks and how to fix it.

**Bugs should be fixed** &#8211; Yes, they aren't. Why the aren't? Because of the 'Semi-god' state developers who just mark &#8220;won't fix&#8221; , &#8220;unaffected me&#8221;  and undecided on all bugs. We need A CLOSER relationship between developers and users bugs. Filing a bug on Alpha 3 that will hit major users should be considered a priority and SHOULD be fixed before the official release. The same apply with the corruption with large ext4 files, an official release should NEVER ships with this &#8220;cool&#8221; bugs. and not fixing it's just unacceptable. [And also, we have bugs lying around for years, this one it's going to complete he's 2 years birthday]("https://bugs.launchpad.net/ubuntu/+bug/204898").

[B]
Backports should be used[/B] &#8211; Yes, when a package sucks and it has problems/bugs the fixed version  SHOULD be packaged and delivered to the user. Why this doesn't happen? Because of the &#8220;stability test&#8221;? Which test, the one that delivered that allow these major bugs? Also for god-sake expand the &#8220;officially&#8221; supported packages to at least more 500 pkgs, people shouldn't  be  allowed to use packages that are just trowed at the repos.

**Packange Standards** &#8211; Ubuntu has no simple standards, in fact, the [wiki page has nothing useful to standardization]("https://wiki.ubuntu.com/PackagingGuide/Complete"). [Debian packaging standards are too much bureaucracy]("http://www.debian.org/doc/debian-policy/"), &#8220;stupid&#8221; IMO, which lends to people packaging the same software in different pkgs types, to get worse we have the famous -dev,-headers,-foo,-bar,-libFooHaxe, which confuses more packagers. How to fix this? Write a SIMPLE and EFFICIENT guideline on how to pkg stuff. [Arch package standards]("http://wiki.archlinux.org/index.php/Arch_Packaging_Standards") is a example of beauty and simplicity of a STANDARD. Why can't debian/ubuntu have a guide/standard simple?

So this weekend I'll try to compile all info of debian/ubuntu packaging standard bureaucracy into a simpler document like Arch Wiki PKG Standard. With links of  &#8220;bureaucracy&#8221; problems directly linked to debian-policy. 

Sorry about my personal outburst. But I can't face the horrible problems of Ubuntu upgrade system and I think we need to make something to fix it.

Any Ideas or thoughs?

---

### Post by Genius314 on 2010-01-21
Upgrading should definitely be improved.

I've done a clean install for every upgrade so far, just to avoid all the problems it causes. I've had a separate partition for / and /home to make clean installing as easy as possible.

I also think clean installing over an old version should be improved.
For instance, it should scan your current version for already installed packages (maybe just programs) and either install them automatically in the new version; or make a sort of "to-do" list, where you can install each thing when you want. I find it difficult having to remember the name of every program I installed in the last version. It's a pain.

---

### Post by mikewhatever on 2010-01-21
Now call all this constructive criticism, and the picture is complete.

---

### Post by Xbehave on 2010-01-21
**"Bugs should be fixed"**
Fix them, help people fix them, pay for them to be fixed OR quit moaning
p.s [https://bugs.launchpad.net/ubuntu/+bug/204898](https://bugs.launchpad.net/ubuntu/+bug/204898) isn't a bug it's a feature request

**"Backports should be used"**
No they shouldn't if i install ubuntu and get firefox3.0, i expect firefox to stay at 3.0 with the exception of major bugfixes and security patches. If **you** want programs to be updated **you** should enable backports.

**"Packange Standards"**
Arch wiki has nothing about separating out -dbg,-dev,-data and no guidelines on turning monolithic packages into modular ones, not everybody should be packaging tbh and if you are then doing it right is important

---

### Post by markinf on 2010-01-21
> **Xbehave said:**
> **"Bugs should be fixed"**
Fix them, help people fix them, pay for them to be fixed OR quit moaning
p.s [https://bugs.launchpad.net/ubuntu/+bug/204898](https://bugs.launchpad.net/ubuntu/+bug/204898) isn't a bug it's a feature request

**"Backports should be used"**
No they shouldn't if i install ubuntu and get firefox3.0, i expect firefox to stay at 3.0 with the exception of major bugfixes and security patches. If **you** want programs to be updated **you** should enable backports.

**"Packange Standards"**
Arch wiki has nothing about separating out -dbg,-dev,-data and no guidelines on turning monolithic packages into modular ones, not everybody should be packaging tbh and if you are then doing it right is important
1)
Actually on link n1 :3 I passed my eyes fast and tough it was a bug report.

2)
About Backports it should be used IMO it should be used. And actually it should be used for real upgrading because staying on a broken software for 6 months it's unnaceptable. People don't care if firefox it's at 3.0, or 3.0.1, or 3.1.2, they care if the app works and IF it has bugs on the "default" shipped version it should be fixed.

3)
I mentioned Arch wiki as a way of organization of pkg standards. It presents what / how their pkg system work and them after that they specify some additional standars for different niche of pkgs, java, python, ruby...

Now you can't compare the objectivity of this document with the BOOK and bureaucracy of Debian-Policy.

---

### Post by Xbehave on 2010-01-21
> **markinf said:**
> About Backports it should be used IMO it should be used. And actually it should be used for real upgrading because staying on a broken software for 6 months it's unnaceptable. People don't care if firefox it's at 3.0, or 3.0.1, or 3.1.2, they care if the app works and IF it has bugs on the "default" shipped version it should be fixed.
3.0.x give a certain behaviour, this lets me work with ubuntu and know that until i upgrade firefox will always behave in a consistent way. I sure as hell don't want to wake up one day and see ubuntu has broken all my extensions, backports should be enabled by those that want them.

> I mentioned Arch wiki as a way of organization of pkg standards.
It has nothing on package standards it's a simple howto for PKGBUILD, for binaries that are not maintained by arch itself, it's the equivilent of writing a control+rules file, not of packaging a program for inclusion in debian/ubuntu.

> Now you can't compare the objectivity of this document with the BOOK and bureaucracy of Debian-Policy.
No you would compare it with the [debian packaging guide]("http://www.debian.org/doc/maint-guide/"), which is comprehensive and covers what you need to know to produce a package of use to others. It might be all the rage to create simple howto's but if you cant follow the debian packaging guide then your probably not going to be much use as a package maintainer.

---

### Post by Skripka on 2010-01-21
> **markinf said:**
> 
I've used others distros from Solid Distros (CentOS, Debian) to RollingReleases (Arch, Gentoo) and upgrading IS a pain in Linux. Actually on Rolling Releases distros is a little better, due to a constant upgrading. How can we tell the user that he can't upgrade because it's going to break his sytem? 

Um.  ***_You read the forums and news pages of the distros' website._***  That easy.  If you are not researching a bit what you are upgrading/doing then you're ASKING to get bit.  Even then the main culprits which cause breakage tend to be Xorg and friends, although things like kernel 2.6.32 have had big issues with Intel gfx drivers.  I of course know this, because I read and stay in the loop on upgrades-even though I don't even own a machine with Intel gfx drivers.

It really is that simple-it is rare that you will always be the lone first reporter of a problem.  Can't vouch for Gentoo's social scene, but that is life on the Arch forums.

---

### Post by lovinglinux on 2010-01-21
> **markinf said:**
> 1)
Actually on link n1 :3 I passed my eyes fast and tough it was a bug report

So, there is nothing affecting you that haven't been fixed over two years. You just picked up a random launchpad entry based on date, without even reading it, just for the sake of complaining. Nice.

> **markinf said:**
> 2)
About Backports it should be used IMO it should be used. And actually it should be used for real upgrading because staying on a broken software for 6 months it's unnaceptable. People don't care if firefox it's at 3.0, or 3.0.1, or 3.1.2, they care if the app works and IF it has bugs on the "default" shipped version it should be fixed.

Seriously? I guess you haven't followed the whole [Shiretoko]("http://lmgtfy.com/?q=Shiretoko+site%3Aubuntuforums.org") discussions. People care too much about anything. There are endless discussions about why Firefox 3.5 wasn't included in the official Jaunty repos, why they had to use a browser with the name Shiretoko and an "ugly" logo,  endless discussions about why Ubuntu should include major Firefox upgrades into the repos and so on.

Nevertheless, I agree that broken applications should be fixed as soon as possible, preferably before the final release if they are reported during beta testing. For instance, my grub takes 23 seconds to load because the mbr is on a different drive than the grub files. This has been reported during the Alpha testing phase. Although it seems to be fixed in Lucid, it hasn't been backported. This is the major problem I'm experiencing with Karmic, along with mplayer issues.

BTW, ext4 has been extremely rock solid for me since Jaunty, even after several power outages (6 times since november here) and some system locks. I also have already done a lot of partition resizing and moving, without losing anything.

---

### Post by Skripka on 2010-01-21
> **lovinglinux said:**
> So, there is nothing affecting you that haven't been fixed over two years. You just picked up a random launchpad entry based on date, without even reading it, just for the sake of complaining. Nice.



In fairness to the OP, I seem to read lots of reports from Ubuntu users here of open bug reports that are 1 year+ old that have not been followed up on, solved, or closed as duplicates.  Of course, I can't name an example OTTOMH.


Ubuntu seems to be suffering from millions of users, and casual bug reporters...and too few vol bug fixers.

---

### Post by Xbehave on 2010-01-21
>  For instance, my grub takes 23 seconds to load because the mbr is on a different drive than the grub files. This has been reported during the Alpha testing phase. Although it seems to be fixed in Lucid, it hasn't been backported.
That sounds like a bugfix not a backport, maybe they are just being very cautious about releasing any bugfixes to the bootloader(you having a 23second boot is better than a server upgrade resulting in no boot due to the patch having unintended side effects). Generally important/security bugfixes (i'd say a 23 second grub waitime is important) get shipped as updated, it's only new versions that become backports.
e.g any firefox 3.5.x released in the next 15 months will be supplied as an update to karmic, however no 3.6.x would need to be a backport.

> BTW, ext4 has been extremely rock solid for me since Jaunty, even after several power outages (6 times since november here) and some system locks.I get several locks a week due to hardware issues and ext4 and btrfs have both shown no problems :)

> **Skripka said:**
> Ubuntu seems to be suffering from millions of users, and casual bug reporters...and too few vol bug fixers.
Dammit! I hate it when i agree with Skripka, but hes right. I'd also bet that a lot of fixed bugs go unmarked because they are fixed upstream or by accident and nobody notices.

---

### Post by lovinglinux on 2010-01-21
> **Skripka said:**
> In fairness to the OP, I seem to read lots of reports from Ubuntu users here of open bug reports that are 1 year+ old that have not been followed up on, solved, or closed as duplicates.  Of course, I can't name an example OTTOMH.

Yep, I know. I just couldn't resist :)

> **Skripka said:**
> Ubuntu seems to be suffering from millions of users, and casual bug reporters...and too few vol bug fixers.

Perhaps. I wish I could help, but I don't have the skills.

---

### Post by cariboo on 2010-01-21
Previous to Karmic, the upgrade guide said to uninstall all 3rd party software, and disable all ppa's to upgrade without breaking anything. People not following the guide, were guaranteed to have problems, as we have seen many, many times.

Karmic + is trying to solve this problem by automagically disabling ppa's, hopefully the devs get this fully developed, so that upgrade problems will be a thing of the past.

---

### Post by lovinglinux on 2010-01-21
> **cariboo907 said:**
> Previous to Karmic, the upgrade guide said to uninstall all 3rd party software, and disable all ppa's to upgrade without breaking anything. People not following the guide, were guaranteed to have problems, as we have seen many, many times.

Karmic + is trying to solve this problem by automagically disabling ppa's, hopefully the devs get this fully developed, so that upgrade problems will be a thing of the past.

Interesting. Perhaps would be nice to include a script to automatically generate a list of installed third-party packages, so the user could easily install them again later, after the upgrade. We all know how to do that, but I believe regular users won't like the idea of uninstalling third-party applications before each upgrade.

---

### Post by cariboo on 2010-01-21
I've already seen a couple of complaints about the ppa's being disabled, I guess you can't please every one. :)

---

### Post by Skripka on 2010-01-21
> **lovinglinux said:**
> We all know how to do that, but I believe regular users won't like the idea of uninstalling third-party applications before each upgrade.

I'm curious why uninstalling things needs done to upgrade kernel etc.?

Is it junky package upgrade script writing that doesn't handle config file syntax/format changes?  I read lots about upgrade woes that go away on clean installs in /root with deleted /home/.config files-but don't see any rational explanation why it should be so.  

I have never experienced these problems on rolling release, so why should it be the case on monolithic release?  Don't get it.

---

### Post by Xbehave on 2010-01-21
> **Skripka said:**
> I'm curious why uninstalling things needs done to upgrade kernel etc.?
Because the can be compiled against incompatible libraries and the dependency info will not uninstall them because it often just says it needs a libfoo >=N, rather than needs libfoo >=N conflicts libfoo >=N+1

> Is it junky package upgrade script writing that doesn't handle config file syntax/format changes?  I read lots about upgrade woes that go away on clean installs in /root with deleted /home/.config files-but don't see any rational explanation why it should be so.
This is up to individual packages, the apt scripts shouldn't touch /home or /root, programs should handle invalid configs gracefully though (firefox is a good example, kde is pretty terrible)

> I have never experienced these problems on rolling release, so why should it be the case on monolithic release?  Don't get it.
I think it's because everything is upgraded gradually (e.g you don't jump between incompatible glibcs) and there is more testing of the upgrade process.

---

