---
title: "My 1st UEFI Install Experience."
date: 2019-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2019-06-07
Hello Ububtu forums,

I acquired an HP Pavilion 500-054 desktop computer ***inxi -Fxz*** specs posted below.

I've read some horror stories about newer HP Computers and Linux installs on different forums.

After receiving this desktop computer with a working Microsoft Windows 8.1 installed I immediately disconnect the 1.5 TB mechanical hard drive and replace it with a 500 GB mechanical hard drive.

All back together and connected I powered up and went into bios settings and reset bios to oem factory defaults then saved and exited and Ubuntu 18.04 took off and installed without a hitch.

After install completed I remove the installation media and updated then installed a few bits of software and all is working great.


My Specs.

```
thomas@hp-pavilion-500-054:~$ inxi -Fxz
System:    Host: hp-pavilion-500-054 Kernel: 4.15.0-51-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu3) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop System: Hewlett-Packard product: 500-054 serial: N/A
           Mobo: MSI model: 2AE0 v: 1.0 serial: N/A UEFI: AMI v: 80.34 date: 06/13/2013
CPU:       Quad core AMD A8-5500 APU with Radeon HD Graphics (-MCP-) arch: Piledriver rev.1 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 25553
           clock speeds: max: 3200 MHz 1: 1817 MHz 2: 1731 MHz 3: 1469 MHz 4: 1774 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Trinity [Radeon HD 7560D] bus-ID: 00:01.0
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon Resolution: 1152x720@59.97hz
           OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 4.15.0-51-generic, LLVM 7.0.0)
           version: 4.3 Mesa 18.2.8 Direct Render: Yes
Audio:     Card Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.15.0-51-generic
Network:   Card-1: Qualcomm Atheros AR8161 Gigabit Ethernet driver: alx port: e000 bus-ID: 01:00.0
           IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Ralink RT5390R 802.11bgn PCIe Wireless Network Adapter
           driver: rt2800pci v: 2.3.0 bus-ID: 04:00.0
           IF: wlp4s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (1.8% used)
           ID-1: /dev/sda model: ST9500325AS size: 500.1GB
Partition: ID-1: / size: 457G used: 8.5G (2%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 2.0C mobo: N/A gpu: 1.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 200 Uptime: 2:33 Memory: 1125.5/7162.9MB Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
thomas@hp-pavilion-500-054:~$ 



```

---

### Post by rbmorse on 2019-06-07
That's great to hear. 

I haven't seen too many complaints about HP desktop machines being particularly difficult Linux installs, but some of their laptop models seem to be very problematic due to some vendor specific code HP uses in their UEFI setups, mostly around how the bootloader is handled. Rod Smith's rEFInd has been a valuable tool, but I understand the reluctance of some to depend upon a utility that lives outside of a distribution's application repository.

---

### Post by poorguy on 2019-06-07
> **rbmorse said:**
> That's great to hear. 

I haven't seen too many complaints about HP desktop machines being particularly difficult Linux installs, but some of their laptop models seem to be very problematic due to some vendor specific code HP uses in their UEFI setups, mostly around how the bootloader is handled..
It is very possible that the stories I read were related to laptops as some of them can be very problematic.

I do know that on this particular desktop that the bios is very reluctant to accept or complete any new changes which is why I chose the default settings.

---

### Post by Dennis N on 2019-06-07
> I do know that on this particular desktop that the bios is very reluctant to accept or complete any new changes which is why I chose the default settings.
Updating the UEFI firmware may help with usability. Yours looks a bit old: Jun 2013. You might check if any is available.

---

### Post by kurt18947 on 2019-06-07
I'm not well versed about HP, laptops are Thinkpads and desktops are home built AMD. What I recall about HP problems is that they were using 32 bit UEFI which linux distros didn't support. I also recall reading a blog post type thing where the writer had HP laptop/ultra light (HP Stream maybe?) and finally figured out that the boot loader was looking one one specific Microsoft flavored file name, something like bootmgr.exe. He renamed that file so it wasn't recognized then gave the GRUB boot file that name. It booted right into GRUB:lolflag:. The bootloader was just looking for a certain file name that was bootable. The actual contents of the file did not appear to be that important, just that it was bootable.

