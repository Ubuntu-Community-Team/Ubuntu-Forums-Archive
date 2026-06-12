---
title: "Concerned about future quality of Ubuntu versions"
date: 2015-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by timothylegg on 2015-12-27
I have been a user of Ubuntu since version 8 came out (I was a prior user of Debian since Woody, and before that FreeBSD)

I find something that works for me and tend to stick with it. About once every couple years, I might download three or four distros to experiment with and see how they behave because I know there will be the day that the OS I use will deviate from what I find useful.

I left FreeBSD when I found out you didn't necessarily have to compile source to install software. That was beauty of Debian.  I left Debian for two reasons: first I filed a bug report and my private email was posted publicly and it was spammed to death (so I assume that most users will only file reports once and never again). It was already apparent that Debian was chronically obsolete.  I left Debian when I saw Ubuntu was a light year ahead not what Debian could provide, so I changed again.

I'm concerned about the quality of Ubuntu installer tools.  The last two devices I installed on were failed installs in the sense that they simply didn't boot after install of the boot loader configuration failed. Boot loaders have been around for how many years and why can't they install correctly on 4 and 9 year old machines? It's not like we are dealing with ncutting edge technology.

I'll see if they get it right with 16.04 this spring.  If that installer also fails, then I'll have diminished confidence in the Ubuntu marque and will seek other approaches.

I hope that in the future, managers can track the number of installations that started, but never actually came live because that is a warning that there are problems with the installer because only about 5% are going to bother creating an account to solve the problem (if a solution exists in the first place)

---

### Post by QIII on 2015-12-27
Not everyone encounters those issues.

That said, for a distro to continue to move forward, it has to occasionally jettison code that would be compatible with older hardware and applications.  Otherwise, that part of the codebase would have to be maintained and that would take away from the resources to move forward.

The Linux community does not have unlimited resources.  Although "vanilla" versions of some distros can maintain compatibility with older hardware, some cannot.  To move forward with Unity, Canonical  had to assume that it would be installed on newer equipment able to handle it.  Other flavors, like Xubuntu, can still be installed on some pretty old hardware.

If Ubuntu doesn't work on older machines, Xubuntu or Lubuntu may.

---

### Post by Irihapeti on 2015-12-27
If you wish, you can get involved with testing the upcoming version. Some of that involves installing the ISO files and reporting any bugs that arise, and it doesn't require a high degree of expertise. See [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) for further details, if you're interested.

---

### Post by CharlesA on 2015-12-27
> **Irihapeti said:**
> If you wish, you can get involved with testing the upcoming version. Some of that involves installing the ISO files and reporting any bugs that arise, and it doesn't require a high degree of expertise. See [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) for further details, if you're interested.

That's a good idea. I haven't really run into any issues with Ubuntu when I used it, but I think the last version I actually used was 14.04 and it's sitting on a VM.

It might help if you provided more info - was grub actually installed, were you able to boot from a livecd and repair grub, etc.

---

### Post by ian-weisser on 2015-12-27
> **timothylegg said:**
> The last two devices I installed on were failed installs in the sense that they simply didn't boot after install of the boot loader configuration failed. Boot loaders have been around for how many years and why can't they install correctly on 4 and 9 year old machines?
You have been around the open-source communities for years, so you know this already: If you didn't file a bug report with sufficient information for a Triager to duplicate the problem, then --as far as anyone who can help is concerned-- it didn't happen.
What else can we do? We're not psychic, and we don't have access to your hardware.

> **timothylegg said:**
>  I hope that in the future, managers can track the number of installations that started, but never actually came live because that is a warning that there are problems with the installer
So...you want every Ubuntu install (installer and completed system) to phone home to Canonical servers with unique identification, performance data to validate a successful install, and reams of diagnostic data to debug installer problems.
That seems rather intrusive, and quite likely to be trumpeted as spyware by Canonical/Ubuntu's louder critics.
Perhaps there are simple, unintrusive ways to identify, debug, and report installer failures?

---

### Post by Irihapeti on 2015-12-28
> **timothylegg said:**
> ....  The last two devices I installed on were failed installs in the sense that they simply didn't boot after install of the boot loader configuration failed. Boot loaders have been around for how many years and why can't they install correctly on 4 and 9 year old machines? It's not like we are dealing with ncutting edge technology.


If you'd like help with fixing your existing issues, please start a support thread in the Installation and Upgrades forums. Unless it's 16.04, in which case the Development Release would be appropriate.

---

### Post by v3.xx on 2015-12-28
> why can't they install correctly on 4 and 9 year old machines?

Maybe you need to try one of the ubuntu flavors.  Mate, Lubuntu or Xubuntu?

---

### Post by Kale_Freemon on 2015-12-28
Another possibility is that the hardware may have problems. The older the machine, the more likely that a piece of hardware could be failing and causing the installations to fail.

