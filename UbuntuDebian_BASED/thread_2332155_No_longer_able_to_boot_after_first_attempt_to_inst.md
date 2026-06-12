---
title: "No longer able to boot after first attempt to install SSD and use for OS"
date: 2016-07-28
forum: Ubuntu/Debian BASED
---

### Post by hfnieddu on 2016-07-28
I am lost in a sea of advice about how to correct boot problems, but none of the advice seems to address my specific issues. I am no longer able to boot my machine, or access it any way other than my BIOS, EFI, or a live USB in trial mode (non-persistent). I fear I have sinned heavily against the partition and boot gods. This is my first post on any forum. What is my penance? I am willing to basically start from scratch via the easiest route to get my machine up and running and again without having to buy new hardware. Please help! Boot-repair info reports before and after running repairs are linked at the bottom of the post. Thanks!

A. Symptoms 
B. Theories
C. Background story
D. Supporting material: lshw, fdisk, file, boot-repair reports before and after, system description

A. Symptoms: When I power up my machine I see the bios logo page and then a screen that says: EFI Shell Version 2.31 , current running mode 1.1.2......Device Mapping Table....Shell>
Alternatively, when I power up my machine and see BIOS logo, **and hit F11**, I get a prompt that says "select boot device." Neither my HDD or SSD is listed at this point (both non-UEFI somehow? I set my boot setting for UEFI only in BIOS because I assumed my live USB install was UEFI). Previously, when I tried to boot, I was getting the message, "...Please insert boot media..." Before I tried to swap drives my machine was working fine.

