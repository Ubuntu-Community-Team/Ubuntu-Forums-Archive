---
title: "I really hate upgrading Ubuntu..."
date: 2014-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2014-10-31
Not to complain, but I've been using Ubuntu for a while now, since version 6 I beleive.  I've never had ONE upgrade experience go pleasantly, with the exception of 12.04.  That was the ONE version that just happened to upgrade and work great, with great new features, etc.  So when I had the chance to upgrade to 14.04 I thought "I don't know, it's the next LTS version and 12 was really good, might as well give it a shot."

Well as always things happened.  I'm not stuck with using the open source radeon driver because of a combination of A) The fglrx driver in the repositories being a later version that no longer supports my graphics and B) A kernel that the legacy binaries from AMD doesn't work on.  Now I eventually figured out that the radeon driver can support basic TV out features which is all I wanted the proprietary graphics for, but it's still with weird underscan issues...

Anyway not a big deal, not really asking for help...  Probably going to downgrade back to 12.04 to be honest.  I just dont' like the Ubuntu update cycles.  I used 8.04 for *years* and don't even remember why I upgraded--was something about my kernel not supporting a piece of hardware I had.  I've been thinking of moving toa  distro that I could just let "sit" for a long time but I don't know, been using ubuntu so long...

At least 14.04 shows my nfs mounts in Thunar.  That's the one nice thing I've found so far.

---

### Post by bro2 on 2014-10-31
> **SagaciousKJB said:**
> Not to complain, but I've been using Ubuntu for a while now, since version 6 I beleive.  I've never had ONE upgrade experience go pleasantly, with the exception of 12.04.  That was the ONE version that just happened to upgrade and work great, with great new features, etc.  So when I had the chance to upgrade to 14.04 I thought "I don't know, it's the next LTS version and 12 was really good, might as well give it a shot."

Well as always things happened.  I'm not stuck with using the open source radeon driver because of a combination of A) The fglrx driver in the repositories being a later version that no longer supports my graphics and B) A kernel that the legacy binaries from AMD doesn't work on.  Now I eventually figured out that the radeon driver can support basic TV out features which is all I wanted the proprietary graphics for, but it's still with weird underscan issues...

Anyway not a big deal, not really asking for help...  Probably going to downgrade back to 12.04 to be honest.  I just dont' like the Ubuntu update cycles.  I used 8.04 for *years* and don't even remember why I upgraded--was something about my kernel not supporting a piece of hardware I had.  I've been thinking of moving toa  distro that I could just let "sit" for a long time but I don't know, been using ubuntu so long...

At least 14.04 shows my nfs mounts in Thunar.  That's the one nice thing I've found so far.

I'm sure someone other then me will be able to give an easy solution, but yes GPU drivers in general are a horrific experience on Linux compared to Windows. On Windows you just install the version you want for your version of Windows, but since the FGLRX drivers depend on your version of Xorg, then getting an old FGLRX on new XORG doesn't work. Once again I'm sure someone more experienced then me will swoop in with a couple of Terminal commands for you to copy/paste, but until then hopefully those newer Radeon drivers will do.

Really this is AMD's fault to cutting support for viable cards. NVIDIA still supports the Geforce 8 series from ~2007 (that can still play modern games btw), but AMD cut support for all cards prior to ~2009 for no good reason whatsoever. I woulden't blame the Linux kernal, but AMD.

I'm on a 5870 card, so I'm nervious since that's going to be the next they cut.

---

### Post by SagaciousKJB on 2014-10-31
> **bro2 said:**
> I'm sure someone other then me will be able to give an easy solution, but yes GPU drivers in general are a horrific experience on Linux compared to Windows. On Windows you just install the version you want for your version of Windows, but since the FGLRX drivers depend on your version of Xorg, then getting an old FGLRX on new XORG doesn't work. Once again I'm sure someone more experienced then me will swoop in with a couple of Terminal commands for you to copy/paste, but until then hopefully those newer Radeon drivers will do.

Really this is AMD's fault to cutting support for viable cards. NVIDIA still supports the Geforce 8 series from ~2007 (that can still play modern games btw), but AMD cut support for all cards prior to ~2009 for no good reason whatsoever. I woulden't blame the Linux kernal, but AMD.

