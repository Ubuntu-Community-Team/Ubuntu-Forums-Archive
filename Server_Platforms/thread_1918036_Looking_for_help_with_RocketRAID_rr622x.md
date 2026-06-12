---
title: "Looking for help with RocketRAID rr622x"
date: 2012-01-31
forum: Server Platforms
---

### Post by Cluster_1 on 2012-01-31
Hi,

I've been doing a lot of Google searching the past couple of days. I am in the process of rebuilding one of my computers and using it as a server. Previously it was running WHS2011 with a 500gb boot drive however the drive was old and crashed, during the time it was up WHS2011 didn't perform to what I had actually hoped for. 

This is a desktop pc I built over a year ago, it has a powerful processor, ton of ram, and a lot of hard drive space. My only problem is the Highpoint RocketRAID 622 PCI-e card that was shipped with the SANS Digital Tower units I bought. I have 2 5-bay units that run do not run in RAID Mode. Just JBOD. I did try the raid setup and unless your using raid qualified drives the speed is just horrible. 

I've been testing several distributions of linux. Opensuse, ClearOS, Fedora.. but they all have one issue and that is they do not support the RocketRAID card. I have been to high points web site and downloaded the open source drivers to compile and I get an error stating that the kernel i'm trying to build on is to old 2.1/2.4 need 2.6 in order for it work, but the kernel I've used is 2.6.* and fails to compile. I contacted highpoint about this issue and they are no longer providing support for that card as they are working on new cards for support and they even directed me to a link to purchase a new card. I suppose this is what happens when you get it free. 

This week I want to get that computer online, my new drive just arrived for boot and I want to really get linux on it. I would prefer it run headless if I could this computer basically sits in the corner and is used for storage people throughout the house can access it and perform daily or weekly backups to it, but before I pull out my hair (whats left of it.) I need to make sure that I can get that card to detect and detect all the drives under Linux. WHS2011 didn't look put together, honestly when you install it it boots up and its really Windows Server 2008 R2, but dumbed down home version and whats worse is it needs to be have a defrag run on it, imagine running defrag on over 20 harddrives, its not pretty. 

Is the a ubuntu server release that has support for the rocketraid card rr622x? Normally I would keep searching but aside from the down computer I also injured my back recently (again) and I am not supposed to spend to much time sitting in front of a computer installing every distro out there till I find one that works. 

Thanks for taking the time to read this.

Cluster_1

---

### Post by rubylaser on 2012-01-31
What release of Ubuntu are you running?  I hope you're trying this on 10.04 LTS, so you're not running into problems compiling against a 3.x kernel.  Also, I assume you tried following [these directions]("https://help.ubuntu.com/community/RocketRaid")?   I don't have one of these cards, but those directions are straightforward and look like they should work.  

If you're using Ubuntu server 10.04, it should be this easy.
```
sudo -i
wget "https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=view&target=rr62x-dkms_1.1_all.deb" -O rr62x-dkms_1.1_all.deb
dpkg -i rr62x-dkms_1.1_all.deb
echo "rr62x" >> /etc/initramfs-tools/modules
reboot
```

I hope that helps.

---

### Post by Cluster_1 on 2012-01-31
I was going to try the latest release of Ubuntu. 11.10 I believe. I can download and try it on 10.04 LTS I really just need this to be a server machine and getting that card to work would solve a lot of issues. I thank you for your reply and wonder how I went to google and didn't find these. I thank you for your help! I will try this tonight after dinner I don't mess with a computer if I have to keep walking away from it.

---

### Post by acdcfanbill on 2012-04-22
Has anyone had any problems with this method in 12.04?

I get an error on the dpkg command.
```
Unable to load DKMS tarball /usr/share/rr64x-dkms/rr64x-1.0.dkms.tar.gz.
Common causes include:
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rr64x-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rr64x-dkms

```possibly an error due to 12.04 using kernel 3.2?

---

### Post by rubylaser on 2012-04-22
If the DEB packages aren't working for you, you could build the modules yourself. Here are the [directions]("https://help.ubuntu.com/community/RocketRaid").

---

### Post by acdcfanbill on 2012-04-22
getting a warning in the make/make install
```
bill-nas@ubuntu-nas:~/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/os_linux.o
  CC [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/osm_linux.o
  CC [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/div64.o
  CC [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/hptinfo.o
  CC [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/config.o
  LD [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/rr62x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/.him_magni.o.cmd for /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/him_magni.o
  CC      /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/rr62x.mod.o
  LD [M]  /home/bill-nas/highpoint_rr_stuff/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/rr62x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'


```

