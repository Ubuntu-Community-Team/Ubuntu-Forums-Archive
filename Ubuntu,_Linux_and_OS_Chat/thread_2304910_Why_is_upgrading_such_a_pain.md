---
title: "Why is upgrading such a pain?"
date: 2015-12-01
forum: Ubuntu, Linux and OS Chat
---

### Post by ejoftheweb on 2015-12-01
I've recently upgraded to 15.04 and I'm hoping it will hang on until 16.04 LTS comes along.

Ideally, an upgrade should keep all my system settings. But it's a long time since I've had a smooth upgrade experience with Ubuntu.
I'm a long-term Linux user and have tried many different distros over the years since I ditched Windows in 2000 - Slackware, Mandrake, Gentoo, Debian, and for the last five years or so, Xubuntu. 

This latest upgrade has destroyed all my existing installed applications.  Every one of them, as if it were a fresh install to a new machine. Fortunately it hasn't destroyed any user data, but I'm going to move the whole of /home to a separate drive, and unmount that before I do another upgrade because, frankly, I don't trust it. 

Reinstalling packages varies from being a minor inconvenience to a major annoyance. Like many actual users, I use one or other of the OpenOffice forks as my Office software; I find it has better interoperability with MSOffice than Abiword/Gnumeric, Currently LibreOffice5. Need to reinstall that. At least that's only half an hour or so compared to the two days it took to emerge under Gentoo!  And delete all the bloatware that comes in the main distro, which in which category I put Thunderbird and Abiword/Gnumeric. It comes to something when I am complaining about bloatware in a supposedly lightweight distro. 

mdadm should be in the main distro anyway. But upgrade deletes mdadm.conf, so I suddenly find a whole array of data just lost. 

A whole load of udev rules files got overwritten. You have no idea how much of a pain it is to rewrite all of those. I develop Android apps, and adb got deleted along with the udev rules for the attached debug/test devices.  Best part of a day lost to getting the debug/test devices working again. 

The overwriting of the whole /var tree is, I think, particularly egregious.  I may be going against the grain here but I put all large-scale media such as music in /var/media, and symlink users' ~/Music directories to it. Luckily that's just a mount-point for the md array that disappeared with mdadm.  It also deleted a whole subtree of /var/log that I use for my development work.

Upgrading to 14.04, I upgraded inline by taking the option presented in the reminder popups. Never again; I was forced to do an almost total reinstall as the machine was unusable afterwards.  This time, I thought I'd learned my lesson, so I downloaded the ISO and ran it as a live disk from a USB drive and took the "upgrade" option rather than "install alongside". Why is install-alongside even an option? who on earth would seriously want to dual-boot slightly divergent versions of Linux? 

 I hope I haven't come to the end of the road with Ubuntu.  I guess I'll give it another year, but if the upgrading experience doesn't improve by the time we get to the beginning of the alphabet again, I might seriously have to look elsewhere.

---

### Post by coffeecat on 2015-12-01
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Bucky Ball on 2015-12-01
Well, the bad news is you may have added to your pain, as 15.04 is only supported until January 2016 at which time you will need to upgrade to 15.10, then 16.04 LTS sometime after next April where you can put an end to your pain for five years. 

A clean install of 14.04 LTS or 15.10 is upgradeable directly to 16.04 LTS in the latter half of next year. 

Some folks don't go near the net upgrade. I, personally, have never had an issue. Keeping a reasonably vanilla install with few manually added PPAs (and disabling any I have installed prior to upgrade) and making sure the machine is up to date prior to the upgrade may have been my saving grace(s). Or just plain luck. There are plenty of horror stories here and elsewhere like yours, though. :|

---

### Post by buzzingrobot on 2015-12-01
Release upgrades in any OS are not done by magic. The upgrade software is not telepathic. The more a system has been altered away from the baseline, the greater the risk of breakage. Anything that is more than just bumping a package version number -- say, changing from upstart to systemd -- is going to be especially sensitive to changes a user has made to the installed system.  E.g., special tweaks made to the "old" are probably not going to survive the transition to the "new".

