---
title: "I want to hexa-boot all unique/original distros"
date: 2010-11-14
forum: The Cafe
---

### Post by user1397 on 2010-11-14
Ive been thinking about hexa-booting, yes you heard that right, hexa-booting linux distros.

I want to make each partition as unique as possible, and preferably want the original base distro, not something based on another distro.

So I'm thinking Debian, CentOS (as close as you can get to RedHat right?), Slackware, Gentoo, Arch, and yes...LFS

Do you think this should be fun, or a total nightmare?! :)

Also suggestions/advice/general info about installing these is welcome.

As for why I am doing this, I want to know what it is like to install distros with certain definite differences in their structure, even though i know that the end result will always be about the same (a gnome desktop, etc)

EDIT: what do you think about one of the BSDs...which one should I try, FreeBSD?

---

### Post by 3Miro on 2010-11-14
I have done something similar with 5 distros. I always have a different combinations of Ubuntu, Gentoo, Arch, Fedora, Slackware and Lunar. On the surface you do get Gnome, KDE, XFCE or LXDE, but there are major underlying differences in how some of them work. The biggest difference is in philosophy and it does make a difference. Ubuntu wants to do everything for you. In Arch and Gentoo you have to set things up yourself, with Arch being considerably easier and simpler. Fedora is paranoid about security. Slackware is very conservative about what you get to install, but also very stable. Lunar is more for servers and due to its small community you sometimes have to fix on the lowest level yourself.

All of those have pluses and minuses, try as many distros as you can and see what you like. For right now I will stick with XFCE Gentoo (unless I decide to give Lunar another chance).

---

### Post by koenn on 2010-11-14
you missed Suse.

---

### Post by user1397 on 2010-11-14
> **koenn said:**
> you missed Suse.

well suse is originally based on slackware, plus I would install opensuse and that is basically as easy to install as ubuntu right?

---

### Post by koenn on 2010-11-14
well, S.u.S.E., the company, started out as a distributor of Slackware, but today Suse is pretty much its own distro. 
And, apart from LFS (and maybe Arch, I don't know), all distro's come with Next-Next-Finish installers

---

### Post by Spice Weasel on 2010-11-14
Those are NOT unique or original.

THIS is unique and original:

[http://en.wikipedia.org/wiki/GoboLinux](http://en.wikipedia.org/wiki/GoboLinux)

---

### Post by user1397 on 2010-11-14
> **koenn said:**
> well, S.u.S.E., the company, started out as a distributor of Slackware, but today Suse is pretty much its own distro. 
And, apart from LFS (and maybe Arch, I don't know), all distro's come with Next-Next-Finish installers
I'm pretty sure slackware, arch, gentoo, LFS, and most of the BSDs dont have next-next-finish installers, correct me if i'm wrong anyone.

---

### Post by 3Miro on 2010-11-14
Arch comes with Next -> Next -> Finish installer, but it only gives you a bare CLI system. Gentoo on the other hand doesn't (I think they have something form 2008, but the current one you have to do it yourself almost from scratch)

[http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml)

LFS is way too much hassle for one person. Once you install it,  you also have to maintain it, so it is a non-stop work. Of course, if you have the time, you should go for it.

I did try Susa once before, when my NVIDIA card died and I had to use an ATI for some time. Susa installed, but once I tried to get the proprietary ATI driver, it messed up the xorg settings and I gave up on it.

---

### Post by 3Miro on 2010-11-14
> **ubuntuman001 said:**
> I'm pretty sure slackware, arch, gentoo, LFS, and most of the BSDs dont have next-next-finish installers, correct me if i'm wrong anyone.

Slackware comes with Next -> Next installer and it gets you all the way to KDE or XFCE. See my previous post for Arch and Gentoo. LFS is not a distribution, it is a book on how to make your own distribution, so it doesn't have a NNF installer. I don't know about BSD.

---

### Post by user1397 on 2010-11-14
> **3Miro said:**
> Slackware comes with Next -> Next installer and it gets you all the way to KDE or XFCE. See my previous post for Arch and Gentoo. LFS is not a distribution, it is a book on how to make your own distribution, so it doesn't have a NNF installer. I don't know about BSD.
yea i know LFS is just a book.  but yea maybe i could leave LFS as a side project for the future.

GoboLinux as mentioned above does look unique.  

So i think i might try:
centOS
debian
slackware
gentoo
arch
freeBSD
goboLinux

and i think that'll be enough for now.

---

### Post by juancarlospaco on 2010-11-14
**Debian kFreeBSD**

---

### Post by oldfred on 2010-11-14
Since i am currently only Ubuntu (and XP), I do not know details.

But you do have to know what boot loader each system uses and which one will be in charge of the MBR. Most distributions let you choose whether or where to install the boot loader. Grub2 is very good at finding other distributions and setting up boot. Grub legacy just about required you to manually add your boot stanza.

You should also create a /data partition for any data that you may want to mount in each distribution.

Do any distributions require primary partitions, LVM or other drive configurations? Or do they all work from logical partitions. Are you installing all on one drive, that may change what goes where.

---

### Post by user1397 on 2010-11-14
hmm I also have to figure out if I can install all of those distros from usb drive, since i'm probably doing this on my netbook

---

### Post by gmargo on 2010-11-14
I'm all for playing around with different installations, but why do you want to do physical hard disk installs?  This is exactly what virtual machines are good for.  (I have roughly 35 different virtual machines for various versions of Ubuntu and other distros.)

---

### Post by oldfred on 2010-11-14
I like grub2 so well I use it to boot all my ISO for install or repairs.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by 3Miro on 2010-11-14
No Linux distribution requires a primary partition to install. All Linux uses the Linux kernel, which doesn't care (under Gentoo you will have to make sure to compile the proper driver into the kernel and for some other distros you will have to be careful about initrd). I have all of my distributions tested on Logical partitions. I wouldn't think BSD would require a primary partition either, but then I have never used BSD. AFIK only windows requires a primary partition to boot.

When I first started playing around, I thought that Grub 2 would be great for managing many Linux installs, however, I was wrong. From within Ubuntu 10.04, Grub will not recognize a Gentoo install and you will have to manually add it (which is somewhat more complicated than editing menu.lst in Grub 1). Then when I had two separate kernels in Arch, Grub will list the entries as Arch and Arch, so I couldn't distinguish between them at boot time. In Grub 1, it is very easy to edit your own entries with things like the specific name of the build with boot options and all. Maybe I just didn't take the time to learn Grub 2, but it looked way more rigid. At any rate, I recommend using Grub 1. 

Distros using Grub 2 or Lilo can still boot, I just lost the boot splash screen on Ubuntu and has some issues with initrd on Slack and PCLOS. All of those are easily resolved so long as you care to take the time.

Also, VirtualBox is good to try things first, however, it is not so good if you want to see a distro at its full potential. There are issues with visual effects, sluggish DE, xorg drivers for different versions of xorg and overall somewhat slow performance.

---

### Post by hhh on 2010-11-14
> **koenn said:**
> And, apart from LFS (and maybe Arch, I don't know), all distro's come with Next-Next-Finish installers

aptosid has a tabbed installer that lets you jump to any section of the setup options (partitioning, name & passwords, timezone, etc...) before installing.

---