unfortunately linux still doesn't see the drive attached to my highpoint card.  ```
lshw -C disk 
``` lists my SSD OS drive and a connected USB drive. 
do we think the Warning is the culprit or did I goof something else up?

---

### Post by rubylaser on 2012-04-22
The make didn't finish, so it doesn't have the modules properly built to support your card yet.  You'll need to get that to compile properly before it will work.

---

### Post by CharlesA on 2012-04-22
Read this:

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

Sidenote: You need to do:

```
sudo make install
```

In order to install the kernel modules.

---

### Post by acdcfanbill on 2012-04-22
Yea, I followed that guide, changing all the 3.0 kernel references to 3.2 for the 12.04 release of ubuntu.  Then I did a sudo make and a sudo make install.  it didn't seem to complain about installing the module, but of course it doesn't work so i assumed the warning I got is what's failing to make the module properly

```
WARNING: could not find /[....]/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/.him_magni.o.cmd for /[....]/rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build/him_magni.o
```

the rr62x-linuxla-src-v1.0/product/rr62x/linuxla/.build directory surely doesn't have the him_magni.o.cmd file that make is complaining about.  I got the drivers from highpoint so I was wondering if anyone knew why this would be missing or if anyone had a workaround/fix/etc

---

### Post by pals0007 on 2012-05-03
Cant anyone help out a newb, i have been trying for weeks and cannot get it done, can someone please compile and send to me, i am begging here looking for highpoint 622 raid drivers.

---

### Post by CharlesA on 2012-05-03
> **pals0007 said:**
> Cant anyone help out a newb, i have been trying for weeks and cannot get it done, can someone please compile and send to me, i am begging here looking for highpoint 622 raid drivers.
You would have to compile them yourself. What version of Ubuntu are you using?

---

### Post by pals0007 on 2012-05-03
OMG Charles you would be a life savor, I am using the latest ubuntu build 12.04lts 64bit, and I am in desperate need of the Highpoint Rocketraid 622 drivers.

---

### Post by CharlesA on 2012-05-03
> **pals0007 said:**
> OMG Charles you would be a life savor, I am using the latest ubuntu build 12.04lts 64bit, and I am in desperate need of the Highpoint Rocketraid 622 drivers.
Have you tried the ones listed here?

[https://help.ubuntu.com/community/RocketRaid#Shortcut_-_DEB_Packages_for_DKMS](https://help.ubuntu.com/community/RocketRaid#Shortcut_-_DEB_Packages_for_DKMS)

Actually those won't work. Watch this space.

---

### Post by pals0007 on 2012-05-03
Yes I have, I have tried the .deb package but the install always quits (and now everytime i try and install something new the rr622x package tries to reinstall but always fails) I have also tried to go through the package modifications it list, but I am so new to linux and not good at anything yet, when I go to compile the package I get like a hundred errors. I have tried several times starting from scratch to recompile it for the 3.2 kernel but I fail to do it everytime. Dont even know if i am getting closer. I have been desperatley trying to stick with this linux thing, I even deleted my windows partition to force myself, I have everything I need except the access to my 10tb enclosure which is ran off of the Highpoint card, This totally sucks since it currently houses all my music, movies, and family photos. I am just at total loss when it comes to compiling for linux, also watched about 4 hours of youtube videos, like I said I think I am getting close but not really

---

### Post by CharlesA on 2012-05-03
> **pals0007 said:**
> Yes I have, I have tried the .deb package but the install always quits (and now everytime i try and install something new the rr622x package tries to reinstall but always fails) I have also tried to go through the package modifications it list, but I am so new to linux and not good at anything yet, when I go to compile the package I get like a hundred errors. I have tried several times starting from scratch to recompile it for the 3.2 kernel but I fail to do it everytime. Dont even know if i am getting closer. I have been desperatley trying to stick with this linux thing, I even deleted my windows partition to force myself, I have everything I need except the access to my 10tb enclosure which is ran off of the Highpoint card, This totally sucks since it currently houses all my music, movies, and family photos. I am just at total loss when it comes to compiling for linux, also watched about 4 hours of youtube videos, like I said I think I am getting close but not really
Wow. I remember it taking me a few days to get the drivers for my raid card to compile correctly on 3.2 when I was thinking about bumping up to Precise.

Anyhow, I got them to compile fine via dkms (which is what you want unless you want to be compiling them again after each kernel upgrade).

I've attached the tar.gz to this post.

You will need to install dksm before running the install script inside the tar.

```
sudo apt-get install dkms linux-headers-3.2.0-24-generic
```
```
tar -xf rr62x.tar.gz
```
```
cd rr62x
```
```
chmod +x install
```
```
sudo ./install
```

EDIT: Nevermind, the tar is too big to fit on the forum, so I am going to upload it to my website here:
[http://charlesa.net/files/rr62x.tar.gz](http://charlesa.net/files/rr62x.tar.gz)

---

### Post by pals0007 on 2012-05-04
> **CharlesA said:**
> Wow. I remember it taking me a few days to get the drivers for my raid card to compile correctly on 3.2 when I was thinking about bumping up to Precise.

Anyhow, I got them to compile fine via dkms (which is what you want unless you want to be compiling them again after each kernel upgrade).

I've attached the tar.gz to this post.

You will need to install dksm before running the install script inside the tar.

```
sudo apt-get install dkms linux-headers-3.2.0-24-generic
``````
tar -xf rr62x.tar.gz
``````
cd rr62x
``````
chmod +x install
``````
sudo ./install
```EDIT: Nevermind, the tar is too big to fit on the forum, so I am going to upload it to my website here:
[http://charlesa.net/files/rr62x.tar.gz](http://charlesa.net/files/rr62x.tar.gz)


OK so I downloaded the file you so graciously uploaded for me, Thank you very much.
I followed your instructions, and it says that the install completed successfully, but? I cannot see my disk nor the scsi adapter in the Disk Utility, this is what I get in the terminal after install, Am I missing something?

```