Putting user files in /var, or any other part of the tree the system considers its own, seems to me very likely to cause trouble.

Putting your home folder on its own partition/drive is a very good idea. Put *all* your user files, etc. there. That way, you can, if you want, do a clean install of a new version and simply tell the installer to avoid formatting the folder. 

Packages can also be excluded from *updating* but I don't know if the exclusion is, or can be, honored by an *upgrade*.

There are also ways to generate a complete list of all packages installed on a system. and then use that list to (re)install packages. You could do that before an upgrade, then clean up your sources.list, etc., files to remove PPA's and other unsupported repos, do the upgrade, restore your sources, then reinstall packages that somehow went missing.

---

### Post by grahammechanical on 2015-12-01
I have done upgrade testing and everything worked perfectly. But I did the test with a fresh install of the older version just to test the upgrade path. So, I can say that going from default to default works great.

Once, as an experiment, I tried upgrading from a fresh install of Ubuntu 9.04 onwards & upwards to 14.04. I got as far as 11.04 (the switch from Gnome 2 panel to Gnome 3 & Unity) when the UI got so messed up as to be unusable. But I did get in some practice doing end of life upgrades.

Oh, do not forget to do the upgrade with an open source video driver and not a proprietary driver. The proprietary video driver will also get upgraded and if the new version has dropped support for the video card, then no desktop is the result.

Regards.

---

### Post by kansasnoob on 2015-12-01
> I downloaded the ISO and ran it as a live disk from a USB drive and took the "upgrade" option

I think the others replying so far didn't notice that :)

Upgrading using the live media is an altogether different process than upgrading via 'release-upgrader'. Probably a lot of Ubuntu users do run dual/multi-boot systems and therefore may never have been offered the option. This screenshot is from Precise but it hasn't changed other than artwork:

[ATTACH=CONFIG]265868[/ATTACH]

I've never used Xubuntu, mostly Ubuntu or Ubuntu GNOME, but I've performed such upgrades and they do pretty much just what it says - keeping docs and other files, reinstalling software **[COLOR="#FF0000"]where possible[/COLOR]**, and wiping system wide settings. I highlighted "where possible" because of it's importance. 

I believe that the only software that can be reinstalled during the "live" upgrade is that which either resides on the live media or which is available via the software sources enabled on the live desktop - typically only main? I know that the universe repo is not enabled on either Ubuntu or Ubuntu GNOME live media, and 'libreoffice' is in universe, so such a package can not be reinstalled during the upgrade. The same is true for packages installed via PPA or some other source such as a tarball or dot_deb.

Both methods of upgrading present risks, and those risks increase with every tweak and package installation, particularly when packages have been installed from any source other than the Ubuntu repos. The reason for that is generally just as simple as an improper soname that tells the release-upgrader that a package is newer than that available in the repos so it loses it's mind.

The safest bet is to avoid frequent upgrades by using only the LTS versions. Xubuntu's LTS versions, the latest being 14.04, are supported for 3 years from the time of release. Also always plan on an upgrade going poorly and have a backup of all your data just in case a fresh install is required.

> Why is install-alongside even an option? who on earth would seriously want to dual-boot slightly divergent versions of Linux?

I honestly think most experienced users use the "something else" option which offers advanced installation options so we're totally in control of what gets erased and what gets kept, but there is a learning curve involved. But I multi-boot for testing purposes. And on those machines where I run a stable release of Ubuntu for production use I have them set up so I can swap between a fresh install and an old stable install until I get all the kinks worked out.

Like the machine I'm on right now has three drives. The 80GB drive is just for testing upstream Debian stuff, but the two 160GB drives get used for alternating stable and testing releases:

