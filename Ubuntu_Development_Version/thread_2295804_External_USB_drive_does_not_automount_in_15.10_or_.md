---
title: "External USB drive does not automount in 15.10 or 16.04 or 16.10"
date: 2015-09-21
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-09-21
I have a 1TB Fantom USB drive that has always mounted at boot and now since I installed Xubuntu 15.10 it never mounts it automatically.

There is nothing special I should be doing I don't believe. It has auto-mounted on every Ubuntu version since 9.04 Jaunty Jackalope.

I can click on it in Thunar and it mounts OK, but it should auto-mount automatically.

I've seen pages that say to add it to fstab but I'm not going to do that as I never have before.

Also in dconf-editor I do not have any media-handling option like - org.gnome.desktop.media-handling. Not sure why.

---

### Post by Cavsfan on 2015-09-21
Never mind. It was something I attempted I believe. I just logged out and back in and it was mounted.

I had added a mount point for it and noticed that when I did mount it by clicking on it then it was named /media/cavsfan/Fantom1/.

I deleted the directory and BAM back to normal.

---

### Post by Cavsfan on 2015-09-22
So, I boot up today and the USB drive is not auto mounted.

---

### Post by sudodus on 2015-09-22
There are problems with udisks, that affect the Ubuntu Startup Disk Creator. Maybe your problems are also caused by the same problems with udisks.

---

### Post by Cavsfan on 2015-09-22
> **sudodus said:**
> There are problems with udisks, that affect the Ubuntu Startup Disk Creator. Maybe your problems are also caused by the same problems with udisks.

OK, thanks for the reply. It's nothing real important. I'll just wait and see how it goes.

---

### Post by ventrical on 2015-09-22
> **Cavsfan said:**
> So, I boot up today and the USB drive is not auto mounted.

There is sometimes a lot of variation with different hardwares. I have to make sure my USB is registered in the BIOS. ie; If I disconnect my USB  hdd dock while my machine is running or reboot without the dock plugged in (just once)  it will knock  the USB out of order until it is registered during the next reboot. This is a very cagey scenario for USB hdds that have to be manually powered on before boot. I am doing emulation experiment specifically for xubuntu. I had a problem just a few minutes ago starting my MSI Mate  PC MoBo. It has latest UEFI  BIOS/Intel Gen 9 chipset and unless it is specifically *set* in BIOS it will not auto-logon during a boot. On older machine .. if I pull out the dock it becomes unrecognized until I go to BIOS and then the next reboot. After xubuntu update I'll see if I can emulate with my hardware. I do not think it is  ubuntu bug. It is BIOS logic/HID human interface management.

Regards..


Regards..

---

### Post by ventrical on 2015-09-22
No prob with this hardware..

```

ventrical@ventrical-P5QL-PRO:~$ inxi -Fxz
System:    Host: ventrical-P5QL-PRO Kernel: 4.2.0-10-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11981
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 10.6.3 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.2.0-10-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: eth2 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 200.1GB (10.6% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
           ID-2: USB /dev/sdb model: Y080M0 size: 80.0GB
Partition: ID-1: / size: 55G used: 17G (33%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 32.5C mobo: 33.0C gpu: 33.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 173 Uptime: 3 min Memory: 468.3/2000.4MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ 

```

---

### Post by ventrical on 2015-09-22
More difficult on this newer device. You have to manually power on the dock at the right time or it will lock up the BIOS.

```

ventrical@ventrical-P5QL-PRO:~$ inxi -Fxz
System:    Host: ventrical-P5QL-PRO Kernel: 4.2.0-10-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 15.10 wily
Machine:   Mobo: MSI model: B75MA-P45 (MS-7798) v: 1.0
           Bios: American Megatrends v: V1.5 date: 12/25/2012
CPU:       Dual core Intel Pentium G630 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10775
           clock speeds: max: 2700 MHz 1: 1735 MHz 2: 2640 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Sandybridge Desktop
           GLX Version: 3.0 Mesa 10.6.3 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.2.0-10-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: eth7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 200.1GB (10.6% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
           ID-2: USB /dev/sdb model: Y080M0 size: 80.0GB
Partition: ID-1: / size: 55G used: 17G (33%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 174 Uptime: 0 min Memory: 300.8/15908.8MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ 

```
Actually  the USB hdd has to be reset so this is a fail.

---