jesse@Jesse-PC:~/Downloads$ tar -xf rr62x.tar.gz
jesse@Jesse-PC:~/Downloads$ cd rr62x
jesse@Jesse-PC:~/Downloads/rr62x$ chmod +x install
jesse@Jesse-PC:~/Downloads/rr62x$ sudo ./install

Creating symlink /var/lib/dkms/rr622/1.1/source ->
                 /usr/src/rr622-1.1

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-23-generic -C product/rr62x/linux/ KERNELDIR=/lib/modules/3.2.0-23-generic/build.....
cleaning build area....

DKMS: build completed.

rr62x:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod......

Backing up initrd.img-3.2.0-23-generic to /boot/initrd.img-3.2.0-23-generic.old-dkms
Making new initrd.img-3.2.0-23-generic
(If next boot fails, revert to initrd.img-3.2.0-23-generic.old-dkms image)
update-initramfs........

DKMS: install completed.
jesse@Jesse-PC:~/Downloads/rr62x$ 


```

---

### Post by CharlesA on 2012-05-04
Reboot so the modules are loaded automatically.

---

### Post by pals0007 on 2012-05-04
I have rebooted several times, The disk and card are picked up in the bios, If i boot to windows it works, just not in Ubuntu,

---

### Post by CharlesA on 2012-05-04
Ok. Run this:

```
sudo modprobe rr62x
```

```
sudo fdisk -l
```

Also run this and post the output:

```
sudo lspci
```

---

### Post by pals0007 on 2012-05-04
Ok here is what I have 
after the 
sudo modprobe rr62x
now they show up before they didnt

```

jesse@Jesse-PC:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes [COLOR=Red]This is the windows drive[/COLOR]
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x090bd3e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   117227519    58254336    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 150.0 GB, 150039945216 bytes [COLOR=Red]This drive is windows apps, linux swap, Ubuntu partition[/COLOR]
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a7dc694

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   190644223    95321088    7  HPFS/NTFS/exFAT
/dev/sdb2       190644224   198456723     3906250   82  Linux swap / Solaris
/dev/sdb3       198457342   293046271    47294465    5  Extended
/dev/sdb5       198457344   293046271    47294464   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes [COLOR=Red]This drive is for music[/COLOR]
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7011d043

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   234438655   117218304    7  HPFS/NTFS/exFAT

Disk /dev/sde: 500.1 GB, 500107862016 bytes [COLOR=Red]This drive is on the external enclosure[/COLOR]
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73598171

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes [COLOR=Red]This drive is on the external enclosure[/COLOR]
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3cb6d21d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes [COLOR=Red]This drive is on the external enclosure[/COLOR]
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x87c263a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT


