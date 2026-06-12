---
title: "bios vs efi setup"
date: 2022-08-28
forum: Ubuntu, Linux and OS Chat
---

### Post by coley9225 on 2022-08-28
Hello everyone.
I recently acquired a rather old dell desktop, probably 2012 or so. It is bios only, as far as I can tell. The only mention of "efi" in the bios, that I can find, is the option to boot into an efi shell. My question is, is there any reason not to use  a bios only computer. I understand some of the limitations, like only 4 primary partitions, but is there any major issue with running this system.

Without booting it, I'll work from memory here. The specs are:
64 bit
Intel processor running 3.4 GHZ, 4 core, 8 thread
8GB of ddr3 memory
integrated intel graphics(I believe it said hd 4000)
descrete graphics card, gforce with 1 GB onboard ram
1 sata3 and 3 sata2 connections

So, again, I'm curious as to whether I I am going to run into any issues with this. I installed lubuntu 20.04 and fully updated, then did a release upgrade, all went well as near as I can tell.
This is a temporary setup, as I plan to but a MUCH newer system, I just have to work it into the budget.

Sorry if this isn't the proper place for this, if not, please move to appropriate sub-forum.
Thanks in advance.

---

### Post by grahammechanical on 2022-08-28
> I understand some of the limitations, like only 4 primary partitions,

The limitation of four primary partitions has less to do with having a motherboard that has a BIOS and not a UEFI settings utility. It has a lot to do with the partition table. A drive that has an MBR partition table will only allow four primary partitions. But there is a work around. A drive that has a GUID partition table (GPT) will allow a lot more primary partitions.

I have used a BIOS motherboard having one drive with MBR partition table and a second drive with GPT partition table. Both systems worked fine. The GPT partition table is more convenient when installing multiple operating systems. 

From the age and specification of your machine I would be surprised that it did not have a UEFI motherboard. I would also be surprised if the drive did not have a GPT partition table. When you installed Ubuntu did you before hand run GParted and set a new partition table? Did you then select MBR? Or, did you select Erase and Install and let the installer do all the work?

The Disks utility will tell you what partition table the drive is using. It will also show whether you have a BIOS boot partition or an EFI system partition.

The important thing to remember about UEFI motherboards is that we can install operating systems in either BIOS/Legacy mode or UFI mode. If we load the Ubuntu live session in BIOS/Legacy mode then Ubuntu is installed in BIOS/Legacy mode. If we run the live session in UEFI mode we get Ubuntu installed in UEFI mode and the Grub boot menu will give us an option to open the UEFI settings utility. Each operating system has to be installed in the same mode. We cannot mix and match.

Regards

---

### Post by TheFu on 2022-08-28
> **coley9225 said:**
> Hello everyone.
I recently acquired a rather old dell desktop, probably 2012 or so. It is bios only, as far as I can tell. The only mention of "efi" in the bios, that I can find, is the option to boot into an efi shell. My question is, is there any reason not to use  a bios only computer. I understand some of the limitations, like only 4 primary partitions, but is there any major issue with running this system.
The Linux foundation recommends using UEFI and SecureBoot when available to have the most secure Linux workstation. There are a number of reasons, which you can research.
With that said, only 1 of my computers, a laptop, is using UEFI boot.  My other systems were OS upgrades (or disk moves) and I never bothered to switch to UEFI, mainly because I understand BIOS and it works, without new issues.  I have 2 Ryzen desktop systems. Both support UEFI booting. I don't use it.  I also run a number of virtual machines. For fun, I forced UEFI boot in one of them, but all the others still use SeaBIOS to boot.

UEFI has ZERO, nothing, nada, to do with whether GPT partition can be used.  That was an arbitrary choice from MSFT to force people to move.  They are doing it again by requiring Win11 hardware have TPM v2 support.  I think it is a deal between MSFT and computer vendors to force new hardware purchases. Nothing more from a "required" standpoint, though TPM can be used to aid security and has been used in business computers for 15+ yrs.  Home users never cared or bothered all this time, so how important is TPM, really?  All Chromebooks have TPM, so Google decided it was important enough for security to mandate the extra $2 for the hardware to have it.

