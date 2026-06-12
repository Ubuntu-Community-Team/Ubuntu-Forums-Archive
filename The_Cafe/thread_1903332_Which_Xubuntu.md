---
title: "Which Xubuntu?"
date: 2012-01-02
forum: The Cafe
---

### Post by rmcellig on 2012-01-02
I am looking for a distro that will match up well with my old Dell 3000 computer. I am thinking of trying Xubuntu but am not sure whether to go with 11.10 or the LTS release 10.04.

Are there any other easy to use resource friendly distros that I might consider for my old Dell 3000?

---

### Post by Elfy on 2012-01-02
I installed 11.10 the other day on an old easynote I acquired for free - it all worked fine - though it did have 1Gb RAM in it.

Depends what hardware it's got I guess.

---

### Post by Lars Noodén on 2012-01-02
There is also [Lubuntu](http://lubuntu.net/) which is even lighter weight.  Or you can skip having a desktop environment completely and install just a window manager like Openbox, FVWM-crystal, or Fluxbox.

Regardless of which one, go with 11.10 with a mind to migrate to 12.04.  Or you can go straight to 12.04 right now, is just that it'll need updating constantly and making small changes until it is officially released in April.

If you can, add a little extra RAM to bring it up to 1GB or 2GB at least.

---

### Post by snowpine on 2012-01-02
1. What are your hardware specs? (very important information)

2. Do you prefer older, well-tested, stable software (10.04) or the latest and greatest (11.10 or maybe even 12.04 pre-release)?

---

### Post by rmcellig on 2012-01-02
What can I use aside from Sysinfo to obtain my Hardware specs?

I am basically using the Dell to record audio and watch/edit some videos, skype, pidgin as well.

I am installing Lubuntu at the moment to see how I like it.

---

### Post by Lars Noodén on 2012-01-02
You can use [lshw](http://manpages.ubuntu.com/manpages/oneiric/en/man1/lshw.1.html).  It can create output in HTML for easier viewing.

```

sudo lshw -html > /tmp/x.html && firefox /tmp/x.html

```

---

### Post by rmcellig on 2012-01-02
Here you go:

```

id:	
randy-dimension-3000
description: 	Mini Tower Computer
width: 	32 bits
capabilities: 	smbios-2.3 dmi-2.3 smp-1.4 smp
configuration:	
administrator_password	=	enabled
boot	=	normal
chassis	=	mini-tower
cpus	=	1
power-on_password	=	enabled
uuid	=	44454C4C-5300-1039-8034-C2C04F473831
id:	
core
description: 	Motherboard
product: 	0TC667
vendor: 	Winbond Electronics
physical id: 	
0
serial: 	..CN4811157800X9.
id:	
firmware
description: 	BIOS
vendor: 	Winbond Electronics
physical id: 	
0
version: 	A02
date: 	11/08/2004
size: 	64KiB
capacity: 	448KiB
capabilities: 	pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
id:	
cpu
description: 	CPU
product: 	Intel(R) Celeron(R) CPU 2.66GHz
vendor: 	Intel Corp.
physical id: 	
400
bus info: 	
cpu@0
version: 	15.4.1
serial: 	0000-0F41-0000-0000-0000-0000
slot: 	Microprocessor
size: 	2666MHz
capacity: 	3600MHz
width: 	32 bits
clock: 	533MHz
capabilities: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
configuration:	
id	=	0
id:	
cache:0
description: 	L1 cache
physical id: 	
700
size: 	8KiB
capacity: 	16KiB
capabilities: 	internal write-back data
id:	
cache:1
description: 	L2 cache
physical id: 	
701
size: 	256KiB
capacity: 	256KiB
capabilities: 	internal varies unified
id:	
memory
description: 	System Memory
physical id: 	
1000
slot: 	System board or motherboard
size: 	2GiB
id:	
bank:0
description: 	DIMM SDRAM Synchronous 333 MHz (3.0 ns)
physical id: 	
0
slot: 	DIMM_1
size: 	1GiB
width: 	64 bits
clock: 	333MHz (3.0ns)
id:	
bank:1
description: 	DIMM SDRAM Synchronous 333 MHz (3.0 ns)
physical id: 	
1
slot: 	DIMM_2
size: 	1GiB
width: 	64 bits
clock: 	333MHz (3.0ns)
id:	
pci
description: 	Host bridge
product: 	82865G/PE/P DRAM Controller/Host-Hub Interface
vendor: 	Intel Corporation
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	02
width: 	32 bits
clock: 	33MHz
configuration:	
driver	=	agpgart-intel
resources:	
irq	:	0
memory	:	f0000000-f7ffffff
id:	
display
description: 	VGA compatible controller
product: 	82865G Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm vga_controller bus_master cap_list rom
configuration:	
driver	=	i915
latency	=	0
resources:	
irq	:	16
memory	:	e8000000-efffffff
memory	:	feb80000-febfffff
ioport	:	ed98(size=8)
id:	
generic
description: 	System peripheral
product: 	82865G/PE/P Processor to I/O Memory Interface
vendor: 	Intel Corporation
physical id: 	
6
bus info: 	
pci@0000:00:06.0
version: 	02
width: 	32 bits
clock: 	33MHz
configuration:	
latency	=	0
resources:	
memory	:	fecf0000-fecf0fff
id:	
usb:0
description: 	USB Controller
product: 	82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
vendor: 	Intel Corporation
physical id: 	
1d
bus info: 	
pci@0000:00:1d.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	16
ioport	:	ff80(size=32)
id:	
usb:1
description: 	USB Controller
product: 	82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
vendor: 	Intel Corporation
physical id: 	
1d.1
bus info: 	
pci@0000:00:1d.1
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	19
ioport	:	ff60(size=32)
id:	
usb:2
description: 	USB Controller
product: 	82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
vendor: 	Intel Corporation
physical id: 	
1d.3
bus info: 	
pci@0000:00:1d.3
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	16
ioport	:	ff20(size=32)
id:	
usb:3
description: 	USB Controller
product: 	82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
vendor: 	Intel Corporation
physical id: 	
1d.7
bus info: 	
pci@0000:00:1d.7
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	23
memory	:	ffa80800-ffa80bff
id:	
pci
description: 	PCI bridge
product: 	82801 PCI Bridge
vendor: 	Intel Corporation
physical id: 	
1e
bus info: 	
pci@0000:00:1e.0
version: 	c2
width: 	32 bits
clock: 	33MHz
capabilities: 	pci normal_decode bus_master
resources:	
ioport	:	d000(size=4096)
memory	:	fea00000-feafffff
id:	
network:0
description: 	Wireless interface
product: 	AR2413 802.11bg NIC
vendor: 	Atheros Communications Inc.
physical id: 	
0
bus info: 	
pci@0000:01:00.0
logical name: 	
wlan0
version: 	01
serial: 	00:15:e9:42:8a:ba
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	ath5k
driverversion	=	3.0.0-14-generic
firmware	=	N/A
latency	=	168
link	=	no
maxlatency	=	28
mingnt	=	10
multicast	=	yes
wireless	=	IEEE 802.11bg
resources:	
irq	:	21
memory	:	feaf0000-feafffff
id:	
network:1
description: 	Ethernet interface
product: 	82562EZ 10/100 Ethernet Controller
vendor: 	Intel Corporation
physical id: 	
8
bus info: 	
pci@0000:01:08.0
logical name: 	
eth0
version: 	02
serial: 	00:13:20:70:e4:01
size: 	100Mbit/s
capacity: 	100Mbit/s
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	e100
driverversion	=	3.5.24-k2-NAPI
duplex	=	full
firmware	=	N/A
ip	=	192.168.2.11
latency	=	64
link	=	yes
maxlatency	=	56
mingnt	=	8
multicast	=	yes
port	=	MII
speed	=	100Mbit/s
resources:	
irq	:	20
memory	:	feaef000-feaeffff
ioport	:	df40(size=64)
id:	
isa
description: 	ISA bridge
product: 	82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
vendor: 	Intel Corporation
physical id: 	
1f
bus info: 	
pci@0000:00:1f.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master
configuration:	
latency	=	0
id:	
ide
description: 	IDE interface
product: 	82801EB/ER (ICH5/ICH5R) IDE Controller
vendor: 	Intel Corporation
physical id: 	
1f.1
bus info: 	
pci@0000:00:1f.1
logical name: 	
scsi0
logical name: 	
scsi1
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	ide bus_master emulated
configuration:	
driver	=	ata_piix
latency	=	0
resources:	
irq	:	18
ioport	:	1f0(size=8)
ioport	:	3f6
ioport	:	170(size=8)
ioport	:	376
ioport	:	ffa0(size=16)
memory	:	feb7fc00-feb7ffff
id:	
disk
description: 	ATA Disk
product: 	Maxtor 6L200R0
vendor: 	Maxtor
physical id: 	
0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	BAJ4
serial: 	L50K5T9G
size: 	189GiB (203GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	000530d2
id:	
volume:0
description: 	EXT4 volume
vendor: 	Linux
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
version: 	1.0
serial: 	ebbb8955-a757-416e-b356-e87a1b5f4e36
size: 	91GiB
capacity: 	91GiB
capabilities: 	primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration:	
created	=	2011-12-15 10:00:44
filesystem	=	ext4
label	=	Ultimate Editio
lastmountpoint	=	/mnt/migrationassistant
modified	=	2012-01-02 09:14:19
mounted	=	2012-01-02 09:14:18
state	=	clean
id:	
volume:1
description: 	Linux swap volume
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
version: 	1
serial: 	d6d25dea-12ec-4a2b-a546-edf173f463ea
size: 	8000MiB
capacity: 	8000MiB
capabilities: 	primary nofs swap initialized
configuration:	
filesystem	=	swap
pagesize	=	4096
id:	
volume:2
description: 	EXT4 volume
vendor: 	Linux
physical id: 	
3
bus info: 	
scsi@0:0.0.0,3
logical name: 	
/dev/sda3
logical name: 	
/
version: 	1.0
serial: 	9da378cf-951b-4dad-bcb2-7440b663843f
size: 	90GiB
capacity: 	90GiB
capabilities: 	primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration:	
created	=	2012-01-02 09:10:46
filesystem	=	ext4
lastmountpoint	=	/
modified	=	2012-01-02 09:29:30
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered
mounted	=	2012-01-02 09:45:35
state	=	mounted
id:	
cdrom
description: 	DVD writer
product: 	DVD-RW DVR-110D
vendor: 	PIONEER
physical id: 	
1
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	1.39
capabilities: 	removable audio cd-r cd-rw dvd dvd-r
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
serial
description: 	SMBus
product: 	82801EB/ER (ICH5/ICH5R) SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	02
width: 	32 bits
clock: 	33MHz
configuration:	
latency	=	0
resources:	
ioport	:	eda0(size=32)
id:	
multimedia
description: 	Multimedia audio controller
product: 	82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
vendor: 	Intel Corporation
physical id: 	
1f.5
bus info: 	
pci@0000:00:1f.5
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	Intel ICH
latency	=	0
resources:	
irq	:	17
ioport	:	ee00(size=256)
ioport	:	edc0(size=64)
memory	:	feb7fa00-feb7fbff
memory	:	feb7f900-feb7f9ff
```

---

### Post by Morbius1 on 2012-01-02
I have a test box:

Dell Dimension XPS T600
600MHz Pentium III
512 MB Memory

It has Xubuntu 11.10 on it and it does run. Not the fastest thing in my inventory mind you but it does run. Coincidentally it dual boots with an older version of Lubuntu and although Lubuntu does run faster it's not by a level of magnitude faster.

Compared to what you have I don't think my system is still considered a PC.

---

### Post by BrokenKingpin on 2012-01-02
I have Xubuntu 11.10 running on all my machines, and it is very good. I tried Lubuntu and it was okay, but found Xubuntu more user friendly and easier to configure. Xubuntu is not as light as Xubuntu, but close enough where I didn't notice  much of a difference even on my slow netbook.

---

### Post by keithpeter on 2012-01-02
> **Morbius1 said:**
> Compared to what you have I don't think my system is still considered a PC.

:twisted:

2Gb of RAM and a Celeron D, I'd have thought that  Morbius1's box ought to be able to run just about any Ubuntu version?

---

### Post by Lucradia on 2012-01-02
There's also this pre-compiled thread of things to try with Debian (Also works with ubuntu too, just different package names.)

[http://forums.debian.net/viewtopic.php?f=20&t=50703](http://forums.debian.net/viewtopic.php?f=20&t=50703)

The mini.iso for ubuntu can be found here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Make sure to actually read the list of packages. You may not want to use flash. There's no GUI login, which may deter you from trying this.

Sadly,
```
case $? in
   1)
      echo "Exit";;
   2)
      openbox --exit;;
   3)
      sudo shutdown -r now;;
   4)
      sudo shutdown -h now;;
esac
```

Won't work anymore. (First one won't do anything; second one will restart openbox even though it's supposed to logout; third and fourth won't do anything, even though it's supposed to auto-open a terminal to allow you to confirm the sudo.)

---

### Post by GraeW on 2012-01-03
I've been an off and on user of XFCE for many years, and agree with comments above that it is very user friendly and easy to configure. It might not be the absolute lightest on resources, but it is no hog like KDE or Gnome.
 
Lately I've been going back and looking at some of the older/dead/dying window manager/environments, and am playing around with WindowMaker. it may not have all the whiz-bang-tweeting-bells-and-whistles but it looks different and is pretty easy to configure (although not quite as point-and-click as newer environments). I found WM and Afterstep are available through Synaptic, along with e17 and a few of the more window-esque managers (most all of which are dead or at least fairly stagnate).
 
I came to linux over a decade ago because I didn't like the constant problems and desktop limitations from windows and couldn't afford an apple. Linux gives the customization I miss from windows 3.1 (before the OS and the desktop became one and the same). I may not have the time or knowledge to do the bigger tweaks for things like conky or others, but I at least know the option is there for me (unlike windows).

---

### Post by wolfen69 on 2012-01-03
> **Lars Noodén said:**
> There is also [Lubuntu](http://lubuntu.net/) which is even lighter weight.

+1 for lubuntu. It will be even faster than xubuntu.

---

### Post by t0p on 2012-01-03
I also like Lubuntu for specs-impaired machinery.  I've got an EeePC 701, which I've beefed up with 2GB of RAM, but there isn't really much I can think of to really help the Celeron M chip (other than replace it, lol).  Vanilla Ubuntu makes it crawl, and Xubuntu isn't much better, but Lubuntu runs pretty nicely (for an ancient, out-moded netbook).

My desktop box  (Pentium 4, 1.7 GHz, 1 GB RAM), runs vanilla Ubuntu passably, but when upgrade time comes round (the next LTS) I may go for a change.  Maybe Xubuntu.

---

### Post by mips on 2012-01-04
Crunchbang XFCE (based on Debian 6) I find much lighter & faster than Xubuntu.

---

### Post by Stafke on 2012-01-04
Just keep in mind that corenominal (crunchbang's developer) is giving up on xfce and focusing on openbox all along.

He does some great work and if you're willing to spend some time configuring your menu, openbox is VERY light to go. Yet it has some rough edges. I had crunchbang (openbox) for a couple of months and I really liked the concept. However, I recently moved back to xubuntu because I prefer to have a desktop that works out of the box after install. (I may go back in the future though, I happen to be a bit of a distro hopper with my netbook).
With xfce I can tweak the settings when I have the time to do so, but in the meantime have a decent working system. In openbox, you'd better not wait too long with configuring everything or you might give up as you do not find your way around in openbox.
I'm not a programmer, but found out how to configure openbox quite easily in crunchbang, so if you want a snappy system and have some time to configure, don't let that scare you. Btw, the crunchbang forum members are very friendly.

I've also heard that ubuntu minimal + xfce is snappier than xubuntu, although I don't know whether this is still true.

---

### Post by Lucradia on 2012-01-04
> **Stafke said:**
> Just keep in mind that corenominal (crunchbang's developer) is giving up on xfce and focusing on openbox all along.

Not too many programs that crunch actually needs to have are coded to not use a DE. If they are, they're usually still rather buggy, unless ayttm finally is less crashy and more stable with MSN. (Pidgin requires GNOME-Config (For Proxy), and ayttm doesn't.)

---

### Post by mips on 2012-01-04
> **Stafke said:**
> 
With xfce I can tweak the settings when I have the time to do so, but in the meantime have a decent working system. In openbox, you'd better not wait too long with configuring everything or you might give up as you do not find your way around in openbox.
I'm not a programmer, but found out how to configure openbox quite easily in crunchbang, so if you want a snappy system and have some time to configure, don't let that scare you. Btw, the crunchbang forum members are very friendly.


Weird thing is once you have setup Openbox to your liking you stop fiddling with it. XFCE is the same for me, once setup you leave it be. I run Arch+Openbox on my laptop and Ubuntu core + XFCE on my desktop. Once they are setup I don't fiddle any more. If I think about it I actually don't see why I need XFCE as I can do everything it does with Openbox. I'll be setting up Openbox on my desktop soon I reckon.

---

### Post by BrokenKingpin on 2012-01-04
> **mips said:**
> If I think about it I actually don't see why I need XFCE as I can do everything it does with Openbox. I'll be setting up Openbox on my desktop soon I reckon.
I find both Xfce and Openbox fairly usable once I get them setup, I just find that Xfce is far easier to get setup to my liking. Xfce has a lot more options for configuring through the GUI. Also things like the Xfce power manager and other utilies just make the setup process super easy as it is all installed by default with Xfce. The Xfce panel is really nice as well.

The other major advantage I see to Xfce is that it's window manager (Xfwm) has a built in compositor, which works very well.

---

### Post by Artemis3 on 2012-01-04
Well obviously openbox alone takes much less memory, but i think for usability adding LXDE is worth (ie. Lubuntu).

That said Xubuntu is the closest you can get to a gnome2 (classic desktop) experience, without the sluggishness and bugs.

It would be good to use 11.10 and then upgrade to 12.04 LTS and remain there, 10.04 LTS is valid (you can upgrade directly to 12.04 LTS later).

I would use Xubuntu 11.10 then stay with 12.04 in that machine, it has plenty of memory; but Lubuntu is also valid. I don't think customizing beyond these is worth it, but you can do it if you have lots of spare time or wish to learn more.

---

### Post by Stafke on 2012-01-05
> **mips said:**
> Weird thing is once you have setup Openbox to your liking you stop fiddling with it. XFCE is the same for me, once setup you leave it be. 

Probably it has something to do with the fact that my netbook is some sort of spare toy to explore some distros etc. As such it is sometimes rather timeconsuming to set up a new openbox config when I feel like trying a new distro.

If it would be my main desktop, it would be otherwise probably.

Another thing with crunchbang: I completely understand the decision to move from buntu-base to debian-base for crunchbang. Yet, the friendly forums on crunchbang have a rather limited population (unlike buntu's) while the debian forums require much more knowledge about your system (which I don't have, I use linux but have fairly limited computer knowledge). Therefore, for me personally, buntu seems a nicer base.
Finally, although the dark look of crunchbang looks very slick in the beginning, it's quite tiring for my eyes after a while (of course you can change that, I know, but it's one of the visual things that makes crunchbang different than others)

Are there any guides to get buntu+openbox?

---

### Post by Lars Noodén on 2012-01-05
> **Stafke said:**
> Are there any guides to get buntu+openbox?

You can get it by installing the package "[openbox](apt://openbox)"  Otherwise [Openbox](http://openbox.org/) is the same on any system.

---

### Post by mips on 2012-01-05
> **Stafke said:**
> 
Are there any guides to get buntu+openbox?

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

First find a guide on how to do a minimal install of ubuntu.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

.

---

### Post by Stafke on 2012-01-05
Thanks mips.

I will stop hijacking this thread now.

---

### Post by Lucradia on 2012-01-05
> **Stafke said:**
> Thanks mips.

I will stop hijacking this thread now.

And this too: [http://ubuntuforums.org/showpost.php?p=11581819&postcount=11](http://ubuntuforums.org/showpost.php?p=11581819&postcount=11)

---