### Post by QDR06VV9 on 2015-09-22
Just an idea systemd or upstart?

---

### Post by ventrical on 2015-09-22
> **runrickus said:**
> Just an idea systemd or upstart?

I tend to agree .. (with cavsfan's setup). It could be a wait state or that the disk is not being unmounted. I do have setups  like that but not similar to cav's. I wouldn't put anything past systemd. :)

regards..

---

### Post by QDR06VV9 on 2015-09-22
I would be curious to see if cavsfan booted to upstart and found his Drive mounted.
Don't think I would bet the farm on it though.

---

### Post by Cavsfan on 2015-09-23
I never touch that USB drive. I leave it on all the time. It consumes very little energy when not in use.
I am pretty much in systemd all the time.

And the USB drive does not mount in either systemd or upstart

I tried booting into upstart but all I got was tty no GUI.
So I deleted the upstart boot line from grub.

But since you were curious if it was being caused by systemd I re-added the boot line and was able to boot into upstart for the first time.
But, the USB drive didn't auto mount and I could not suspend, restart or shutdown in upstart.

I had to press the reset button to get out of upstart.

It appears to see it - /dev/sdb but in Thunar it is grayed out and when I right click on it, the mount option is available.
It will mount if I click on mount and then it's not grayed out any more. It just doesn't do it automatically like I'm used to Ubuntu doing.

```
cavsfan@cavsfan-le-beast:~$ inxi -Fxz
System:    Host: cavsfan-le-beast Kernel: 4.2.0-10-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 15.10 wily
Machine:   Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 Bios: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22741
           clock speeds: max: 2842 MHz 1: 2842 MHz 2: 2842 MHz 3: 2842 MHz 4: 2842 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce 9800 GT/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 304.128 Direct Rendering: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.2.0-10-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (0.7% used) ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB
Partition: ID-1: / size: 19G used: 9.2G (54%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 33.0C gpu: 0.0:44C
           Fan Speeds (in rpm): cpu: 2793 fan-1: 2347 fan-3: 2712 fan-4: 0
Info:      Processes: 183 Uptime: 10 min Memory: 719.7/3951.9MB Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16 

```

---

### Post by QDR06VV9 on 2015-09-23
As I said I would not have bet the farm on it.
systemd has produced a bunch of new behavior's at least on my end, But in time I am sure I will become wiser as I learn it.
Systemd, Love it, Hate it. Or Indifferent, **it is here to stay.**
I have different results with my WD Mybook(USB) though with systemd. The Only DE that seems to be very polished right now for me is** Mate.**
I am thinking that sudodus is right about udisks(bug)
Thanks for testing that out for us(me) cavsfan.
Kind Regards

---

### Post by jeremy9856 on 2015-09-23
Cavsfan, I think you should open a bug report :
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

After that add it to this test case :
[http://iso.qa.ubuntu.com/qatracker/milestones/346/builds/102861/testcases/1628/results](http://iso.qa.ubuntu.com/qatracker/milestones/346/builds/102861/testcases/1628/results)

---

### Post by flocculant on 2015-09-23
This is definitely not a general issue - I have no problem with any sort of USB drive here. 

Which always makes for loads of fun all around while looking for the particular bit of wire's got a dodgy joint ...

---

### Post by Cavsfan on 2015-09-23
> **QDR06VV9 said:**
> As I said I would not have bet the farm on it.
systemd has produced a bunch of new behavior's at least on my end, But in time I am sure I will become wiser as I learn it.
Systemd, Love it, Hate it. Or Indifferent, **it is here to stay.**
I have different results with my WD Mybook(USB) though with systemd. The Only DE that seems to be very polished right now for me is** Mate.**
I am thinking that sudodus is right about udisks(bug)
Thanks for testing that out for us(me) cavsfan.
Kind Regards

You're welcome QDR06VV9. Upstart is way worse than systemd. Systemd is the way of the future and Arch has no problem whatsoever running systemd as it's only startup daemon or whatever it's called.
I'm done with upstart. I'm going to remove that grub entry and be done with it.

> **jeremy9856 said:**
> Cavsfan, I think you should open a bug report :
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

After that add it to this test case :
[http://iso.qa.ubuntu.com/qatracker/milestones/346/builds/102861/testcases/1628/results](http://iso.qa.ubuntu.com/qatracker/milestones/346/builds/102861/testcases/1628/results)

I leave my USB drive on 24/7 and every other version of Ubuntu has had no problem showing the USB drive as mounted. It gives the same info. as every other version of Ubuntu when booting up.
Something about cache write through or whatever on sdb or sdb1.
This is my first time trying Xubuntu. I thought I'd try it because I have Xfce as the only DE on Arch and they are almost identical.
I cannot be the only one having this problem. Or is it Xubuntu causing the problem?

> **flocculant said:**
> This is definitely not a general issue - I have no problem with any sort of USB drive here. 

Which always makes for loads of fun all around while looking for the particular bit of wire's got a dodgy joint ...

I have no problem with it. I can click on it and it opens the files; it's not like I cannot connect to it.
It just shows as greyed out and when right clicked on it gives the option to mount it.

But, I can click on it so it's no big deal. I just thought I'd mention it.

---

### Post by flocculant on 2015-09-24
>  It just shows as greyed out and when right clicked on it gives the option to mount it.As far as I am aware - that's as it should be.

---

### Post by tokyobadger on 2015-09-24
[quote="Cavsfan"]I have no problem with it. I can click on it and it opens the files; it's not like I cannot connect to it.
It just shows as greyed out and when right clicked on it gives the option to mount it.

But, I can click on it so it's no big deal. I just thought I'd mention it.[/quote]

A few questions:

1. If you open a media application eg Banshee, are files on the drive available without intervention?

2. Is there anything different in this version than in 15.04 or earlier in terms of how the OS handles the drive?

3. "Greyed out" - in which context eg dock, Thunar, other?

---

### Post by Cavsfan on 2015-09-24
> It just shows as greyed out and when right clicked on it gives the option to mount it.

> **flocculant said:**
> As far as I am aware - that's as it should be.

Good to know. Is this just with Xubuntu?

> **Cavsfan said:**
> I have no problem with it. I can click on it and  it opens the files; it's not like I cannot connect to it.
It just shows as greyed out and when right clicked on it gives the option to mount it.

But, I can click on it so it's no big deal. I just thought I'd mention it.

> **tokyobadger said:**
> A few questions:

1. If you open a media application eg Banshee, are files on the drive available without intervention?

2. Is there anything different in this version than in 15.04 or earlier in terms of how the OS handles the drive?

3. "Greyed out" - in which context eg dock, Thunar, other?

1. I don't have Banshee but do have Audacious and when I try to add songs from the USB drive I have to click on it and wait until it mounts first and then they are available.

2. Yes, this is the first version as I mentioned previously since Ubuntu 9.04 Jaunty Jackalope to do this.
But, it's also my first time trying Xubuntu too.

3. It's grayed out in Thunar.

---

### Post by QDR06VV9 on 2015-09-24
@cavsfan
> [COLOR=#000000]Upstart is way worse than systemd. Systemd is the way of the future [/COLOR]
I guess that is determined on which side of that fence you landed on.
[https://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/](https://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/)
Wish I could send systemd to the rubbish bin in flames.:D
Good thing Trusty is supported till 2019
Best OS i have used since maverick.
I have seriously thought about finding a non Debian based distro(without systemd).
And Life Goes on.

---

### Post by mc4man on 2015-09-24
Xubuntu (thunar) seems to only have settings for 'hot-plugged/inserted', by default automount should be enabled. It also breaks optical media out to separate settings than for volumes (removable), also by default set to on for parole.
As far as removable that's plugged in prior to boot it seems to not mount which I think is good behavior as compared to nautilus which automounts everything but Windows volumes & does not separate optical media from storage drives. (one automount option for all, again Gnome being short-sighted

---

### Post by Cavsfan on 2015-09-25
```
[COLOR=#000000]Upstart is way worse than systemd. Systemd is the way of the future [/COLOR]
```

> **runrickus said:**
> @cavsfan

I guess that is determined on which side of that fence you landed on.
[https://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/](https://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/)
Wish I could send systemd to the rubbish bin in flames.:D
Good thing Trusty is supported till 2019
Best OS i have used since maverick.
I have seriously thought about finding a non Debian based distro(without systemd).
And Life Goes on.

It's coming whether we want it to or not lol so may as well embrace it. :p
I deleted my Trusty and Mint 17.2 installs and replaced them with Arch Linux, which I gather is the utmost bleeding edge distro out there.
It's difficult to install I will say but Gentoo is supposed to be even more difficult.
Although I cannot imagine anything harder than installing a disk, the OS and then using command line and a wiki app on my phone to slowly build the system.
Then once you've added a kernel and all the basics you add a DE. I went with Xcfe at a friend's suggestion and loved it.
It took me about 4 days, then I gave up and a couple of days later restarted the process and realized what I had done wrong. 
It comes with systemd only and never needs rebooted when anything is updated/installed.

That is why I went with Xubuntu 15.10 to test this go round as it is pretty much identical to Arch. And I will always be testing new Ubuntu versions because of my grub wiki.

> **mc4man said:**
> Xubuntu (thunar) seems to only have settings for 'hot-plugged/inserted', by default automount should be enabled. It also breaks optical media out to separate settings than for volumes (removable), also by default set to on for parole.
As far as removable that's plugged in prior to boot it seems to not mount which I think is good behavior as compared to nautilus which automounts everything but Windows volumes & does not separate optical media from storage drives. (one automount option for all, again Gnome being short-sighted

I have the exact same settings as you have. So, I guess it is just a Xubuntu thing right? 
It is that way on Arch Linux, but when you attempt to mount another system's partition it wants a sudo password or it will not be mounted.

Too bad Ubuntu isn't as secure as that is. I had to install a package called **udevil** (of all names lol) to automount my USB drive at startup and it works well.

The main reason this is a problem is that I have VinDSL's conky on all my Linux systems and it shows how much is used and what it available etc.
But, it does not show anything until I manually mount it.

Thank you kindly for the posts. :)

---

### Post by QDR06VV9 on 2015-09-25
> [COLOR=#000000]It's coming whether we want it to or not lol so may as well embrace it. [/COLOR]:razz:
I am embracing it;)
[IMG]http://i.imgur.com/nlyfHAe.gif[/IMG]

---

### Post by Cavsfan on 2015-10-13
I installed ntfs-config and configured it to connect the external USB drive but it also wanted to connect the internal windows partition which cannot really be done with Windows 10.

But, it didn't seem to work so I purged it. Then I logged out and it seemed in Thunar that it was connected (not grayed out).

Then I noticed the conky still didn't show it but the conky was referring to **/media/cavsfan/Fantom/** while Thunar showed it as **/media/Fantom/**.

So, once I changed it in the conky viola, working fine again finally. I logged out twice and it's still connected at login.

I'll report back tomorrow if it holds through a reboot. :D

---

### Post by Cavsfan on 2015-10-17
I'm not sure if ntfs-config messed my system up or not but I had to re-install a day or so.

I've read not to use ntfs-config as it re-writes your /etc/fstab file.

Does anyone know much about ntfs-config?

---

### Post by jerrylamos on 2015-10-17
Plugged in a USB stick.  Wily 15.10 didn't see it.  Files didn't see it.  Files Computer didn't see it.

Gparted saw it, so I could see the  /dev/sdc O.K.

Wily still didn't see it.

did a dd if=wily....iso of=/dev/sdc bs=4M

Ran fine

sudo umount /dev/sdc*     said it wasn't mounted.

sudo sync

Removed USB stick and plugged it back in, Wily saw it just fine, what did I want to do.

Hmmmm

---

### Post by ventrical on 2015-10-17
> **runrickus said:**
> I am embracing it;)


Incredible. :)

---

### Post by mc4man on 2015-10-18
> **Cavsfan said:**
> I'm not sure if ntfs-config messed my system up or not but I had to re-install a day or so.

I've read not to use ntfs-config as it re-writes your /etc/fstab file.

Does anyone know much about ntfs-config?
If your file manager doesn't allow setting an internal volume to automount on bootup/login then you'd need to add an fstab entry to do so. Can't see that ntfs-config does anything wrong there, at least with ntfs volumes.

Myself don't see the need to automount internal volumes, only takes a sec per session to do so thru the file manager
(when mounted thru FM the you can umount the volume, when done thru fstab then only root can.

---

### Post by sudodus on 2015-10-18
> **jerrylamos said:**
> Plugged in a USB stick.  Wily 15.10 didn't see it.  Files didn't see it.  Files Computer didn't see it.

Gparted saw it, so I could see the  /dev/sdc O.K.

Wily still didn't see it.

did a dd if=wily....iso of=/dev/sdc bs=4M

Ran fine

sudo umount /dev/sdc*     said it wasn't mounted.

sudo sync

Removed USB stick and plugged it back in, Wily saw it just fine, what did I want to do.

Hmmmm

There are bugs in udisks2, for example this one [Erasing disk failed: Error wiping newly created partition](https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1460602)

Maybe you are affected by such a bug, and after 'cleaning' the partition table, it works again.

(mkusb provides a 'safety belt' around what you did to solve the problem - [there is a wipe menu now](https://help.ubuntu.com/community/mkusb#Wipe_menu))

---

### Post by Cavsfan on 2015-10-18
Actually the only reason I wanted the external USB drive to automount on boot, which every other version of Ubuntu I've ever dealt with does is because VinDSL's conky displays information about the USB drive.
Like how much is used/unused in a lua bar and the percentage that is free.

I'm not sure if ntfs-util actually made it mount every boot or not, but I am definitely not wanting to touch the fstab file to do anything.

I'll just click on it to mount it in Thunar.

Thanks for the replies.

---

### Post by Cavsfan on 2016-03-12
Finally figured out how to auto-mount the 1TB USB drive that sits on my computer desk.

I created the mount point: ```
sudo mkdir /media/cavsfan/Fantom
```

Then added ```
sudo mount /dev/sdb1 /media/cavsfan/Fantom/
``` to **/etc/rc.local**.

Rebooted and BAM it's mounted automagically. :popcorn:

Now this thread really is solved. I guess Xubuntu is the only one that doesn't automount USB drives...
It's the only flavor of Ubuntu that I've used that doesn't any way.
I googled how to run sudo at startup and this was the top link: [http://ubuntuforums.org/showthread.php?t=1822137](http://ubuntuforums.org/showthread.php?t=1822137)

---

### Post by Cavsfan on 2016-09-25
Installed Yaketty Yak 16.10 yesterday and the way to get a USB drive, that is always on, to automount at boot is different that it was for Xenial Xerus 16.04 LTS.
This also worked for Zesty Zapus 17.04 and Artful Aardvark 17.10.

I entered this in terminal:
```
sudo mkdir /media/cavsfan/Fantom
```
Then created a script simply named **fantom** with this in it:
```
#!/bin/bash
# Mount Fantom USB drive
sudo mount /dev/sdb1 /media/cavsfan/Fantom/

exit 0
```
Then I made it executable **chmod 755 fantom** and copied it into **/etc/init.d** like this: **sudo cp fantom  /etc/init.d/fantom**

You also have to make a symlnk for it to work **sudo ln -s /etc/init.d/fantom /etc/rc3.d/S01fantom**

I had looked in that folder and seen that everything started with S01, so I knew I should begin the name with that.
I rebooted and it was mounted.

Problem once again solved. Although these instructions are 3 years old, I was able to use them with some modifications [here]("http://askubuntu.com/questions/290099/how-to-run-a-script-during-boot-as-root").

I hope this helps someone else. :)

---

### Post by deadflowr on 2016-09-25
> You also have to make a symlnk for it to work **sudo -s /etc/init.d/fantom /etc/rc3.d/S01fantom**
don't you need an **ln** in there to make a link?

---

### Post by Cavsfan on 2016-09-26
> You also have to make a symlnk for it to work **sudo ln -s /etc/init.d/fantom /etc/rc3.d/S01fantom**

> **deadflowr said:**
> don't you need an **ln** in there to make a link?

Yes, thank you for catching that. I corrected it in my post and my quote of your post.
The link I posted had the **ln** in it.

---

### Post by Cavsfan on 2017-03-04
I installed Zesty Zapus 17.04 today and was trying to get my Fantom USB once again to mount.

It was the same way it was for 16.10 but, I had some major typo errors in that fix.

They are corrected now and I'm surprised someone didn't catch more than what          deadflowr did because I was really scratching my head before I figured it out.

I had mixed **rc2.d **and** [B]rc3.d**[/B], which is very wrong and I was copying the file to the linked folder initially and then linking it, which of course did not work.

But, it's good to go now. This is more than a little embarrassing. :redface:

---

### Post by Cavsfan on 2017-06-29
Artful Aardvark 17.10 worked the exact same way to auto-mount a USB drive as in post [#32]("https://ubuntuforums.org/showthread.php?t=2295804&page=4&p=13549647#post13549647") of this thread.

---

### Post by Cavsfan on 2018-03-11
Still works for Xubuntu Bionic Beaver 18.04.

---