I should probably clarify.  The UEFI + GPT mandate by MSFT was arbitrary, but still a mandate in their OSes. If they didn't make some sort of mandate and push for migration, I could see where it would be bad for support calls.  I think UEFI was more about "secureboot" needs than anything else. MSFT had/has a real issue with securely booting - to be fair so to all other OSes, so we shouldn't judge them too harshly for their attempt to fix it without making the fix optional.  Ubuntu and all other Linuxes have the same issue.  But for real boot security, there are about 5 things that all need to be setup in specific ways to actually be secure. Miss one of those things and there's a tiny crack open.  Also, the "evil maid attack" - you can read about that - can defeat many of these security aspects, unless the computer is never, ever, out of our physical control.  When I'm staying in a hotel, I always boot from a flash device that never leaves my person. That, along with the 5 other things, including encryption of all storage in the laptop, is the only way I know to be safe when traveling.

The downside for UEFI/BIOS booting is that we need to use the same for all OSes installed on the box to drastically remove complications and have 1 clear boot method. Since the /boot/efi/ FAT32 partition is shared by all OSes that boot using EFI, if you intend to dual boot with Windows, a good case could be made for UEFI booting Linux.  Also, if the hardware vendor didn't 100% follow the UEFI standards, booting under Linux might require renaming some specific files in the /boot/efi/ubuntu/ directory (don't quote me on the name I don't really remember).  Only of my older laptops had this issue. Basically, the vendor expected only MSFT OSes to be installed and only implemented the UEFI boot standards sufficiently to support MSFT OSes, screwing every other OS ... but the workaround was to rename/copy the UEFI boot files. That doesn't always work, but really should.

Anyway, we should always be using GPT partition tables since around 2014. There are many improvements.  Linux doesn't care if [GPT and BIOS] or [GPT and UEFI]. Those are completely separate issues.


> **coley9225 said:**
> 
Without booting it, I'll work from memory here. The specs are:
64 bit
Intel processor running 3.4 GHZ, 4 core, 8 thread
8GB of ddr3 memory
integrated intel graphics(I believe it said hd 4000)
descrete graphics card, gforce with 1 GB onboard ram
1 sata3 and 3 sata2 connections


Don't memorize this stuff and guess.  Facts are more important.  **inxi -Fxz** will provide facts.  I don't really think it matters too much, provided the specific CPU is really 64-bit and the GPU model+revision is known.  Just run the command.

So, again, I'm curious as to whether I I am going to run into any issues with this. I installed lubuntu 20.04 and fully updated, then did a release upgrade, all went well as near as I can tell.
This is a temporary setup, as I plan to but a MUCH newer system, I just have to work it into the budget.

Sorry if this isn't the proper place for this, if not, please move to appropriate sub-forum.
Thanks in advance.[/QUOTE]

Ubuntu Chat is for open ended questions, so if you aren't seeking specific commands, I think it fit here perfect.

BIOS or UEFI?  Your choice. If the BIOS mentions EFI anywhere, then assume it has full support, perhaps with some other-OS EFI stuff missing. I don't think that's been much of an issue since 2015-ish.
GPT or MBR partitioning?  Your choice, but there are many, many, reasons to use GPT, always. It is safer.


And if you aren't planning to dual/tri/quad boot, then you can still run other OSes inside a VM under Linux and use either UEFI or BIOS to boot those other OSes. Your choice.

---

### Post by oldfred on 2022-08-28
Vendors still call UEFI boot as BIOS.
It was about 2011 when vendors started converting hardware to UEFI boot as in 2012 Microsoft required all Windows 8 systems to be UEFI with gpt partitioning.

