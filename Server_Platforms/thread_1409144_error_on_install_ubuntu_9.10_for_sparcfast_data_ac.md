---
title: "error on install ubuntu 9.10 for sparc//fast data access mmu miss"
date: 2010-02-17
forum: Server Platforms
---

### Post by philo_71 on 2010-02-17
hello,
I would like to install Ubuntu 9.10 on a Sun Blade 150 blade.
I create  cdrom iso burning with a 10x
was open I made a boot ok: boot cdrom

I get the following error:
fast data access mmu miss
i do 
probe-ide all
reset-all
always

fast data access mmu miss


see you
philo

---

### Post by miguel_lobos on 2010-03-15
I've been fighting the same battle without success yet. I've tried all of the tricks that have made earlier versions work, such as:

1. Ensuring that the latest version of OBP installed (4.17.1,)
2. Removed all but one of the physical memory sticks
3. Powered the machine down and unplugged it prior to attemtping the install
4. used the 'ide=nocdma' command appendage
5. Tried "netboot"ing from the 'release' version, and several of the 'daily build' versions

So, I was able to boot and install from an old Ubuntu Server 7.10 SPARC CD, (did the one memory stick trick and the unplug trick listed above), but since that release is now more than 3 years old and it is not an 'LTS' release, the update repositories are no longer available for this release on the 'official' ubuntu.com package sources. 

To upgrade, I've read elsewhere in either official Ubuntu.com documentation or this forum that one must go through each release cycle to be successful in getting to the desired end state. :-/ I have verified that jumping from the 7.10 release using the 'cdromupgrade' script on the 9.10 CD doesn't work for me, as the python script choked before I got very far.

I just downloaded the 8.04.1 CD image, and running the 'cdromupgrade' script from the root of the CD choked again (though not the same way the 9.10 disc did). So, I crossed my fingers and booted this disc, and the install is running well so far. I'll post back later with the final result, and hopefully from here, I'll be able to use apt-get to upgrade through the rest of the ported releases to get to the current release. 

BTW, I'm not yet running an X-Windows desktop on this system, so I can't comment on how well / suitable this configuration is for any of the run-of-the-mill desktops.

Wish me luck, and I'll try to write the story / saga of what it takes as this mystery unfolds...

Lobos

---

### Post by miguel_lobos on 2010-03-16
> **miguel_lobos said:**
> ...I'll post back later with the final result, and hopefully from here, I'll be able to use apt-get to upgrade through the rest of the ported releases to get to the current release... 


Ok,

So I had some idle time yesterday afternoon, and got to play around with several releases and attempts. Booting from the 8.04.1 or later port Ubuntu server CDs on the Blade 150 in my posession results in the image booting ok (well, 8.04.1 and 8.10), and subsequent complaints that the installer can't find the CD-ROM (Actually, its an IDE-attached 16x DVD-ROM labeled Model SR-8588-B, can't see who the manufacturer is). The Jaunty and Karmic releases fail with complains of "Fast Data Access MMU Miss" errors.

Since I have another Sun machine running Solaris that I had previously configured as a tftp server, I attempted several netboot images (Hardy, Intrepid, Jaunty, Karmic and even a pre-release Lucid), with varying levels of success in booting. Anything newer than Jaunty also crashes at boot some a "Fast Data Access MMU Miss" in /packages/obp-tftp. Hardy and Intrepid get most of the way through the install before hanging (looks like right around the time SILO is being installed).

This may be an understatement, but I'm coming to the conclusion that the Ubuntu releases don't seem to install smoothly on Blade 150, or in later port releases, at all. The bottom line is this - every attempt to install any Ubuntu release from the last three years on this machine has not resulted in a successful post-install boot. In my book, that meets the criteria for a failed install. Sure, I can boot into rescue mode from either a CD or netboot, but I shouldn't have to.

I'm sure if this were an active discussion, that there would be plenty of advisement that I somehow have a hardware problem, but since other operating systems install cleanly from CD / DVD or TFTP booting on this box, I am less inclined to believe that this machine has a true hardware fault. Just last week I successfully installed Solaris 10 ( 10/09 U8 ) from DVD on this machine, and I am now finishing up what has been a smooth Debian 5.0.4 installation using the netboot from my local TFTP server / Internet package source method.

I wished for a working, current Ubuntu port on this platform, but since I've blown my time budget (for now), I guess I'll settle for a working Debian machine at this point.

Lobos

---

### Post by lnelson on 2010-03-16
I was very glad to find your post yesterday, especially since I was working on the same problem on the same day.

The problem with the install hanging is indeed because of SILO.  I found a thread about this:

[https://bugs.launchpad.net/ubuntu/+source/silo-installer/+bug/194032](https://bugs.launchpad.net/ubuntu/+source/silo-installer/+bug/194032)

Basically, SILO is prompting for user input but there is no way to interact with it from the install scripts.  I just did a ctrl-C to abort the SILO install then proceeded with the rest, of which there wasn't very much.  Then I had to boot back into rescue mode and run silo manually.  The silo.conf file is already set up properly.  After that, the system booted into the new install.

I started with 8.04.1 and I am now in the middle of the upgrade from 8.10 to 9.04 on my way to 9.10.

I'm doing this on a Netra120.

---

### Post by philo_71 on 2010-03-26
i found the error another error.
the error is the video card XVR-500 are not supported by debian/Ubuntu
the video card compaibility is XVR-100 or XVR-300 with ati chipset


best regards
philo

---

### Post by thebigob on 2010-06-03
This is an excellent post which will explain all about Ubuntu on sparc issues:
[http://ubuntuforums.org/showthread.php?t=1438225&highlight=sparc](http://ubuntuforums.org/showthread.php?t=1438225&highlight=sparc)

---