I'm on a 5870 card, so I'm nervious since that's going to be the next they cut.

Yeah I totally agree, I have a desktop that has an integrated Radeon HD 3300 and it's in the same generationas my laptop's card that I just updated.  I never used it though, have been running a GeForce 7950 for years.  Nvidia definitely has better legacy support, their "legacy" cards are actually older than 5 years.

I'm pretty good at fixing issues over the years, but yeah this one is one of thsoe times where I'm like "I'm just going to wait 6 months until enough people have had the same problem that some linux guru fixes it and I can find it on Google" :P

What I'd really like though is something that is built for like, EXTRA long term support.  The three year cycle is okay, but I got a long just fine for a while just compiling new versions of software as I needed them.  That is until I needed to update the kernel or glibc or something more deeply rooted in the system.

It just seems like every time I upgrade to a new Ubuntu distro, that they're trying to do something too "new" and breaking support for older hardware.  There needs to be a more xenophobic release of ubuntu :P

---

### Post by coldraven on 2014-10-31
I am stuck with a worse card, the ATI X1250 :( At least in Ubuntu 12.04 I have the option at the login screen to run it in 2D mode but I fear this is not available in 14.04.
This laptop has a great keyboard and a lovely matte screen so I don't really want to replace it for the sake of a new shiny OS.
I'm moving to Arch!

---

### Post by /ADM on 2014-10-31
It bugs me too sometimes.  But my fairly old GMA X4500MHD still works good in Ubuntu (thanks mainly to terrific Intel Linux support).  But I also disagree with how Ubuntu rolls out updates, kind of pushes away the old and demands new things eventually.

Wasn't this one of the reasons why Linux is better?  Because old hardware will work?  They could at least keep an older Xorg, it's not like this ancient beast is going to reinvent the wheel or anything.

---

### Post by buzzingrobot on 2014-10-31
There's little that can be done about proprietary video drivers on Linux until/unless AMD/Nvidia do it. The drivers are released as binaries, according to AMD's and Nvidia's own schedules. All they really know is that their employees who developed the drivers were satisifed they worked well enough on the hardware they use.

If the open source drivers meet you needs, life will be easier if you just use them. If your hardware has onboard Intel video and it's good enough for you, use it. Intel's open source support and cooperation is superior to AMD and Nvidia's.

Upgrades from one release to another can be tricky on any distribution.  The more the system has been altered from the original baseline, the more the chance for failure. On Ubuntu, that means backing out any PPA's *and* the software installed from them.  I'd also revert to an open source video driver. Then I'd back up anything I can't risk losing.  After a successful upgrade, add the drivers and the PPA's back, after making sure they are actually available for the new release.

Better yet:  Don't upgrade.  Just do a new install. Put /home on its own partition (or its own drive), do you own partitioning, reuse /home without formatting it.

---

### Post by SurfaceUnits on 2014-10-31
> **buzzingrobot said:**
> Better yet:  Don't upgrade.  Just do a new install. Put /home on its own partition (or its own drive), do you own partitioning, reuse /home without formatting it.

^^^Word!! I have two system partitions that I alternate between current and previous. Now I have 14.04 and 13.10; I'll install 14.10 over 13.10 partition, etc.

---

### Post by SagaciousKJB on 2014-10-31
> **buzzingrobot said:**
> There's little that can be done about proprietary video drivers on Linux until/unless AMD/Nvidia do it. The drivers are released as binaries, according to AMD's and Nvidia's own schedules. All they really know is that their employees who developed the drivers were satisifed they worked well enough on the hardware they use.

If the open source drivers meet you needs, life will be easier if you just use them. If your hardware has onboard Intel video and it's good enough for you, use it. Intel's open source support and cooperation is superior to AMD and Nvidia's.

Upgrades from one release to another can be tricky on any distribution.  The more the system has been altered from the original baseline, the more the chance for failure. On Ubuntu, that means backing out any PPA's *and* the software installed from them.  I'd also revert to an open source video driver. Then I'd back up anything I can't risk losing.  After a successful upgrade, add the drivers and the PPA's back, after making sure they are actually available for the new release.

Better yet:  Don't upgrade.  Just do a new install. Put /home on its own partition (or its own drive), do you own partitioning, reuse /home without formatting it.

Yeah I use to run /home on its own partition but found that it didn't really do anything but preserve my configuration files in whatever ".folder" they happened to be in.   Which isn't BAD but I've always been looking for a way to preserve all of the programs I had installed too.  Otherwise it's like, saving a bunch of configuration files for a bunch of programs I don't even have, or must reinstall, etc.  Probably something with apt or dpkg that I could do, but even then there's programs from source.

I once tried to make a separate /usr/bin so that way when I had to clean install I wouldn't have to reinstall a bunch of the same software I'd already made, but obviously it didn't really work out as I'd expected.  Lots of different things in /opt/ and /lib/ that needed to be copied too.  Sure all my little binaries that I made worked, but not really the rest of them in there.

What I do now is just intentionally avoid storing things on "home" and have two hard-drives that I save most of my data too.  When I think it's about time to upgrade I just copy the home folder to one of those drives, install freshly, and then one-by-one pick out the configuration files I needed.  I like doing it this way too because sometimes with an upgrade there is a newer default configuration for something that I happen to like better so I can just keep the distro's config file if I happen to like it.

---

### Post by buzzingrobot on 2014-11-01
> **SagaciousKJB said:**
> 
  Otherwise it's like, saving a bunch of configuration files for a bunch of programs I don't even have, or must reinstall, etc. .

Don't understand why you would have "a bunch of configuration files" for packages you have not installed.

> I once tried to make a separate /usr/bin so that way when I had to clean install I wouldn't have to reinstall a bunch of the same software I'd already made, but obviously it didn't really work out as I'd expected.  Lots of different things in /opt/ and /lib/ that needed to be copied too.  Sure all my little binaries that I made worked, but not really the rest of them in there.

What I do now is just intentionally avoid storing things on "home" and have two hard-drives that I save most of my data too.  When I think it's about time to upgrade I just copy the home folder to one of those drives, install freshly, and then one-by-one pick out the configuration files I needed.  I like doing it this way too because sometimes with an upgrade there is a newer default configuration for something that I happen to like better so I can just keep the distro's config file if I happen to like it.


Some of the things you take on when you build and install packages from source include chasing down their dependencies, resolving conflicts, manually handling updates, rebuilding to add security patches, potentially rebuilding against new libraries after a reinstall, etc. (The packaging system is not aware of software installed from source tarballs.)  Any changes made to directories that you want to preserve should be backed up and restored after the new install.

One way to handle this sort of thing, in addition to the backups, is to craft a post-install script that restores the changes/additions you have made to the system, including rebuilding source-installed software, if necessary. Github is one place to look for examples of these post-install scripts.

You're right that applications sometimes alter the structure of their configuation files and/or put them in new locations. Well-behaved programs will migrate existing config files to the new approach. If not, it's a development failure that leaves users to clean up the mess.

---

### Post by SagaciousKJB on 2014-11-01
> **buzzingrobot said:**
> Don't understand why you would have "a bunch of configuration files" for packages you have not installed.




Some of the things you take on when you build and install packages from source include chasing down their dependencies, resolving conflicts, manually handling updates, rebuilding to add security patches, potentially rebuilding against new libraries after a reinstall, etc. (The packaging system is not aware of software installed from source tarballs.)  Any changes made to directories that you want to preserve should be backed up and restored after the new install.

One way to handle this sort of thing, in addition to the backups, is to craft a post-install script that restores the changes/additions you have made to the system, including rebuilding source-installed software, if necessary. Github is one place to look for examples of these post-install scripts.

You're right that applications sometimes alter the structure of their configuation files and/or put them in new locations. Well-behaved programs will migrate existing config files to the new approach. If not, it's a development failure that leaves users to clean up the mess.

Well I mean when you install a new clean version of Ubuntu, you will have your /home directory there but it's full of configuration files for software that is not currently installed.  I was saying it would be nice if there was some way to keep a "list" of which ones were installed to kind of mitigate that issue.  I guess doing it manually--i.e. just remembering what you install--would be a solution.

I'll take a look at those scripts, I'd be interested to see what all directories need to be navigated and copied from in order to produce a useable backup.  I was never able to get it done.

---

### Post by buzzingrobot on 2014-11-02
> **SagaciousKJB said:**
> ...when you install a new clean version of Ubuntu, you will have your /home directory there but it's full of configuration files for software that is not currently installed.  I was saying it would be nice if there was some way to keep a "list" of which ones were installed to kind of mitigate that issue.  I guess doing it manually--i.e. just remembering what you install--would be a solution.

I'll take a look at those scripts, I'd be interested to see what all directories need to be navigated and copied from in order to produce a useable backup.  I was never able to get it done.

For generating a list of installed packages, and reinstalling them, see this from the Debian wiki: [https://wiki.debian.org/ListInstalledPackages](https://wiki.debian.org/ListInstalledPackages). 

If you have removed packages included in a default install, and then do a new clean install, it will do a default install.  It has no awareness of what packages were removed from the previous install. If those packages are part of the default install of the new version, they will be installed. If you opt to not format /home, it does not avoid installing what it needs to install.

---

### Post by SagaciousKJB on 2014-11-02
> **buzzingrobot said:**
> For generating a list of installed packages, and reinstalling them, see this from the Debian wiki: [https://wiki.debian.org/ListInstalledPackages](https://wiki.debian.org/ListInstalledPackages). 

If you have removed packages included in a default install, and then do a new clean install, it will do a default install.  It has no awareness of what packages were removed from the previous install. If those packages are part of the default install of the new version, they will be installed. If you opt to not format /home, it does not avoid installing what it needs to install.

Neat, that will definitely make things easier down the line.

---

### Post by EnglishElectricAndy on 2014-11-02
One thing I've found with my (willingly admitted) limited experience of version upgrading is that kernels relevant to the previous release remain on my hard drive, e.g. moving from Xubuntu 13.04 to 13.10 left 3.8.xxx kernels available. Similarly going from 13.10 to 14.04 left me with a /boot directory with 3.11.xxx kernels in place.

No amount of "apt-get clean && remove && autoclean && autoremove" would get rid of these, neither would installing ubuntu-tweaks as this only seems to detect kernels applicable to the currently installed version. The only way that seemed to work for me was to temporarily change ownership of /boot via a 'chown' command in the terminal, go back to my file mananger GUI, open the boot directory, select the obselete kernel images and vmlinuz directories, right-click and select 'Delete'. Lo and behold, I've got over half a GB of disk space back!

Being a cautious soul I naturally 'chown'ed /boot back to root ownership afterwards.

Edit: I also 'sudo update-grub'ed just to make sure I hadn't been over-confident!

---

### Post by buzzingrobot on 2014-11-03
In my experience, kernels are not deleted during any updates, on Ubuntu or elsewhere. The assumption cannot be made that the user wants to use the latest kernel provided by that distribution.  Kernels may be installed from sources other than a distribution's standard repo, may be configured and compiled to meet specific requirements by a user, etc. The user may be a developer who needs to work with multiple kernel versions. Upgraders, then, should not delete existing kernels. Grub typically defaults to the latest kernel, but this is configurable by the user.

---

### Post by craig10x on 2014-11-03
However, old kernels ARE deleted when you Upgrade from one version of ubuntu to the next...that's been my experience...when doing the upgrade with the software updater, it leaves only the one you are using from your current version and adds on the latest kernel from the new version you are upgrading to...then when you re-boot of course you go to the new kernel for the new version you just moved into...

But, yes, when you get normal updates within the version you are using, and you get a kernel update, older ones do not get removed....you have to remove them manually...

---

### Post by d4m1r on 2014-11-04
While I've never had "unfixable" problems with any Ubuntu installation, some work is often required to get everything working smoothly again.

On one hand, I like when Update Manager pops up for me as it usually means bug fixes and new features BUT it is also a lot of work for me because I ad-hoc test all the packages that were updated to make sure they are OK.

Often, one bug is fixed while another is introduced :lol:

FYI, I'm still on 12.04 as I find it perfect for my uses (combination of stable and latest features) and plan on using it until it is supported....2017?

---

### Post by Mike_Walsh on 2014-11-04
> **EnglishElectricAndy said:**
> One thing I've found with my (willingly admitted) limited experience of version upgrading is that kernels relevant to the previous release remain on my hard drive, e.g. moving from Xubuntu 13.04 to 13.10 left 3.8.xxx kernels available. Similarly going from 13.10 to 14.04 left me with a /boot directory with 3.11.xxx kernels in place.

No amount of "apt-get clean && remove && autoclean && autoremove" would get rid of these, neither would installing ubuntu-tweaks as this only seems to detect kernels applicable to the currently installed version. The only way that seemed to work for me was to temporarily change ownership of /boot via a 'chown' command in the terminal, go back to my file mananger GUI, open the boot directory, select the obselete kernel images and vmlinuz directories, right-click and select 'Delete'. Lo and behold, I've got over half a GB of disk space back!

Being a cautious soul I naturally 'chown'ed /boot back to root ownership afterwards.

Edit: I also 'sudo update-grub'ed just to make sure I hadn't been over-confident!

Correct me if I'm wrong in this assumption, but as I understand it you can remove unwanted kernels via Synaptic; I've certainly 'house-cleaned' a couple of times myself in 'Trusty'.....wouldn't this also work for other redundant kernels?

I happily admit that I have NO experience of upgrading. I don't want to; I shall stick with LTS releases, as I value stability. I will probably give 16.04 a miss, wait until 18.04, and do a complete, fresh install. After all, the entire process, installing, and then re-installing the packages that I use, will take no more than a couple of hours.....two and a half, tops. A couple or three hours, once every four years, will NOT be a hardship!

Regards,

Mike.

---

### Post by craig10x on 2014-11-04
Yep...you can remove old kernels using Synaptic Package Manager, and it works really well...

---

### Post by Mike_Walsh on 2014-11-04
Hi, Craig.

I thought so. Mind you, I still wouldn't like to say if even Synaptic will only recognise the kernel versions as found in the relevant release of Ubuntu. I was browsing, and came across this back in August:-

[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

In fact, I've used the advice on this (and other related pages) for setting up every single one of my distros.....and it's all worked very well. That was when I first used Synaptic; and I must admit, I can see why many people like using it....once you get the hang of how to find stuff with it!

If you think about, even for installing new versions of all six of my distros, I'm not looking at more than a day's work all told.....I THINK I can live with that.

Regards,

Mike. ;)

---

### Post by craig10x on 2014-11-04
Hi Mike!  Yeah, you just type in the number (very carefully) for the exact kernel number you want to remove, and you see 4 files installed, then apply all 4 for "complete removal" and hit apply...once removed, re-boot!
You can check it on the package manager by typing the number again and you would see it is gone...it also gets removed from the grub menu automatically...
When i did it, i always did one kernel at a time and re-booted...i think that is the smoothest and safest way to do it....

Of course, now that i mostly upgrade, the ubuntu upgrader very graciously removes all the old kernels for me (except the one i am using when i do the upgrade of course)...saves me the work ;)

---

### Post by SurfaceUnits on 2014-11-07
Many people keep a script with the programs they install and run it after an upgrade   sudo apt-get install    their list of programs  ie

sudo apt-get install gimp gimp-help-common gimp-help-en gimp-texturize gimp-flegita create-resources flegita-gimp gimp-data-extras gimp-ufraw gimp-gutenprint gimp-lensfun gimp-plugin-registry gnome-xcf-thumbnailer gtkam-gimp gutenprint-locales icc-profiles ijsgutenprint pandora sane ufraw xsane

---

### Post by SagaciousKJB on 2014-11-09
> **SurfaceUnits said:**
> Many people keep a script with the programs they install and run it after an upgrade   sudo apt-get install    their list of programs  ie

sudo apt-get install gimp gimp-help-common gimp-help-en gimp-texturize gimp-flegita create-resources flegita-gimp gimp-data-extras gimp-ufraw gimp-gutenprint gimp-lensfun gimp-plugin-registry gnome-xcf-thumbnailer gtkam-gimp gutenprint-locales icc-profiles ijsgutenprint pandora sane ufraw xsane

Yeah I think this will probably be my approach in the future.  I tried using the dpkg list method, but it wanted to reinstall a lot of packages like coreutils, and at the end said it would remove bash? O_o  So I scrapped that and just wound up reinstalling everything manually anyway.  Seems like just making a simple list and remembering it would serve better.

Anyway I'm happily back on 12.04.  I can't say I really liked anything new about 14.04 but to be fare I only use XFCE

---

