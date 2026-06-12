---
title: "Installing 10.04 Server from USB will not work."
date: 2010-07-23
forum: Server Platforms
---

### Post by rexless on 2010-07-23
Greetings.

What is wrong with the Ubuntu installer?  I am trying to install 10.04 Server from either a USB CD-ROM or a USB memory stick and no matter what I try (and I've tried every trick I've been able to find so far).  I regularly install other OS's using these methods without any problems or workarounds required.  Why is the Ubuntu installer so screwed up?

When I try to install from USB CDROM the installer boots, asks me all those keyboard questions, and dies at "Detect and mount CD-ROM".  It askes me if I want to load CD-ROM drivers from removable media :(
I've even tried various things such as using the command prompt to manually copy the iso to /root/ and mount the iso to install from... no dice.

So next I tried using the Universal USB Installer tool as outlined at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
The USB stick is created and it will also boot up the installer as expected.  This method stops at the same point as the USB CD-CDROM.

Other than rip open the server and hack in an ide/sata CDROM drive (there's no room for one), what does one have to do to make this work?

---

### Post by sylvester_0 on 2010-07-23
Have you tried Unetbootin? I'm not sure if it will create "server" installation disks. Also, I'm pretty sure you can just DD (dd if=ubuntu.iso of=/dev/sdX) the ISO to USB sticks.

---

### Post by arrrghhh on 2010-07-23
Strange... I hate to say it, but there's gotta be something with that mobo that Ubuntu does not like.

I installed Ubuntu Server edition 10.04 from a USB flash drive just about a month ago on my box, no problems whatsoever.

---

### Post by rexless on 2010-07-23
I used unetbootin which had an option for the server edition.
I think I'll try the dd option just-in-case.
I had this same problem when I was trying to install Ubuntu Cloud on a different machine some time ago and gave up.

---

### Post by rexless on 2010-07-23
I just tried the same on a completely different system with identical results.  Perhaps Ubuntu doesn't like any motherboards?

---

### Post by rexless on 2010-07-23
On the second system if I connect the IDE CDROM drive the installer works.  If I use Oracle Enterprise Linux install CD or the Xen 5.5 install CD over USB it works fine.  

It's definitely Ubuntu that's screwing things up.

Unfortunately in order for this to be acceptable I MUST be able to install from a USB source.  Once the machine is in the data center, there's no option to rip it open and dangle an IDE drive from it should there be a need to reinstall or recover/repair the OS.

There must be some workaround for this.  Clearly the system can boot from the devices...

---

### Post by sylvester_0 on 2010-07-23
Are you saying that the machine is already in the data center and it needs to be re-installed? Or are you worried about not being able to "recover" the OS through USB reinstallation? If it's the latter, I think that should be the last of your concerns as long as you've properly set up your server (RAID etc.)

Sorry that I can't really provide more help. Unetbootin usually works fine for me. Have you considered using Debian instead? I switched most of my servers to Debian about a year ago. The installation options (USB/network/miniCD) seem to be more diverse...

---

### Post by Uniqueone on 2010-07-27
Hi Rexless

i just posted a solution for someone else on what sounds to be a similar problem ( perhaps the exact same problem )

[http://ubuntuforums.org/showthread.php?t=1538056&highlight=usb+install](http://ubuntuforums.org/showthread.php?t=1538056&highlight=usb+install)

This is a problem with the distribution hopefully the Dev's take notice

good luck.

---

### Post by rexless on 2010-08-11
[SIZE="6"][B]THANK YOU

UBUNTU DEV -- Please fix this![/B][/SIZE]

---

### Post by cdenley on 2010-08-11
If you want a dev to see your request, you're probably better off filing a bug report, if there isn't one already. I doubt a dev would see your post here, even if you use a really big, annoying font.

---

### Post by dtfinch on 2010-08-24
I'm getting this too on Ubuntu Server 10.04.1. 

But it looks like it is a file extension issue as suggested in the linked post, though I haven't retested yet. I have 4 truncated filenames in I:\pool\main\l\linux , though I don't know why this never happened before. I've been using unetbootin for years now to copy the iso to usb and never had this problem prior to 10.04.1.

Edit: Correcting the filenames wasn't enough to solve the problem, and I've found no others that were truncated. Same error occurs.

Edit 2: Looking at [https://bugs.launchpad.net/unetbootin/+bug/373089](https://bugs.launchpad.net/unetbootin/+bug/373089) , my next step is to copy \dists\lucid to \dists\stable and \dists\unstable to work around the broken symlinks issue.

Edit 3: After fixing that, it still gives the same error. Console output suggests that it's trying to mount the physical cd-rom drive device rather than the device associated with the usb drive. If I mount the drive to /cdrom/ manually, it proceeds until it gets to "installing base system" and fails with "Debootstrap Error - Failed to determine the codename for the release." The console output gives no clues.

I've spent too many hours on what used to be a time saver. Burning a CD now.

Edit 4: Though I don't have time to risk on another USB attempt, there's mention of a new "cdrom-detect/try-usb=true" boot option that defaults to false, which would explain why it tried only to mount the physical cd-rom and ignored the usb drive. [https://bugs.launchpad.net/unetbootin/+bug/297409](https://bugs.launchpad.net/unetbootin/+bug/297409)

---

### Post by sh1ny on 2010-08-25
I just used an usb to install 10.04.1 2 days ago. Looking at this post i decided to open it and check - i have no such truncated filenames. I used the startup disk creator that comes with ubuntu ( System -> Administration -> Startup Disk Creator ). So i highly doubt this is a flaw in the cd image or the Startup Disk Creator.

---

### Post by rmh80 on 2010-09-09
Installing from server 10.04 ISO with USB will work.
I have done it with 10.04 server from USB to headless machine wihtout network connections.

But when i tried install 10.04.1 server to that machine it failes to that CD-ROM detection.
Seems "cdrom-detect/try-usb=true" wont do anything in 10.04.1 server.

So i have to install 10.04 and then update it manually with keryx to 10.04.1.

Have you tried 10.04 or 10.04.1 ISO ?

---

### Post by feonix83 on 2012-03-26
There is an open bug, from about a few months before it was recommend to open one, I believe:

[https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/574468](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/574468)

---