```

The external enclosure dirves is what I have been looking for

```

jesse@Jesse-PC:~$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4290]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 0622 (rev 01)
02:00.1 IDE interface: Marvell Technology Group Ltd. 88SE91A4 SATA 6Gb/s Controller (rev 11)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
05:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
07:00.0 Multimedia video controller: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller

```

---

### Post by CharlesA on 2012-05-04
Ok, does it show up after rebooting now?

---

### Post by pals0007 on 2012-05-05
> **CharlesA said:**
> Ok, does it show up after rebooting now?

Nope, after a reboot the drives did not show back up, not until I did a 
sudo modprobe rr62x

---

### Post by CharlesA on 2012-05-05
> **pals0007 said:**
> Nope, after a reboot the drives did not show back up, not until I did a 
sudo modprobe rr62x
Huh, it should load automatically, which is the whole point of using something like dkms.

Post the output of:

```
ls -ld /var/lib/dkms/rr622
```

```
uname -r
```

---

### Post by pals0007 on 2012-05-08
Sorry I have been out of town.

I did a fresh reboot and do not see the drives again, I ran the commands you asked and this is what shows up

jesse@Jesse-PC:~$ ls -ld /var/lib/dkms/rr622
drwxr-xr-x 3 root root 4096 May  4 01:21 /var/lib/dkms/rr622

jesse@Jesse-PC:~$ uname -r
3.2.0-24-generic

---

### Post by pals0007 on 2012-05-08
Whats weird is after a fresh boot the drives dont show, but if I do 

sudo lspci 
It list the highpoint card, but still the drives do not show

---

### Post by pals0007 on 2012-05-08
The disk only show up after doing 

sudo modprobe rr62x 
Just so I understand what is "modprobe" mean?

---

### Post by CharlesA on 2012-05-08
> **pals0007 said:**
> Sorry I have been out of town.

I did a fresh reboot and do not see the drives again, I ran the commands you asked and this is what shows up

jesse@Jesse-PC:~$ ls -ld /var/lib/dkms/rr622
drwxr-xr-x 3 root root 4096 May  4 01:21 /var/lib/dkms/rr622

jesse@Jesse-PC:~$ uname -r
3.2.0-24-generic

Oops, I meant run:

```
ls -l /var/lib/dkms/rr622/
```

It should look like this:

```
charles@Atlantis:~$ ls -l /var/lib/dkms/rr622/
total 4
drwxr-xr-x 4 root root 4096 May  3 10:14 1.1
lrwxrwxrwx 1 root root   27 May  3 10:14 kernel-3.2.0-24-generic-x86_64 -> 1.1/3.2.0-24-generic/x86_64

```


> **pals0007 said:**
> The disk only show up after doing 

sudo modprobe rr62x 
Just so I understand what is "modprobe" mean?

modprobe just loads kernel modules. I'm not sure why the module isn't loading automatically.

What happens if you run this:

```
sudo dkms install -m rr622 -v 1.1
```

It should tell you:

Module rr622/1.1 already installed on kernel 3.2.0-24-generic/x86_64

---

### Post by pals0007 on 2012-07-11
jesse@Jesse-PC:~$ ls -l /var/lib/dkms/rr622/
total 4
drwxr-xr-x 6 root root 4096 Jul 10 12:30 1.1
lrwxrwxrwx 1 root root   27 May  4 01:02 kernel-3.2.0-23-generic-x86_64 -> 1.1/3.2.0-23-generic/x86_64
lrwxrwxrwx 1 root root   27 May  4 01:21 kernel-3.2.0-24-generic-x86_64 -> 1.1/3.2.0-24-generic/x86_64
lrwxrwxrwx 1 root root   27 Jul 10 12:31 kernel-3.2.0-26-generic-x86_64 -> 1.1/3.2.0-26-generic/x86_64
jesse@Jesse-PC:~$

---

### Post by pals0007 on 2012-07-11
jesse@Jesse-PC:~$ sudo dkms install -m rr622 -v 1.1
[sudo] password for jesse: 
Module rr622/1.1 already installed on kernel 3.2.0-26-generic/x86_64
jesse@Jesse-PC:~$

---

### Post by CharlesA on 2012-07-11
Should be working after a reboot.

---

