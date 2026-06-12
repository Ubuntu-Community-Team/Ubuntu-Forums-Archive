---
title: "My bad experiences trying to install 16.04 final beta"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by agronholm2 on 2016-03-28
So Xenial final beta was out, and I was looking forward to trying it out. I had 15.10 desktop installed and so I did do-release-upgrade. Not everything went smoothly some packages failed to install, possibly due to third party packages. OK, then I removed the offending 3rd party packages and fixed with apt-get install -f and apt-get dist-upgrade. Rebooted. X loaded but Unity did not. My desktop was broken. Looking at systemd logs, it seems compiz was constantly segfaulting. No amount of upgrading would help. So I decided to wipe the slate clean and try installing from scratch.

I created a USB stick using my Windows workstation and booted my laptop with that. My first surprise was the broken graphics ([image here]("http://imgur.com/PKmfHYG")).
The window content was partially on top of the title bar, WTF? Also, the desktop size seems to be far larger than the screen, why is this happening? 15.10 didn't have these problems.
Trying to continue, I clicked on the continue button (Jatka), at which point the cursor turned to the rolling ball for several minutes (this happened with 15.10 too).
When that was over, the buttons went grey and it took me several restarts to figure out that it was actually displaying a modal dialog off-screen. I worked around that by moving the installer window towards the upper left corner of the screen so the dialog's title bar was then displayed just within the viewport so I was able to drag it up to see it completely.

I was then presented with the location selection screen and the preselected choice was correct, so I pushed Next. Then, I was asked to select my keyboard layout, but I guess I hit [this bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1549529") because US English was the only choice. I tried the keyboard layout autodetection procedure too but the only choice it resulted in was the Latvian keyboard.

Next, I got into the partitioning setup phase. I then repartitioned my drive, adding one big btrfs partition as / and then a second partition for swap. But after that, at the point where it tried to install grub, grub crashed. I was then shown a dialog that told me a bug report would be sent after I closed the window. But the "close" button had no effect. At this point I decided to cut my losses and reinstall 15.10. That process at least worked flawlessly.

For a release that was supposed to be "blocker free", this amount of bugs is appalling. And I hadn't even gotten to the point of trying the OS after installation.

---

### Post by vasa1 on 2016-03-28
Describe your computer's specs.

---

### Post by kansasnoob on 2016-03-28
> For a release that was supposed to be "blocker free", this amount of bugs is appalling.

It's a Beta not a final release, meaning it's still in development. Even then it's not uncommon for bugs to be present in the initial release, most of which will be fixed by the first point release (16.04.1). The only way things get fixed is by diligently filing bug reports and following up on them.

---

### Post by grahammechanical on 2016-03-28
I put in another install of a Xenial daily ISO image just the other week. The install went well and the resulting installation works fantastic. But then in all the years I have been installing development ISO images I have only once ever had to use an F6 option to load the live session. And that was years ago. The problem was soon fixed in later daily ISO images. I must have pretty ordinary hardware.

I do not often do it myself as I like a bit of excitement but we should really read the release notes. There might be something in there relating to our hardware.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Upgrading from 14.04? Don't do it at this time. Got AMD graphics? No AMD proprietary video driver in 16.04. Swap partition not being created during installation? It is a known bug and there is a work around. 

From the posts on this forum I would say that we do not have to be installing a beta version of Ubuntu to have problems installing Linux. I cannot count the number of times someone has said, "the install went well, but on restart ..." It makes me smile. If an install does not get me to a working desktop, then the install has failed as far as I am concerned.

This Xenial Xerus 26 week development period has been another boring development cycle as far as breakages are concerned. So, I do not agree with the conclusions of the OP.

Regards.

---

### Post by ventrical on 2016-03-28
> **agronholm2 said:**
> 

Next, I got into the partitioning setup phase. I then repartitioned my drive, adding one big btrfs partition as / and then a second partition for swap. But after that, at the point where it tried to install grub, grub crashed. 

There have been big problems with btrfs + grub.  And even if you get successful install there will be problems later on down the road if you decide to add/remove partitions.

Try ext4 file system.

regards..

---

### Post by agronholm2 on 2016-03-31
Lenovo ThinkPad T550, 16 GB RAM, Intel+nVidia 940M graphics.

---

### Post by agronholm2 on 2016-03-31
> **ventrical said:**
> There have been big problems with btrfs + grub.  And even if you get successful install there will be problems later on down the road if you decide to add/remove partitions.

Try ext4 file system.

regards..

Well, I've been running 15.10 since it came out, no problem. And after the 16.04 beta2 installation failed, I reinstalled 15.10 with the exact same settings and it worked flawlessly.

---

### Post by sudodus on 2016-03-31
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Is 16.04 LTS working well from a USB drive?

---

### Post by agronholm2 on 2016-04-03
> **sudodus said:**
> [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Is 16.04 LTS working well from a USB drive?

I'm not seeing the graphical glitches when I boot using the "Try Ubuntu" option.
All my problems have workarounds (like booting in legacy BIOS mode instead of UEFI). It's just sad to see regressions in the installer for no good reason.

---

### Post by sudodus on 2016-04-03
Have you tried with a ***proprietary nvidia driver*** for your graphics chip? I think such a driver is used automatically when you "Try Ubuntu", but you have to install it manually in an installed Ubuntu system.

There could also be temporary problems in 16.04 LTS, because it is in a rapid developing phase. I have a glitch that involved webkit and the nvidia 304 driver (webkit works with the free nouveau driver). This glitch appeared a couple of weeks ago, and things like that can be expected before a version is released :-P

---

