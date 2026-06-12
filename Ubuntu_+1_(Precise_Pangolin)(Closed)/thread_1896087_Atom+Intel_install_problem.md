---
title: "Atom+Intel install problem"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2011-12-16
Has anyone got Precise 32bit working on a system with an Atom N270 + Intel 945 chipset? I tried the daily live iso last week, and I got a kernel panic, before the desktop even loaded. Today I can install Precise, but I get a kernel panics within a couple of minutes of starting up.

---

### Post by mdurham on 2011-12-16
cariboo907, I have three of the same type of system as you and they all do the same as you describe. If you can use the 3.1.0-x kernel I think you will find it will work, at least it does for me.
Cheers, Mike

> mike$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Ralink corp. RT2860
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


---

### Post by jerrylamos on 2011-12-16
Not quite the same.  This is Acer Aspire 1 D255E:

Intel® Atom™ CPU N455 @ 1.66GHz × 2 

lspci says: Intel Corporation N10 Family Integrated Graphics ControllerIntel Corporation N10 Family Integrated Graphics Controller

Currently running 3.2.0-4-generic

with update to 3.2.-5-generic in process.

It's been running precise pangolin all along.  Boring.  I don't think I can hardly tell the difference vs. oneiric ocelot in another partition, except oneiric had lots of breakage in development.

Jerry

---

### Post by lucazade on 2011-12-16
try to find out which kernel module is problematic by unloading it at boot time.
probably is the intel kernel module for the gfx-card.. if i'm not wrong you must employ i915 module.
try to pass this fake kernel param to avoid module from starting up:
i915.dummy=1
or
nomodeset
(the last one kills Kms needed by video drivers to work.. so i915 will be not loaded).

---

### Post by mdurham on 2011-12-16
> **lucazade said:**
> try to find out which kernel module is problematic by unloading it at boot time.
probably is the intel kernel module for the gfx-card.. if i'm not wrong you must employ i915 module.
try to pass this fake kernel param to avoid module from starting up:
i915.dummy=1
or
nomodeset
(the last one kills Kms needed by video drivers to work.. so i915 will be not loaded).

Thanks for the advice lucazade but it didn't help, it still crashes in the same way.

The computer is an Asus eee B202 (so called nettop).
In fact we have 4 of these B202's. I have PP installed on one and can't get past kernel 3.1. The Live alpha will not boot on 3 of them but strangely will boot on one of them.I've found a difference between the bootable and non-bootable boxes. I don't know if this is relevant or not.

Bootable has Ethernet controller:
JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 11)

Un-bootable:
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by lucazade on 2011-12-17
> **mdurham said:**
> Thanks for the advice lucazade but it didn't help, it still crashes in the same way.

The computer is an Asus eee B202 (so called nettop).
In fact we have 4 of these B202's. I have PP installed on one and can't get past kernel 3.1. The Live alpha will not boot on 3 of them but strangely will boot on one of them.I've found a difference between the bootable and non-bootable boxes. I don't know if this is relevant or not.

Bootable has Ethernet controller:
JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 11)

Un-bootable:
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

then find out which kernel module for the realtek is in use in the unbootable machine:
```
lspci -k
```

and unload that module at boot

---

### Post by jerrylamos on 2011-12-17
This is a different atom & intel graphics controller which does work, see as follows:

> jerry@USBHD40:~$ lspci -k
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
	Subsystem: Acer Incorporated [ALI] Device 0349
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Acer Incorporated [ALI] Device 0349
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Acer Incorporated [ALI] Device 0349

Any differences to the ones that don't work?

Currently using linux-image 3.2.0-5.11

Jerry

---

### Post by cariboo on 2011-12-17
I've created a bug report, using apport-cli, as the system crashes when running the desktop. bug #[lpbug]905606[/lpbug]

---

### Post by mdurham on 2011-12-17
> **cariboo907 said:**
> I've created a bug report, using apport-cli, as the system crashes when running the desktop. bug #[lpbug]905606[/lpbug]

Well done, I've subscribed.

---

### Post by cariboo on 2012-01-22
I've been whining and complaining about this problem for the last month, last night I saw a post on the forum where the poster stated his system wouldn't boot with an SD card inserted. I'm embarrassed to say that I never even though about removing the SD card. Last night I did, and the system booted the way it is supposed to, and didn't go into a kernel panic. I'm currently running kernel 3.3-rc1, and everything works the way it should, suspend even works when I close the lid.

So now the question is, has anyone had their system kernel panic with an SD/USB drive connected during boot. I have Lubuntu 11:10 installed on the SD card, and it runs the way it should, and I also have a partition with Xubuntu on it, and it runs the way it should. It seems it's just Unity 3D that has the problem, I haven't tried 2D yet or gnome classic, but will try them later today.

---

### Post by Double.J on 2012-01-22
Hi there cariboo, Mine's a 2008 NC10 N270 GMA945 2GB RAM.

I restarted with an SD card to test - no problems here. I only jumped in on Precise a week ago and haven't been met with any kernel panics yet - I quite often have a USB stick in when booting as all my cloud stuff is backed up on there.