---

### Post by poorguy on 2019-06-08
> **Dennis N said:**
> Updating the UEFI firmware may help with usability. Yours looks bit old: Jun 2013. You might check if any is available.

Never been a fan of updating bios unless I was having major motherboard issues.

There are a couple of newer bios updates so I'll look into those and see what fix they offer.

---

### Post by poorguy on 2019-06-08
> **kurt18947 said:**
> I'm not well versed about HP, laptops are Thinkpads and desktops are home built AMD. What I recall about HP problems is that they were using 32 bit UEFI which linux distros didn't support.

I don't know much about HP Computers other than I know a lot of people who use HP computers and never have any problems with them until they try to dual boot Windows 10 and Linux then the problems with booting and bios seem to happen.

---

### Post by kurt18947 on 2019-06-08
> **poorguy said:**
> I don't know much about HP Computers other than I know a lot of people who use HP computers and never have any problems with them until they try to dual boot Windows 10 and Linux then the problems with booting and bios seem to happen.

I guess that's because if HP's BIOS finds that certain file, it's going to boot from that file come hell or high water. The trick I read about let the machine boot using that file name but the file contents were GRUB now Windows. At least that's how I understand it. I've used this to boot multiple OSs but haven't tried it on a machine with UEFI. The old version did work on a machine with UEFI set to compatibility mode. I may experiment with it using native UEFI.

[URL="https://www.terabyteunlimited.com/bootit-collection.htm"]https://www.terabyteunlimited.com/bootit-collection.htm

  	 	 	 	   [/URL][SIZE=3][FONT=Calibri, sans-serif]Do note that BootIt UEFI only works with 64 bit UEFI so wouldn't work on devices that use 32 bit UEFI
[/FONT]
 [/SIZE]
[SIZE=3]  [/SIZE][]("https://www.terabyteunlimited.com/bootit-collection.htm")[SIZE=3][URL="https://www.terabyteunlimited.com/bootit-collection.htm"]


[/URL][/SIZE]

---

### Post by poorguy on 2019-06-08
I'm going to have to read up about UEFI / EFI and learn some about it.

I'm also going to see what I can learn about HP bios settings / bios configuration. 

UEFI / EFI is all new to me.

---

### Post by VMC on 2019-06-08
If you plan to use only Ubuntu, then efi is a non issue. The problem is when you mix and match various OS's does efi raise up from the dead.

---

### Post by poorguy on 2019-06-08
> **VMC said:**
> If you plan to use only Ubuntu, then efi is a non issue. The problem is when you mix and match various OS's does efi raise up from the dead.

Only using Ubuntu 18.04 and have nothing against Windows 10 just no need for it.

---

### Post by VMC on 2019-06-08
Actually efi will boot your linux ***and*** Windows without issue. Its the other linux/BSD that can cause issue. Are you using Secure Boot?

---

### Post by poorguy on 2019-06-08
> **VMC said:**
> Actually efi will boot your linux ***and*** Windows without issue. Its the other linux/BSD that can cause issue. Are you using Secure Boot?

I believe I'm using UEFI although uncertain how to tell as what I did was just entered factory defaults in bios and it mentioned UEFI and during install it said to install 3rd party software to disable UEFI.

My apologies for not knowing although I did mention my first UEFI install.

---

### Post by oldfred on 2019-06-09
If you have gpt partitioning & and ESP - efi system partition which is FAT32 then it is UEFI.
If you have MBR with 4 primary partition limit and extended partition then it is BIOS.
Also:
       Check UEFI boot mode
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy 

Many with older HP had UEFI boot issues and work arounds required. Many newer threads with users with HP have said UEFI updates have made it work with Ubuntu better. Not sure what models or versions.
Work arounds listed in link in my signature.

---

### Post by poorguy on 2019-06-09
Hey oldfred,


I ran the command **[ -d /sys/firmware/efi ] && echo EFI || echo Legacy **and my output says[B] EFI.
[/B]I also checked my partitions in gparted and it also shows to be **[EFI System Partition]  [fat32]  [/ boot / efi].**

Hey I learned something new.


Thanks

---

