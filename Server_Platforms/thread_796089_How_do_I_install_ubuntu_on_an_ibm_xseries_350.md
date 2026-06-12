---
title: "How do I install ubuntu on an ibm xseries 350?"
date: 2008-05-16
forum: Server Platforms
---

### Post by battista on 2008-05-16
I have shortly purchased an older ibm xseries 350 Server. It came with 8GB RAM, 4 xeon 900 processors, an ibm dualchannel serveraid scsi controller with 6 harddisks configured as raid5. The system has a CD ROM boot device and a very restricted bios. 

This is where my problems starts. I tried to install opensuse 10.3, but it failed. I tried ubuntu gutsy, it failed. I tried openSuse 10.2, and it worked fine.

The motherboard is equipped with a rare ServeRaid OSB4 chipset, that controls the CD ROM device. 

I believe that sometime between Opensuse 10.2 and 10.3, or between feisty and gutsy, there has been a change in the os drivers and/or environment, which causes newer linux os versions (knoppix, opensuse 10.3, ubuntu guty and hardy heron) to cause failures reading the cd rom, no matter what you do. 

This causes any installation attempt from cdrom to abort sooner or later. In most cases, some of the drivers are not loaded or fail to be unpacked.

This results in media fail errors.

Opensuse 10.3 comes up with a sector read error at sector 108 or 112. Hardy Heron says the hardy.gz archive can't be unpacked and so on.

Am I missing some boot parameters maybe?