In terms of GUI, it's running the defaults, plus gnome shell, lubuntu, xubuntu, KDE and Openbox.

I've gone a bit mad in CCSM trying to see what the netbook would take and no problems yet.. except the usual result of trying to move the launcher ;) but all the usual effects are working for me.

htop says 530MB @ 2xchrome, 1x thunderbird, GIMP, 2xterminal, Xchat on unity 3D

I've also tried both my wireless cards (artheros and broadcom) and they don't cause any troubles. Sorry!

---

### Post by Hylas de Niall on 2012-01-22
Hi,
I've just tried booting the alpha 1 (from usb stick), hitting shift on boot and choosing 'nomodeset' in the f6 options.

the boot failed :( although i wasn't really very surprised, as i'd read this thread before attempting it).

*Without* 'nomodeset' i had correct graphic res boot, but kernel panic complete with flashing LED's!

Medion akoya mini e1210 (rebranded MSI wind u100)

Atom N270 + Intel 945 chipset

oh, and no SD in the slot either

Would i be better off booting from a DVD?

---

### Post by GeorgeVita on 2012-01-22
> **cariboo907 said:**
> ...So now the question is, has anyone had their system kernel panic with an SD/USB drive connected during boot. I have Lubuntu 11:10 installed on the SD card, and it runs the way it should, and I also have a partition with Xubuntu on it, and it runs the way it should. It seems it's just Unity 3D that has the problem, I haven't tried 2D yet or gnome classic, but will try them later today.

System: EeePC 1000h
1. Lubuntu 12.04 installed on HD (installation done from A1, fully updated till now)
2. Ubuntu 12.04 installed to SDHC (8GB) from LiveUSB (Live Daily .iso of 22-JAN)

Just checked, all boot fine, Lubuntu & LXDE from HD, Ubuntu and Ubuntu 2D from SDHC.

Notes: 
a. I used "Something else" for manual partitioning to do the installation
(because installer creates [an extra swap area]("https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507")) 
b. manual installer asks where to place boot manager, my decision was sdc (the SDHC card) and not sda (the HD)
c. grub boot from SDHC has all options including HD installation and their recovery modes

I wonder if we choose sda for the boot manager and boot without the SDHC card, will this cause a problem?

-------------
> **Hylas de Niall said:**
> ... the boot failed ... kernel panic complete with flashing LED's ...
Would i be better off booting from a DVD?