```
lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  105GB  105GB   primary   ext4            boot
 2      105GB   160GB  54.5GB  extended
 8      105GB   123GB  17.5GB  logical   ext4
 7      123GB   141GB  17.5GB  logical   ext4
 6      141GB   158GB  17.3GB  logical   ext4
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.7GB  76.7GB  primary   ext4            boot
 2      76.7GB  80.0GB  3289MB  extended
 5      76.7GB  80.0GB  3289MB  logical   linux-swap(v1)


Model: ATA ST3160318AS (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  137GB  137GB   primary   ext4            boot
 2      137GB   160GB  23.0GB  extended
 6      137GB   157GB  20.0GB  logical   ext4
 5      157GB   160GB  3040MB  logical   linux-swap(v1)

```

Or this one from the box I typically use for upgrade (via release-upgrader) testing has only one 500GB drive so I swap between /dev/sda1 and /dev/sda2 for current stable and latest testing versions:

[ATTACH=CONFIG]265869[/ATTACH]

Is any of that clear as mud?

---

### Post by Tadaen_Sylvermane on 2015-12-01
First off I suggest you keep a virtual machine of your existing OS if you decide to go the direct upgrade route. Do it on the vm first, make sure all is well then go bare-metal. I have yet to have success in any of my tests upgrading either Ubuntu or Debian without some kind of issues, and I am honestly far to lazy to go chasing the problem down. It's faster for me to get the new version .iso, install it, and I have a script to do the setup for me that I run after initial boot. To keep things easy I always keep a /data partition and link folders into /home/$USER so backups are trivial, they are already there waiting for my script to symlink them into place.

---

### Post by tehardis on 2015-12-01
I have used Ubuntu since 8-04. I am no computer whiz. I like what Ubuntu has to offer, but have had issues upgrading. It's a learning experience. I am learning more about the booting options DVD vs flash stick  etc, etc. I do make sure I have back ups to needed files in case things do not go smoothly. I feel Linux users accept/ want an OS that requires some user input.

---

### Post by monkeybrain20122 on 2015-12-02
Why are all you people recommending all these complex routes to "upgrade" instead of just telling the OP the obvious?  Forget about "upgrade", backup data and do a clean install, it takes 15 minutes and save a lot of headaches and troubles down the line. Also I recommend a separate /home partition (choose "something else" in installer instead of automatic) that way next time you just need to reinstall into the / partition and leave all the user data and settings alone.

I find "upgrade" makes no sense at all. If your system is vanilla and pristine it would take you no time to reinstall your software so in about 30 minutes you are all good to go (15 for installing OS, 15 for installing software max) while "upgrade" will take you god knows how long. On the other hand if you have a highly tweaked system you would think that upgrade will save you the troubles of going through the tweaking again, but in that case "upgrade" will likely leave you with a broken system because the upgrader gets confused by all your customization, that is, in the only scenario where one has the incentives to go the "upgrade" route the process may very well fail. So what is the point unless you want to test Ubuntu's upgrader and file bug reports?

---

### Post by QIII on 2015-12-02
It is not deliberately made so, any more than German is made to be difficult for English speakers.

The problems is that often English speakers expect German to be just like English.

Most people have grown up with Windows.  To most people, PC = Windows.  The easiest way to master Linux is to simply not expect it to be Windows.

You didn't spring forth fully formed and armed for battle from the head of Zeus and leap into the fray with Windows.  Humans tend to forget that they were once babes in Windows, too.  This is a new language.  It takes time to learn.  I was not bilingual at the start.  I studied German for four years in High School and four years at the University to get caught up to the proficiency I had in English.

With regard to computers, I started out with Unix.  Linux was a refreshing chance to go home from my sojourn with Windows.

No.  Linux is not for nerds.

And if Windows does not have update or upgrade problems, please explain to me why I spent so many years helping out on Windows forums just as I do here now.

---

### Post by kansasnoob on 2015-12-02
> Why call it "flavour" when the rest of the world calls it "version"?

Because "version" refers to the release date, eg; 14.04 = Trusty, 15.10 = Wily, etc. OTOH "flavor" refers the desktop environment or specific targeted usage.

---