I started using gpt in 2010 on my old desktop & later converted 2006 Dell laptop to gpt. Both were BIOS only. But to use gpt with BIOS, I had to have a tiny 1MB unformatted partition with bios_grub flag. A few systems did not like gpt partitioning back then. And some required a boot flag, even though grub does not use a boot flag.

Windows requires MBR for BIOS boot, so now only reason to have MBR(msdos) is if booting Windows in BIOS mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by coley9225 on 2022-08-28
Thanks for the info. Per the requessted info:

```
coley:$ inxi -FxzSystem:
  Kernel: 5.15.0-46-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: MSI model: B75MA-E33 (MS-7808) v: 1.0
    serial: <superuser required> BIOS: American Megatrends v: 1.4
    date: 01/21/2013
CPU:
  Info: quad core model: Intel Core i7-3770 bits: 64 type: MT MCP
    arch: Ivy Bridge rev: 9 cache: L1: 256 KiB L2: 1024 KiB L3: 8 MiB
  Speed (MHz): avg: 1596 high: 1597 min/max: 1600/3900 cores: 1: 1596
    2: 1596 3: 1596 4: 1597 5: 1597 6: 1596 7: 1597 8: 1597 bogomips: 54273
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel IvyBridge GT2 [HD Graphics 4000]
    vendor: Micro-Star MSI Xeon E3-1200 v2/3rd Gen Core processor driver: i915
    v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GF119 [GeForce GT 610] vendor: Gigabyte driver: nouveau
    v: kernel bus-ID: 01:00.0
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: nouveau resolution: 1920x1080~60Hz
  OpenGL: renderer: NVD9 v: 4.3 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio
    vendor: Micro-Star MSI driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: NVIDIA GF119 HDMI Audio vendor: Gigabyte driver: snd_hda_intel
    v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Micro-Star MSI driver: r8169 v: kernel port: d000 bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 465.76 GiB used: 17.11 GiB (3.7%)
  ID-1: /dev/sda vendor: Seagate model: ST500DM002-1BD142 size: 465.76 GiB
Partition:
  ID-1: / size: 457.38 GiB used: 17.11 GiB (3.7%) fs: ext4 dev: /dev/sda1
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: nouveau temp: 46.0 C
  Fan Speeds (RPM): N/A gpu: nouveau fan: 0
Info:
  Processes: 209 Uptime: 48m Memory: 7.45 GiB used: 850.1 MiB (11.1%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 2331 Shell: Bash
  v: 5.1.16 inxi: 3.3.13



```

When I installed lubuntu, it apparently used mbr partitioning.(I checked in gparted, and indicated msdos partitioning) I was unaware I could use gpt with bios, thus allowing for more than 4 partitions, thats good news. The current hdd is 500 GB, 1 partition. I'm going to resize that and covert to a separate /home partition.

Is there a way to backup my current setup, convert this hdd to gpt, then restore to the gpt drive, or will I have to do a reinstall. Also, can I add a second hdd and use gpt on that. I have another 500GB and a 1TB hdd available, for additional installs and data.

Anyway, the os hdd is on the sata3 connection, and very fast compared to my much newer laptop, so may just run this for a while. Thanks for the help and info.

---

### Post by oldfred on 2022-08-28
First thing Google said:
> MSI B75MA-E33 LGA 1155 Intel B75 HDMI SATA 6Gb/s USB 3.0 Micro ATX Intel Motherboard with UEFI BIOS


So UEFI system.
You may want to check if any UEFI/BIOS updates are available. Usually older systems stop having updates, but if you never updated, it needs those updates.

You can make sure your normal backups are up to date, and then convert to gpt. Then restore from backup.
Normally conversion to gpt erases drive. You can use gdisk to convert, but since UUIDs all change, that really only works if data only drives. 
Gparted still defaults to MBR, unless drive over 2TB. 
Ubuntu installer will even install in UEFI boot mode to MBR drives, and probably should not.

You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