Granted I'm betting it's lack of compatibility since, as others have astutely pointed out, sometimes distros have to let go of older code in order to move forward. And since Ubuntu has it's sights on being a modern operating system, it would make sense for them to occasionally let go of older code that would have otherwise allowed compatibility with those older machines.

Luckily, there are many different distros out there. One is bound to work on your older machines. I'd recommend starting with the lighter weight variants of Ubuntu since they're more dedicated to reviving older machines. For instance, I've got a 12 year old Dell that boots just fine with Lubuntu 14.04. But the main version of Ubuntu won't work on it.

Either way, the only machine I've ever had trouble installing Ubuntu on was an old MacBook that I gave to my girlfriend.

---

### Post by kansasnoob on 2015-12-28
> **Irihapeti said:**
> If you'd like help with fixing your existing issues, please start a support thread in the Installation and Upgrades forums. Unless it's 16.04, in which case the Development Release would be appropriate.

+1! I'd be very interested in learning why grub failed to install. On 4 to 9 year old systems things should be straight forward - simple msdos/mbr configuration - so it should be fairly easy to figure out what's happening.

---

### Post by buzzingrobot on 2015-12-28
> **timothylegg said:**
> ...I left Debian... I filed a bug report and my private email was posted publicly and it was spammed...

I have a faded memory of a flap about that happening a long time ago. I've filed Debian bug reports and, as far as I can tell, the email address wasn't scraped by spammers. 

>  The last two devices I installed on were failed installs in the sense that they simply didn't boot after install of the boot loader configuration failed.

Did you see a message from the installer that it failed to install the boot loader, or did the installer proceed normally and the machine fail to boot afterwards? Had the installer correctly identified the partition where the bootloader would be installed?

---

### Post by grahammechanical on 2015-12-28
> they simply didn't boot

I have known times when the boot loader failed to install. That was when I was messing around with btrfs and I did not have a certain amount of free space at the start of the disk.

I have also known installs that failed to boot but it was not to do with the boot loader not being installed. It was caused by ticking the box "Install third party software." Ticking that box will bring in not just some third party audio & video codecs but also a proprietary video driver.

I always install without ticking that box because the latest Ubuntu brings in the latest proprietary video drivers and the latest video drivers no longer support my video adapter. And this video adapter is about 8 to 9 years old.

Proprietary video drivers regularly drop support for older video hardware.

I have 2 installs of 16.04 development branch on hardware that was not top of the range when I built it in 2007. I have no problem installing and I never tick the box "Install third party software." One install runs on the open source video driver. The other install runs on a legacy proprietary driver.

I have been using the development version for more than 3 years. So, I expect problems but it been a long time since a daily ISO of the development version failed to install.

Regards.

P.S. Ubuntu does have a Quality Assurance team. See the bugs that are being reported for the daily images of the next release of Ubuntu. Anyone can become an ISO image tester.

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds)

[https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

---

### Post by timothylegg on 2016-01-01
That's actually quite interesting to me.  I have a way of finding problems, but I tend to do things that are different from the ideals that are set out of us to follow (such as using the classic gnome instead of unity).  I hope that wouldn't be too far out of the box.

Backing up the hard disk is pretty much non-issue for us.  dd is a wonderful, wonderful tool (and I haven't screwed up yet)

---

### Post by SantaFe on 2016-01-01
> **grahammechanical said:**
> I have known times when the boot loader failed to install. That was when I was messing around with btrfs and I did not have a certain amount of free space at the start of the disk.

I have also known installs that failed to boot but it was not to do with the boot loader not being installed. It was caused by ticking the box "Install third party software." Ticking that box will bring in not just some third party audio & video codecs but also a proprietary video driver.

I always install without ticking that box because the latest Ubuntu brings in the latest proprietary video drivers and the latest video drivers no longer support my video adapter. And this video adapter is about 8 to 9 years old.

Proprietary video drivers regularly drop support for older video hardware.

I have 2 installs of 16.04 development branch on hardware that was not top of the range when I built it in 2007. I have no problem installing and I never tick the box "Install third party software." One install runs on the open source video driver. The other install runs on a legacy proprietary driver.

I have been using the development version for more than 3 years. So, I expect problems but it been a long time since a daily ISO of the development version failed to install.

Regards.

P.S. Ubuntu does have a Quality Assurance team. See the bugs that are being reported for the daily images of the next release of Ubuntu. Anyone can become an ISO image tester.

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds)

[https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

Hmmm....I have an OLD Dell dimension 9150 and this video card: [AMD/ATI] RV620 LE [Radeon HD 3450]


I must have been one of the lucky ones because I just installed Ubuntu-MATE 15.10 a couple of days ago & checked the install third party software box and have the default drivers that Ubuntu-MATE installs.  Even checked for third party software & it eventually replies "No Third Party Software Found"

Checked in Synaptic under Radeon  and found 3 entries:
```

xserver-xorg-video-ati
xserver-xorg-video-radeon
libdrm-radeon1

```

Either I was lucky, or the graphics card I have is so old..... How Old Is it?  It is so old it was handed down from George Washington himself! ;)

---