### Post by kansasnoob on 2015-12-02
> Like it or not, Windows is the bench mark. Making software or an OS different to Windows does not make you better. Making software or an OS that IS better than Windows makes you better !!! Windows does not have update or upgrade problems, that I know of !!! 

That is absolutely laughable :lolflag:

If Windows is your cup of tea please use Windows, but leave those of us who want an operating system that works alone, OK :D

---

### Post by tehardis on 2015-12-02
Do you think that some Linux issues may have something to do with the hardware it is installed on? I had received a recommendation when upgrading from 12-04 to 14-04. My video drivers were not all they needed to be for Utility to work trouble free.

---

### Post by mastablasta on 2015-12-02
> **tehardis said:**
> Do you think that some Linux issues may have something to do with the hardware it is installed on? I had received a recommendation when upgrading from 12-04 to 14-04. My video drivers were not all they needed to be for Utility to work trouble free.


if you use proprietary drivers then those can cause issues. I believe in 13.10 they were disabled first automatically then I did the upgrade. proprietary drivers, as I understand it, patch the kernel. so they "mess around" with the core of the OS.

the more of hw you have that uses opensource drivers (drivers part of kernel/core) - e.g. Intel, HP, Atheros (!?), AMD (ye old GPU) the easier & more painless update or upgrade for sure. 

note that when you are using proprietary drivers and due to the way Linux manages packages , you can get a text mode only even during regular OS updates. usually with GPU drivers of course. Linux kernel is replaced/patched, but not the proprietary closed source driver and they end up incompatible with each other. rare to happen, but it did happen to me on one occasion.

---

### Post by howefield on 2015-12-02
Thread cleaned liberally and for the benefit of everyone, but one in particular...