I checked every possible reason (faulty cds, faulty hardware drive): The CD media are always okay, the cd drive is okay (using a different cd rom drive doesn't change anything), and every cdrom is well read on the same drive, as long as you use an older linux, for example is you mount and copy it from a booted 10.2 opensuse. 

So I am stuck with opensuse 10.2        :-(

If you boot a newer cd rom, the cd device starts having sector read errors (opensuse) or bad packages (ubuntu). The same cd-rom rechecked on the same drive under 10.2 opensuse is fully read and/or unpacked, of course.

Now unfortunately the ibm bios is not very flexible installing other boot devices (except floppy disk maybe).

So how can I install a newer os on this server (preferred any debian/ubuntu derivate) by avoiding this problem?


Until now any of my installation attemts failed.

Unfortunately I have only limited knowledge of other installation methods than an automated download and/or a booted distribution cd.

---

### Post by Sef on 2008-05-16
Moved to Server Platforms.

---

### Post by battista on 2008-05-16
> **Sef said:**
> Moved to Server Platforms.

Thanx. Wasn't sure about the right category.

---

### Post by PhilippWollermann on 2008-05-16
What about updating the BIOS? :)

If there is no newer version, you could just install an older Ubuntu version and then upgrade your way to Hardy.

---

### Post by Synoia on 2008-05-18
I had similar problems on an Xseries 360. The install cd failed with read errors. I put in a new IBM part numer CD, no change. Update the BIOS no change. Burnt the CD on different media, different CD burners, different CD burning programs, no change. I was able to install Win XP, Vista, and 2003 Server without trouble.

Xseries Config, 2 Gbyte memory, 4 processors, 2 x 15 GByte Xseries SCSI disks (Disk 0 and Disk 1).

This is what I did, for a hard disk install:

1. Installed windows on Disk 0. 
2. Installed WinGrub on windows.
3. Copied an image of the install CD to the windows drive. PowerISO under windows should copy your install CD image.
3. Downloaded the hd install kernal (vmlinuz), and initrd.gz, for my version of Ubuntu to my hard drive.

Here's the URL for vmlinuz & initrd.gz

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

Replace "**edgy**" wih your version of Ubuntu, mine was version 7.04 or "**fiesty**". You can browse around the archive tree to find your version of these files.

4. Created & formatted, & mounted (under windows) a 1 Gbyte **FAT** partition on Disk 1.
5. Copied the .iso image file, vmlinuz & initrd.gz to this new partition.
6. Started wingrub. Was very careful to put GRUB on the disk 1, partition 0 (I did it on the disk 0 and this version of grub does not read NTFS partition, so I had to fix the windows MBR).
7. On my CD, the loader was ISOLinux. On my CD there is an ISOlinux directiory, with an ISOlinux.cfg file. To use the "preseed" supplied with the install CD, I copied the kernal paramters line from the ISOlinux.cfg file

**APPEND  preseed/file=/cdrom/preseed/s2p.seed locale=en_US initrd=/install/initrd.gz rw quiet -- **

into the MENU.lst file in the Grub directry on Disk 1. My MENU.lst file became:

[B]timeout 10

title HardDisk Installer
root (hd0,0)
kernel /boot/vmlinuz preseed/file=/cdrom/preseed/s2p.seed locale=en_US vga=normal ramdisk_size=14972 root=/dev/rd0 rw quiet -
initrd /boot/initrd.gz [/B]


8. Shutdown Windows. Remove Disk zero. (This works without cutting power, I did it in the long bootup phase before BIOS writes to the display). You will get an error light from the Xseries. Ignore it.

9. The system rebooted using grub, and if you've not messed up any file names this should install whatever is on you linux distribution.

Good luck, this took me two weeks to work through, and I knew nothing about Linux installation before I started! No Warrenties Expressed or Implied.

---

### Post by battista on 2008-05-19
@ Synoia

Thanks. I thought I was getting crazy about this.


There must be some sort of incompatibility with ServerWorks OSB4 chipset that causes this problem. There doesn't seem to be any direct solution to solve this, so the way you recommended seems to be a good orkaround.


I was wondering if an alternative could also be to attach a SCSI CD ROM drive to the onboard adaptec controller. As far as I know, the adaptec bios does also support booting from attached CD ROMs. 

Did you try this?

If you didn't: Does anyone else know if booting from SCSI CD-ROM works on these machines?

--
PS: 
I also had a 4 processor multithread xseries 360 until last year. Fine machine. But this baby consumes a whole lot of electricity. As we pay 24 eurocents here in germany for one kilowatthour, it significantly started eating up my salary, so I had to get rid of it :-((

---

### Post by /etc/init.d/ on 2008-05-19
Install Ubuntu from a USB flash drive or an external USB CD drive.

---

### Post by battista on 2008-05-19
> **/etc/init.d/ said:**
> Install Ubuntu from a USB flash drive or an external USB CD drive.

I don't have a boot option for usb devices on this machine. 

It's too old and it doesn't give you this kind of bios option. 

Okay, I could take a stick, put some ext2 filesystem on it and copy the cd core onto it and/or create an /etc/apt/sources entry for the stick. 

But as far as I see, this doesn't bring me any further on how do to boot my hardy heron. 

Or are there floppy disk sets available with a hardy heron ubuntu kernel that allow me to change the install source from /dev/cdrom to whatever is necessary (some /dev/sdxx maybe)?

---

### Post by battista on 2008-05-28
I just read about another solution that seems to work:

```

ftp://archive.ubuntulinux.org/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso

```

Thanks to everyone for the assistance.

---

### Post by NateMan on 2008-05-28
So your going to install over the network? The link just downloaded myself an installer. Where's the page to the guide for it? Or what it is? I've been meaning to setup a pxe server to do easy ubuntu installs.

---

### Post by windependence on 2008-05-28
I was thinking maybe ftp install but I don't think Ubuntu offers that option. I know SuSE used to.

-Tim

---

### Post by NateMan on 2008-05-28
One idea is installing an older working distro and upgrading the version to 8.04. Kinda a hack idea, but it might be easier than many other options.

---

### Post by skillit on 2009-04-21
I think this is the link he is referencing:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It is the installation instructions for using the mini.iso.

---

### Post by Ravaun on 2011-03-16
The Xeon 900 cpu ("Cascades") is a Pentium-III class processor.  Ubuntu has a minimum install recommend of 1Ghz.  This may be the issue, since the CD-Rom drive likely only uses ONE cpu to access vs. all 4 Xeon 900's.


Most server-based installs are modular, loading the Kernal and essential system files into memory, followed by a Hard Drive write of necessary install files.  Cpu usage is fairly low-key during such an install (Windows 9x, XP, and Vista all use this technique.  Not sure if Windows 7 does.)


From what I've seen, Ubuntu sets up pretty much on-the-fly, which is heavily cpu-intensive.  Once the basic set-up is achieved, the install files (what MS calls CAB files and Ubuntu calls Packages) are copied to the HD and the set-up of the X-server (aka GUI or Desktop Environment) ensues.  All of which is VERY cpu-intensive.

[I have noticed that Vista (if you disable the initial screen-blanking) actually boots up much like a Linux install does, albeit faster. (Assuming it's not handling an Update install, which can take Hours!)]


There may also be an issue of DMA (Direct Memory Access); CD-ROM to Memory.  Uncertain as to how the X-series handles such acesses, as info. on them is fairly sparse (after a 45 mins of web searching).


Most likely issue was with the Video subsystem the 350 uses.  That's where 95% of all OS installs I've overseen fail.  (I've done DOS 2.0 to Windows Vista, various versions of Linux distros, and a few VM installs.  Never a MAC install, though...thank the Goddess!)

---