B. Theories:1. There is some incompatibility going on between BIOS/MBR and UEFI/GPT (At some point in my troubleshooting I used boot-repair, but I didn't know how to specify I had an EFI installation). 2. My partitions are all wrong. 3. Something in the CPU is totally confused because it was configured to look at the original /dev/sda (EFI cpuconfig?). 4. Something else really easy that I don't see because I'm frazzled from overthinking.

C. Background: I built my first machine a few weeks back (description below). I installed Zorin OS 9 on a WD Red HDD. I thought better of that later. My machine was working fine though for a number of weeks. I see SSDs are on sale on Amazon Prime day, so I decide to buy one, make it my primary drive and save the Red for backup. I attempt to install Zorin OS 9 from my live USB, and that is when my problems started. I attempted to create partitions on the SSD based on research, but the SSD was never found as a boot device. I proceed to try a bunch of other things. I tried completely overwriting the Red HD. I tried re-ordering the boot order and setting in my bios. At this point I'm just going to walk away and drink a beer.

D. Supporting Materials 
**lshw:** [http://pastebin.com/t0yzw223](http://pastebin.com/t0yzw223) 

f**disk:** [http://pastebin.com/kRGXsskf](http://pastebin.com/kRGXsskf) 
[B]
boot-repair reports before and after requesting a boot-repair repair[/B] (without specifying UEFI) 

**Before:** [http://paste2.org/1FNhYe36](http://paste2.org/1FNhYe36)
**After:** [http://paste2.org/yfwMAA5z](http://paste2.org/yfwMAA5z)

system description:

MSI H97 Motherboard
Intel I-7 Chip
16 GB Memory
1 x 1TB WD Red
1 x 250 GD SSD
OS is Zorin 9

---

### Post by Bucky Ball on 2016-07-29
Welcome. [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") is your friend. Hope it helps.

Once the repair is done, please copy the link it provide for the bootinfo output it produces and post that link here. Thanks.

If the repair works, probably don't need to post the bootinfo. ;)

---

### Post by howefield on 2016-07-29
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by hfnieddu on 2016-07-29
Thanks Bucky Ball! I believe I have done boot repair. I have two boot-repair info reports posted above which live in pastebin. This link is in the bottom of the post. The first report was just informational. In the second report, I asked for the repairs to actually be made. In the hex dump you can see the error that I was receiving. If you are familiar with how to read these reports I would love for you to take a look.

---

### Post by oldfred on 2016-07-29
It looks like your 1TB drive is still sda and SSD is sdb.
I might switch those, but that may create all new problems.

If you disconnect a drive, UEFI loses all its entries in its NVRAM. 
Most on several cold reboots find the ESP - efi system partition entries & add them back to UEFI. But some require you to manually add them again. Either efibootmgr or reinstall of grub using Boot-Repair.

Ubuntu's grub (not sure about others) only installs to the ESP on sda, no matter what you say during install. I have installed to my sdb and flash drives (full installs) multiple times and every time it overwrite the /EFI/ubuntu entries in ESP on sda. I quickly learned to backup ESP. Actual only difference was the 3 line grub.cfg in the ubuntu folder that is a chain entry to the full grub.cfg in your install. 

With older versions of Ubuntu and Intel, Intel boot parameters were required. My newest build with Skylake and 16.04 did not seem to need those.

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
 i915.preliminary_hw_support=1 #Skylake some versions of Ubuntu -For linux kernels older than 4.3.x, i915.preliminary_hw_support=1 must be added to your boot parameters for the driver to work on the new Intel Skylake (6th gen.) GPUs. On a fully updated system running kernel 4.3.x and up, this step is unneccesary. 

Do not use fdisk with gpt partitioned drives. In Ubuntu 16.04 is a newer version of fdisk that does work with gpt (at least to show them correctly).
Use:
sudo parted -l
sudo gdisk -l /dev/sda

Update:
did you install the latest UEFI from MSI?
Some older MSI cards, users said they had to turn off Secure Boot. Not sure with MSI, but many systems call it "Windows" or "Other".
I also turn off fast boot in UEFI, until system is fully configured. Then UEFI is slower booting so I have time to press key to get into UEFI. And any changes are recognized by UEFI. 
In fast boot mode UEFI assumes no changes and immediately turns system over to operating system. System data written onto drive for operating system is not updated, and boot is so quick that you do not have time to press a key to get into UEFI.

---

### Post by hfnieddu on 2016-07-29
Thanks oldfred! I will re-read your advice five times here when I get home and proceed. It is good to know that /dev/sda is the preferred real estate for ESP. I will use parted and gdisk. I will install the latest UEFI from MSI. I will ensure that secure boot and fast boot are turned off. Do you think I should try these steps and investigations before simply disconnecting one of my drives, or after?

---

### Post by oldfred on 2016-07-29
It also should work from HDD, so you can test before swapping drives in SATA ports.
But either way should work.

I also found skipping a SATA port or having DVD in between drives cause some issues. So be sure SSD is in SATA 0 and drive in SATA1 when you do change them around.

---

### Post by hfnieddu on 2016-07-29
Will do, I'm actually looking forward to getting home and trying it.

Attempting to follow suggestions of oldfred: a) ensure MSI UEFI is updated (couldn't do for reasons below), b) disconnect drives and reconnect HDD in order to stay focused on sda (check), c) attempt boot repair in order to reinstall grub with only one drive connected (check)

Sadly, the result was still the same. I'm hosing something up. I'm going to try a couple more sessions, and then if no joy, I will take it in to a local repair shop.

Here are the questions I generated from the steps I took below. There are a couple boot-repair reports along the way with links to pastebin.

**Questions generated from these steps:**

1. How do I know that /dev/sda1 is mounted to root "/"? I assume sda needs to be mounted there because it is labeled as "efi."
2. How do I start my machine and process from scratch, installing Ubuntu instead of Zorin?
3. When I hit, "Something Else," option during install, why were none of the partitions created by boot-repair showing mount points?
4. What do the lines 744-800 mean in my boot-repair reports?

**Steps I took 7/29/2016**

1. Confirmed Fastboot was disabled in MSI UEFI BIOS, in windows section. Could not find SecureBoot option in MSI UEFI BIOS (found it later as an advanced
setting in boot-repair). Changed option to "Legacy + UIEFI"
2. Update UEFI from MSI - Does not appear MSI has a Linux version for PC Mate H97 motherboard. I downloaded BIOS update, which was in .zip form. Could not install and saw no install file.
Then went into current BIOS to see if there was an update option. Did not see any native update option.
3. Executed "sudo gdisk -l /dev/sda." Output: [http://pastebin.com/UZzzzmRH](http://pastebin.com/UZzzzmRH)
4. Disconnected SSD (dev/sdb) in order to dump NVRAM and rebooted. Left SSD disconnected with all these steps. Rebooted without Zorin Live USB inserted. 
I did this because I already have downloaded Zorin OS 9 on HDD and wanted to see if it would work.
Result: "Reboot and Select Proper Boot device or Insert Boot Media in selected Boot device and press a key"
5. With SSD disconnected SSD (dev/sdb) in order to dump NVRAM and rebooted, rebooted with Live USB inserted and installed Zorin on sda. Used "Replace Zorin OS 9 with Zorin" option, hoping that default partitions would be created.
Result: "Reboot and Select Proper Boot device or Insert Boot Media in selected Boot device and press a key"
6. Rebooted again, this time entering MSI UEFI BIOS environment and manually clicking on my HDD as selected Boot device.
Result: "Reboot and Select Proper Boot device or Insert Boot Media in selected Boot device and press a key"
7. Boot-repair with only one HDD connected. Rebooted with Live USB for Zorin OS9 inserted in order to enter trial environment. Installed and ran boot-repair. Details below.
a. Installed boot-repair according to the second option at this site: 
In boot-repair GUI:
Did not understand GRUB location. ""OS to boot by default to sda2," but, default check had "Separate /boot/efi partition: sda1" Should I align these?
"GRUB options: deselected "SecureBoot"
pastebin report: [http://paste2.org/J6OH6zHw](http://paste2.org/J6OH6zHw)
8. Rebooting without Live USB. Will try to rely on previous download.
Result: "Reboot and Select Proper Boot device or Insert Boot Media in selected Boot device and press a key"
9. Rebooting with Live USB. Hopefully install can happen with previous boot-repair changes.
Installing. In install, selecting "Something Else" option. Hit Install. REceived, "no boot device selected." Now at this point, which partition should I choose for boot?
Also, none of the partition are showing a mount point. I'm going with selecting "efi," but I don't see anywhere to select "/" as the mount point.
10. Ran parted -l. Results here: [http://pastebin.com/ryNsBfp0](http://pastebin.com/ryNsBfp0) It looks like I have the right file type and I have the right flag. I still don't see a mount pount.
11. Ran mount. Results here: [http://pastebin.com/1y30g8JG](http://pastebin.com/1y30g8JG) not very useful. Not in a table format.
12. I am now considering abandoning trying to get Zorin OS 9, and try to install Ubuntu from a Live USB. It seems it will help me eliminate a variable
and help me speak the same language as all the documentation that I'm reading. 
13. Starting to investigate whether or not I need to manually mount my HDD to "/" since I don't see evidence anywhere that it is. In the pastebin report generated
by boot-repair, dev/sda1 (the efi partition) is not referenced at all in the "mount points" section.
14. Inspecting lines 744-800 of above boot-repair report. It appears that sda1 (efi) is attempting to be mounted, but I don't see further evidence. I see a lot of red text.
15. I am now going to try and make sure that NVRAM is dumped on my HDD as well by disconnecting it. I will then run boot-repair again, hopefully with NVRAM flushed.
16. Discconnected HDD too, and removed Live USB and then booted. Result: EFI Shell is presented. "map:cannot find required map name."
17. Started playing around with Shell commands in EFI. What a speghetti mess. One thing that is interesting is that it looks like GPT MBR has a GUID. I would have hoped 
that all traces of MBR were erased since I asked for a boot repair in EFI mode. Does this confuse the boot process? Anyway, interesting, but I'm not getting anywhere.
18. Rebooted with Zorin OS 9 Live USB and HDD connected.
19. Ran boot-repair with advanced options in order to deselect "SecureBoot."
pastebin report: [http://paste2.org/LdCOy4Ch](http://paste2.org/LdCOy4Ch)
20. Rebooted. and attempted to install Zorin via Live USB. Selected something else, but partition scheme looked the same.
21. Hit "back" and then asked for Zorin to replace the previous version of Zorin.
Result:"Reboot and select proper boot device, or Insert Boot media in selected boot device and press a key."
22. Stopping for the day. If I don't hear otherwise, on my next session I will be attempting to install Ubuntu instead of Zorin so that I can make sure I'm 
speaking the same language as everyone on this forum. If I need to do anything in anticipation of that, please let me know (like uninstall zorin or reformat any drives 
 or reconfigure chips and NVRAM in order to start with a clean slate from scratch.

---

### Post by oldfred on 2016-07-30
Do not mix up what partitions are, the ESP - efi system partition is just for UEFI. All installed systems put boot loaders into that partition for UEFI boot. Ubuntu then has / & swap as minimum partitions and even swap can be optional if you have lots of RAM.

Boot-Repair cannot create partitions. I normally use gparted and partition in advance.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 
    
It looks like grub2's os-prober found your Zorin entry and added it to Ubuntu's grub menu.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

Best to review steps & links in my signature for UEFI install.

---

### Post by hfnieddu on 2016-07-30
ok, thanks for sticking with me oldfred. I will regroup here and try again using your suggestions.

---

### Post by oldfred on 2016-07-30
You probably should review link in my signature. I know it is a lot, especially if you follow many of the links that have even more info.

If using two drives and multiple installs, I normally suggest smaller / (root) partitions like 25GB and large shared data partitions. Then in each install you can mount the shared data (cannot do during install though) and have all the same data in all installs. I started years ago with XP & a shared NTFS partition with Firefox & Thunderbird profiles. Now no Windows so shared data partition is ext4 formatted.

Fdisk has only just been updated to recognize gpt partitioned drives with the version in 16.04. But I have used gpt since about 10.10 in BIOS boot mode. But gpt keeps the protective MBR with one partition entry that says entire drive is gpt. That is so old tools like the old fdisk do not see disk as unpartitioned or unformatted and erase it. And the MBR can be used for BIOS boot with older systems. Windows only boots with BIOS from MBR partitioned drives.

You mount command showed /cow which is copy on write or the live installer's version. That is not showing anything from your install.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by hfnieddu on 2016-08-01
Wow, I finally did it. I have Zorin OS 9 loaded on my HDD. Thank you SO much oldfred! You gave me a ton of good resources in that last post. I used gparted according to your and your sources instructions. I then found the most explicit answer buried in the answer section of a post here: [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu). I had to figure out in the installer how to mount the ext4 device to "/" and also that I needed to check the "Format?" option. Now I'm good to go. The whole process took me roughly 10 hours. I guess I got my wish with this build: an education. Should I mark this "Solved" somehow?

Success! Thanks oldfred for the resources.

I pre-partitioned my HDD in gparted. I did:
sda1, fat32,boot flag,500MB
sda2, swap,(no flag),16GB
sda3, ext4,(no flag)

I checked my BIOS to make sure that secureboot, fastboot, and intel rapid instal were all disabled. I also set the mode to UEFI only. 

I installed from a Live USB, selecting "Something Else" in the installer. It took a while to figure out how to select the right device and assign "/" as the mount point. I assumed 
that because the file system was already ext4 I didn't need to re-select that option. Once I did, a menu dropped down to select "/" Also, I checked the "Format?" box 
for the ext4 device although I had to research it. 

The whole process took me about 10 hours to research and finally get done. Mission accomplished though. I learned a ton and I have my machine back. I think I will save adding the SSD for another day. How do I make this resolved?

---

### Post by oldfred on 2016-08-01
Glad you got it working. Two drive UEFI installs can be difficult. 
I also manually partition to make sure I have ESP on sdb, but grub only installs to ESP on sda.
And if you disconnect a drive, UEFI forgets its NVRAM boot entries. Some find them again with several cold (full power down) boots, others require use of efibootmgr to add entries.

Quick answer to how to change to [solved] is in my signature.

       Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by hfnieddu on 2016-08-01
Will do, thanks again

---