[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

> Trolling, Attacks and Flaming: These are always forbidden.

    Trolling is posting in a way that provokes emotional responses.
    Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.
    Flames are messages that personally attack or call any people names or otherwise harass. These, along with any generally condescending posts will be edited or removed at the moderators discretion.

> Profanity: We have users of all age groups and of all tolerance levels where profanity is concerned. A language filter is in place to catch most major forms of profanity that may accidentally be used. Do not attempt to circumvent the language filter by using variations or slight misspellings of profanities.

---

### Post by furtom on 2015-12-02
> **neil36 said:**
> From the out side looking in, it appears to a bunch of computer guru nerdy type people wanting to prove their superior knowledge...That is not directed at anyone, it is simply my opinion of what it looks like when standing on the out side looking in. 

I also agree that it seems (appears) that it is deliberately made difficult for anyone that is not a computer guru nerdy type person.

Well, Neil, you don't appear to be a troll, so I won't treat you like one. But you have to remember, when you come to play in a new sandbox, you have to learn the culture before making judgments.

Linux has a reputation (among the uninformed) for being unfriendly to newbies. Nothing can be further from the truth, especially regarding Ubuntu and this forum.

Linux may be less accommodating to those who display an unwillingness to do a minimum of searching, reading and perhaps thought.

> I am no dunce when it comes to computers, but it took over 2 weeks just to install Ubuntu because it is not made clear that a FAT32 USB is needed.

Perfect example. No one is calling you a dunce. However, creating a bootable usb stick is extremely well documented. I can think of at least half a dozen ways of doing it off the top of my head. Most of which use GUI tools that would have formatted your stick correctly without even mentioning it.

I don't know which method you tried, but it obviously wasn't one of those. No problem. But when it didn't work, a Web search would have uncovered many, many alternate methods for you. A bit of reading would have set you straight on the requirements. A polite post here in the new to Ubuntu section would have received a helpful response instantly.

> Or for another example, why is it called a "package" when almost every computer USER on the planet calls it software or software program ? Apple have been successful in making people call it "App" (application) but it is still a software program...and Linux in all it's "flavours" is just no where near big enough to be making up clever word plays...The last big attempt got their **** sued off when they tried to play the name "Lindows"... Why call it "flavour" when the rest of the world calls it "version"?... I could go on and on !

Back to the new sandbox analogy. You have to learn new terminology when you join a new group. This is completely normal.

Linux isn't just a piece or software to run your computer; it's a culture, a group and a way of doing things outside the norm. Perhaps you are not interested in that. That's OK, too. Nevertheless, if you have decided to use Ubuntu, and are coming to this form for help and learning, you have to pick up the lingo. No one is going to make any apologies.

> Like it or not, Windows is the bench mark. Making software or an OS different to Windows does not make you better. Making software or an OS that IS better than Windows makes you better !!!
I think it is better! By every and any measure. You don't have to agree, but it seems you must at least be curious about it or you wouldn't be here.

> Windows does not have update or upgrade problems, that I know of !!!
This is wrong on so many levels!

First of all, windows upgrade problems abound as any quick search of other forums will show you. We're not here to talk about those.

But on a more fundamental level, you can not compare the two procedures! If you upgrade windows, what are you upgrading? It's kernel, certainly, it's ancillary programs and processes, and the UI... Maybe a few extras like the web browser. That's about it. That's fair. Windows is an OS and you are upgrading the OS. There is no reason to expect it to upgrade your office suite, productivity tools, and all your other programs. You are on your own with them.

However, an ubuntu upgrade pretty much updates all your software, your utilities, libraries, core and supplementary packages, your office suite, etc. Basically everything.

Furthermore, all the stuff that windows upgraded is closed source, binary, locked down. MS had total control over what was on your computer and what it is upgrading. This procedure certainly should go well &#8211; though sometimes it doesn&#8217;t.

On linux, however, nothing is further from this scenario. You have total control over your system and what you are running. You can upgrade outside of official channels, remove whatever you want, move stuff around, mess with configuration files, and compile anything you can't find any other way.

Ubuntu tries to handle all that and usually does a pretty good job of it. And when it doesn't, you'll find a lot of people here ready and willing to help.

Oh, and BTW, the software and the community support all comes without charge.

I hope you will think on these things before you post again.

Best,

---

### Post by help_me2 on 2015-12-02
I always clean install the root partition, and leave my home folder untouched. Never have a problem.

---

### Post by buzzingrobot on 2015-12-02
> **kansasnoob said:**
> That is absolutely laughable :lolflag:

If Windows is your cup of tea please use Windows, but leave those of us who want an operating system that works alone, OK :D

Yes.  Entire web sites are devoted to telling Windows users which updates to accept and which updates to avoid.

As for upgrading from one version to the next, there are plenty of reports from people who claim their Windows 10 upgrade didn't work. Most likely for the same reason that Ubuntu upgrades go south: People changed something and either forget about it or never understood what they were changing in the first place. 

(My vote for most common cause of Ubuntu upgrade failures is uninformed PPA use:  People copy-and-paste a few lines from a site or a blog to grab a driver of some sort from a PPA.  They pay no attention to the fact that a bunch of dependencies are also being pulled in, and that one or more of them replace core packages.  Nothing goes wrong for months until they try a version upgrade, which fails because those PPA packages created a dependency scenario the package manager cannot resolve.)

---

### Post by mastablasta on 2015-12-03
> **buzzingrobot said:**
> 
As for upgrading from one version to the next, there are plenty of reports from people who claim their Windows 10 upgrade didn't work. Most likely for the same reason that Ubuntu upgrades go south: People changed something and either forget about it or never understood what they were changing in the first place. 

or for example were told to role back the upgrade: [http://www.pcworld.com/article/3002188/windows/dell-hp-support-agents-advise-callers-to-ditch-windows-10.html](http://www.pcworld.com/article/3002188/windows/dell-hp-support-agents-advise-callers-to-ditch-windows-10.html)

---

### Post by rewyllys on 2015-12-03
> **help_mSe2 said:**
> I always clean install the root partition, and leave my home folder untouched. Never have a problem.
That accords with my experience.

Separate partitions for / (root) and /home are the easiest and best path to painfree upgrades.

---

### Post by SurfaceUnits on 2015-12-04
As Britney would say, anyone who doesn't backup their stuff be whack. I've always upgraded from LTS thru interims to the next LTS when I do a fresh install. The most troubleshooting I've had to do is run DPKG from Recovery Console to clean up a few items. As Britney would say, mixing your data with OS files be whack.

---

### Post by Andrew_Constantine on 2015-12-04
Probably the best way I do 'upgrades' is have a separate /home/ partition and keep that intact. Or since everything I need is on an external drive I just do a whole fresh install, install software i need and I'm off and running. That is really the best way to do an upgrade, no matter the OS. Even though Windows and OSX are trying their darnedest to make users do in-place upgrades.

---

### Post by cariboo on 2015-12-04
I usually do upgrades every 6 months, when the next version toolchain is released. I've never had any problems, except when I have the proposed repository is enabled. I have /home on a separate partition, so none of my data gets overwritten.

---

### Post by buzzingrobot on 2015-12-04
Application sometimes change the composition and/or location of the config files they store in a user's /home directory.  If that happens during an upgrade, manual intervention may be needed to sort things out if an app botches, or doesn't bother to do, the migration.

---

### Post by mikodo on 2015-12-04
I have never done a release upgrade. In my earlier days with Ubuntu, I broke it so often when tinkering that I would often resort to new installs. From that experience and the advice of more knowledgeable people, I try to prepare in advance for new fresh installs. Have a list of my configurations and software that I am going to want installed available is helpful. This takes effort and time granted but, some of the process can be automated too. Oh, and I keep my data partition separate and then just symlink to it from new installs.

---

### Post by furtom on 2015-12-07
> **buzzingrobot said:**
> Application sometimes change the composition and/or location of the config files they store in a user's /home directory.  If that happens during an upgrade, manual intervention may be needed to sort things out if an app botches, or doesn't bother to do, the migration.

I don't understand this.

Even if you have /home on a seperate partition, you still tell the installer where it is and that it is /home. You just don't format it. Those config files will then be upgraded as they should be.

---

### Post by furtom on 2015-12-07
> **mikodo said:**
> Oh, and I keep my data partition separate and then just symlink to it from new installs.

I do this, too. But not with all of /home. Mainly because my data disk is USB.

---

### Post by Bucky Ball on 2015-12-07
> **furtom said:**
> I do this, too. But not with all of /home. Mainly because my data disk is USB.

More or less the same as Mikodo is describing, except their method keeps your user settings and config files in /home directory in / and not in the /home partition on the USB. Both method's have their advantages and disadvantages, depending on what you're after. :)

With the symlink method, if you clone or backup the / partition you have the lot, all user settings and the OS config. With the separate /home partition you would need to back up the user settings from there and also the / partition.

---

### Post by matt_symes on 2015-12-07
> **furtom said:**
> I don't understand this.

Even if you have /home on a seperate partition, you still tell the installer where it is and that it is /home. You just don't format it. Those config files will then be upgraded as they should be.

If i understand correctly, that's not what buzzingrobot is saying.

Re-read it but keep in mind that when you upgrade Ubuntu distribution releases, you also upgrade all the applications software to the versions in the new Ubuntu release.

That updated applications software may store its configuration files in a different location in the home directory than the previous version of the software.

buzzingrobot will correct  me if i am misunderstanding him.

---

### Post by buzzingrobot on 2015-12-07
> **furtom said:**
> I don't understand this.

Even if you have /home on a seperate partition, you still tell the installer where it is and that it is /home. You just don't format it. Those config files will then be upgraded as they should be.

They *should be*, yes, but sometimes they aren't. 

User edits may need to be redone, as well, especially if an app uses new config files in a new location.

---

### Post by furtom on 2015-12-07
> **buzzingrobot said:**
> They *should be*, yes, but sometimes they aren't. 

User edits may need to be redone, as well, especially if an app uses new config files in a new location.

OK. Got it. thank you matt and sorry buzz. I thought you were saying you didn't choose the partition as /home during install.

Still, it shouldn't happen with packages within the standard instillation!

---