If you still want BIOS boot, I might add both an ESP & bios_grub partition. I did that for many years when UEFI first started, but I still had BIOS systems, so I could easily convert a drive to UEFI boot. Only real difference is version of grub. Grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot.

---

### Post by sudodus on 2022-08-28
If your system is fairly new, and you can remember what you installed and tweaked, it is probably faster to make a fresh installation. Otherwise there are many ways to backup your system for example using rsync or tar (in both cases with elevated permissions to 'see' all files and to preserve ownership and permissions).

Maybe a good way is to keep your current system as the backup, create a fresh installation in the other drives, and after installation copy the files you want from the old drive to the correct location in the new drive.

---

### Post by coley9225 on 2022-08-28
I think, at this point, it is a new install-only a few apps installed, so I'll try a new install and use the "do something else" option, try for uefi, and see what happens. I'll update when I do. 
Thanks

---

### Post by TheFu on 2022-08-28
> **coley9225 said:**
> I think, at this point, it is a new install-only a few apps installed, so I'll try a new install and use the "do something else" option, try for uefi, and see what happens. I'll update when I do. 
Thanks

The BIOS controls whether UEFI is booted or not.  You need to ensure the BIOS is set to use (and only use) UEFI booting, if that is your intent.  The choice isn't in the Linux installer.

You can use **apt-mark showmanual** to get a subset of APT installed packages.  This list isn't perfect, since every package in the system after the installer finishes isn't marked "automatic", but it is handy to have that list in a text file for reinstalls later. My backup scripts create that list nightly to be included in the critical backup files.

Also, MBR/MSDOS has a 4 PRIMARY partition limit, but that doesn't really matter to Linux, since Logical Partitions have been supported for over 2 decades.  128 Logical partitions are allowed on any disk - it just becomes a disk space and management/maintenance issue.  Since all Logical Partitions must fit inside a single "EXTENDED PARTITION" which is 1 of the 4 allowed PRIMARY PARTITIONS under MSDOS partition tables, the management of the different partitions with Primary/Extended/Logical as used in MSDOS partitioning, can become ugly.   GPT supports 128 (or more? - don't quote me, but it is at least 120) primary partitions.

The Ubuntu Installers each have their quirks.  The installer team makes choices for simplicity very often, so they have kept MBR/MSDOS partitioning longer than needed and when we let them use the whole drive, some of those installers will wipe whatever partitioning we've already setup and force MBR.  I remember crying tears of joy in 20.04 when my GPT partition table in a fresh install didn't get wiped and replaced with an MBR table.  That was for 1 flavor, sorry, I don't remember which.  The last few years, I've been starting the installer, then switching to a different TTY, pulling over a script template for the partitioning, formatting and volume management I want, setting up the disk(s) how I desire there, then toggling back to the Ubuntu installer, choosing "Do something else" and manually connecting the storage layout to the mount locations I want.  I was tired of having no easy way to get storage setup the way I wanted and the disk-setup in the installer is atrocious.  Way too much point-n-click when a few lines in a script handles it much more efficiently.  YMMV.

---

### Post by zebra2 on 2022-08-29
I would use 22.04. Even in bios mode you will need a 8 Meg bios boot partition and a 256 Meg EFI boot partition or 22.04 will fail install.  I personally use Ext4 file system.with a separate /Home.  I have yet to install a UEFI on any of my computers including my primary system with 22.10.  Also with this scheme you can still have a /SWAP partition and avoid the new swap file setup. I also have my 22.04 system dual booting Windows 10 on a NTFS partition.  You can setup all of this yourself with the Setup disk by choosing "Other"  on the install choice menu.

---

### Post by kevdog on 2022-08-31
Totally irrelevant to this thread but I've switched between a MBR and GPT partition setup without having to reinstall -- only reason was to see if I could, other than that, not too much purpose.  For the purpose of the OP, I wouldn't overthink things too much. Your system is old, which is OK but how many partitions do you really need -- I'm guessing 1-2 or 3 at most.  Any setup will work in your case.

---