These problems are expected as this version (Ubuntu 12.04) is still on "Alpha". I faced the same problems from a daily live before some days (I don't remember if it was 16-Jan or 17-Jan).
Booting from any device (or directly from .iso) must be the same, assuming that there is no problem with the .iso (you must [check it with md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")).


G

---

### Post by Hylas de Niall on 2012-01-22
> **GeorgeVita said:**
> These problems are expected as this version (Ubuntu 12.04) is still on "Alpha". I faced the same problems from a daily live before some days (I don't remember if it was 16-Jan or 17-Jan).
Booting from any device (or directly from .iso) must be the same, assuming that there is no problem with the .iso (you must [check it with md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")).


G

Yep, i knew to expect issues with an alpha release, and have also tried a couple of the dailies previously with the same results (md5's all tallied).
I made my post more because i was using the same sort of setup as the OP, and was interested if there had been any progress with the issues i encountered since the dailies i'd tried.
:)

Ack! Well, the self same alpha booted fine (if incredibly slooooowly!) on my main desktop machine. I'm adding this from a live session of it. So i guess the iso is okay?
It's odd that it's clunky-er than a previous daily release from a week or so previous, but that's the nature of alphas i guess :)

---

### Post by kevpan815 on 2012-01-22
> **cariboo907 said:**
> Has anyone got Precise 32bit working on a system with an Atom N270 + Intel 945 chipset? I tried the daily live iso last week, and I got a kernel panic, before the desktop even loaded. Today I can install Precise, but I get a kernel panics within a couple of minutes of starting up.

Although my Atom Intel is a different CPU and Chipset, it won't run 32 Bit Ubuntu 12.04 LTS at all, but it will run 64 Bit Ubuntu just fine as long as I only use the Guest Account, otherwise if I use my Kevin John Panzke User Account, I get a Kernel Panic over and over again. I have already filed a Bug Report on my Kernel Panic Issue. So far the only Status Change in the Bug Report is New changed to Confirmed just to let you guys know.

---

### Post by cariboo on 2012-01-22
The one thing I found disappointing about my bug report, was that it was a bot posting the same thing every time a new kernel was released, it kept changing the bug to unconfirmed, and asking us to try the latest kernel version. Of course I tried the latest version and changed the bug to confirmed again. There wasn't any human interaction.

---

### Post by effenberg0x0 on 2012-01-22
> **cariboo907 said:**
> The one thing I found disappointing about my bug report, was that it was a bot posting the same thing every time a new kernel was released, it kept changing the bug to unconfirmed, and asking us to try the latest kernel version. Of course I tried the latest version and changed the bug to confirmed again. There wasn't any human interaction.

I've seen that many times. As far as I can understand the way the bug reporting system works, you gotta have it set to confirmed before a new kernel release. Otherwise it goes to unconfirmed. But, even if there's no absolute certainty of the bug existence, if you have enough people signing as "affected" by it, you can just change from unconfirmed to confirmed with the reason "it affects more users". But then you have to change the tags to something specific. There's a list of tags they use [here]("https://wiki.ubuntu.com/Bugs/Tags").

Regards,
Effenberg

---

### Post by mdurham on 2012-01-23
> **cariboo907 said:**
> The one thing I found disappointing about my bug report, was that it was a bot posting the same thing every time a new kernel was released, it kept changing the bug to unconfirmed, and asking us to try the latest kernel version. Of course I tried the latest version and changed the bug to confirmed again. There wasn't any human interaction.
It appears that nobody is interested in doing anything about this bug, it seems a pretty serious bug to me. 
cariboo907 I'd like to try kernel 3.3, how do you do it?
Thanks, Mike

---

### Post by cariboo on 2012-01-23
@mdurham, you can get 3.3-rc1 kernel and headers [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc1-precise/"). 

What I did is start one of the other distributions on my system, mounted / of my broken unity install on /mnt, in my case it was located on /dev/sda7, so I used the following command:

```
sudo mount /dev/sda7 /mnt
```

then I copied the header and kernel packages to a location in the directory tree on /mnt, in my case I used /opt, you have to copy the files as root, you can use whatever method you like best. I next chrooted /mnt. seeing as /dev/sda7 was already mounted on /mnt. I skipped that step, next I ran the following commands:

```
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
```

if you need internet access during these steps, copy /etc/resolv.conf to /mnt/etc/:

```
sudo cp /etc/resolv.conf /mnt/etc
```

then run the chroot command:

```
sudo chroot /mnt
```

Then cd to where you copied the packages and use dpkg -i to install the packages:

Start with the *all.deb package:

```
dpkg -i linux-headers-3.3.0-030300rc1_3.3.0-030300rc1.201201191835_all.deb
```

Next the i386 specific header package:

```
dpkg -i linux-headers-3.3.0-030300rc1-generic-pae_3.3.0-030300rc1.201201191835_i386.deb
```

And finally the kernel package:

```
dpkg -i linux-image-3.3.0-030300rc1-generic-pae_3.3.0-030300rc1.201201191835_i386.deb
```

Let us know how it goes.

---

### Post by mdurham on 2012-01-24
Thanks cariboo907 for those detailed instructions, they were much appreciated. Unfortunately kernel 3.3 produces the same result as all the 3.2's that is, it produces a panic after about 30 seconds after booting, so I'm still using 3.1. The odd thing is it panics on three of my four Asus B202's but not on the fourth. I guess I'm stuck with using 3.1
Thanks again for your help with installing the 3.3 kernel.
Mike

---

### Post by mdurham on 2012-02-02
We are not alone with this bug here are a couple of interesting discussion links.

[Bug 784404 – Kernel Panic after installing kernel-3.2.1-3.fc16.i686]("https://bugzilla.redhat.com/show_bug.cgi?id=784404")

[[SOLVED] Fedora16 kernel 3.2.1 panic on ATOM netbook - FedoraForum.org]("http://www.fedoraforum.org/forum/showthread.php?p=1549797")

---

### Post by kevpan815 on 2012-02-02
> **mdurham said:**
> We are not alone with this bug here are a couple of interesting discussion links.

[Bug 784404 – Kernel Panic after installing kernel-3.2.1-3.fc16.i686]("https://bugzilla.redhat.com/show_bug.cgi?id=784404")

[[SOLVED] Fedora16 kernel 3.2.1 panic on ATOM netbook - FedoraForum.org]("http://www.fedoraforum.org/forum/showthread.php?p=1549797")

I solved the problem on 64 Bit Ubuntu Alpha 2 + latest updates by installing Ubuntu Kernel 3.3.0 RC2 from the Ubuntu Kernel PPA Mainline Website. It's easy to install on Ubuntu since Everything there is in .DEB installer format!

---

### Post by Hylas de Niall on 2012-02-03
Still getting kernel panic on the Alpha 2...
===SNIPPED===

:confused:

....i just read caribou's post

---

### Post by xyzzyman on 2012-02-03
> **Hylas de Niall said:**
> Still getting kernel panic on the Alpha 2...
===SNIPPED===

:confused:

....i just read caribou's post

If you want a kernel with all the ubuntu goodness and the patch applied, you can get them from launchpad

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-13.22](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-13.22)

If not it should be available in the repo anywhere's from now until 24 hours from now.

---

### Post by keithpeter on 2012-02-03
Hello All

I'll be trying my Asus EeePC 1000 (N270 with 945 graphics) booting from a usb stick. This netbook has ssd storage (8Gb and 32Gb, one fast one slow) and I don't like reinstalling it a lot.

I had kernel panics on Onieric which may have been due to wifi power down. The little plastic spacer is still in the SD card slot :twisted:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/869502/comments/130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/869502/comments/130) 

(also 131 comment).

---

### Post by Hylas de Niall on 2012-02-27
Yes!

No kernel panics on today's daily build!
...and Unity is much faster and better behaved!

I'm very encouraged by this :)

Nice work folks!

:D

---

