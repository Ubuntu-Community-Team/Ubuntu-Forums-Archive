---
title: "Full install to USB flash drive, UEFI Boot"
date: 2016-10-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Halbarad on 2016-10-02
This is the procedure I have used for fully installing Ubuntu to a 32GB usb flash drive **that boots in UEFI mode**. The install is done **from a fully working Ubuntu system** installed on your HDD. The method can be slightly modified so to allow installation from a live CD, but this is not dealt with in the present tutorial.  The usb drive is fully portable and boots the system on any PC that UEFI boots.
This tutorial is NOT about liveCDs, with or without persistence; you get a full installation and your flash usb drive exactly works as an internal hard disk (HDD). Live CDs with persistence have severe limitations in comparison. 
This tutorial** does not cover BIOS boot**. If you are interested in booting from BIOS, you may install one of Sudodus' ISOs (see for example [https://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506]("https://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506"))

The official installer fails to install to usb drives. Perhaps it is only a matter of time before the installer is fixed and Ubuntu can be smoothly installed to a usb flash drive but -- who knows, fixing a bug may take several years and the opportunity of walking with your system in your pocket can't wait. By the way, this is an opportunity that only Linux gives -- "Windows to go" is a completely different thing and cannot be updated, upgraded etc. Therefore, if you wish to keep your system in your pocket, you have just a few options. Either you flash Sudodus' ISOs (look for them in Ubuntu Forums, I've tried a couple of them and they worked, with some glitches that seem to me secondary) or you take all the steps by yourself following this tutorial. Or -- last but not least -- you try other distributions, such as Porteus.
I am going to divide this tutorial into several posts. It looks very long because I am trying to make all the steps explicit; people who have a basic competence with the terminal and with system maintenance will just focus on the central part of Post 3.

(1) (this one) Intro and warnings
(2) Preliminary work
(3) Procedure (directions, step by step)
(4) quick explanations about the steps in (3)
(5) Ubuntu to go? Should be easy

***Warning***: no harm should come from following these directions, **so far as they are precisely followed**. Much work has to be done as root -- because all the efi files must have a root owner, and in order to work on the mounted EFI partition you must have root privileges: precision and care are important.
***Warning***: even if you are awake and careful, your system might have peculiarities that lead to unpredictable results. This procedure always worked for me, but you never know. Before starting, you ought to make a complete backup of your system, using Clonezilla or other methods of your choice.
***Warning***: portability requires that you do not install specific (esp. proprietary) drivers. Drivers are linked to specific hardware and they work on the machines that mount that hardware. However, if you are not interested in portability, you surely can install such drivers (e.g. nVidia drivers) on your flash drive once Ubuntu is there. In this case you'd have an Ubuntu system entirely residing on your flash drive and you could even throw your internal drive away (or install other Operating Systems on it); but your install would not be portable. 
***Warning***: flash drives can be slow. I warmly recommend that a full install of the system on flash drive is done only on USB3 *fast* drives. I have tried several 32GB USB3 drives; a Cruzer Extreme is very fast: all Ubuntu flavours boot from it in less than half the time it takes to boot from my hard disk drive and all programs (including Firefox) start very quickly.
***Warning***: modern flash drives wear out much more slowly than older ones. However, the procedure has effective steps for reducing writing cycles, for limiting the use of the swap file to a minimum (or to nothing) etc. At any rate, a good amount of RAM is required in order to avoid use of the swap file. 2 GB should allow one to work without ever having to use the swap file (once a swappiness of 0 has been set: see below, directions step by step).
***Warning***: my procedure is for a UEFI boot. Therefore the flash drive will *not* boot from BIOS systems. You can have flash drives that boot both in UEFI and BIOS systems and you might modify this procedure to produce one, but I am not interested in doing so. If you wish, you can use Sudodus' ISOs for this purpose ([https://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506]("https://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")); or you can do some work and modify this procedure.

I am very grateful to Sudodus and Oldfred. I started from their work and suggestions and went on working on my own, with comparisons and trials.

---

### Post by Halbarad on 2016-10-02
Post 2: Preliminary work
0. Backup you system. Data, boot partitions, root partition, all. It's boring, all right, but you ought to backup anyway from time to time.
1. You must have a live USB of the Ubuntu flavor you want to install. This must *not* be on the same flash drive you are going to install Ubuntu on (trivially). You should use mkusb and flash the live CD with persistence. Just google "mkusb" or "ubuntu live usb" for directions about this task and about how to install mkusb.
2. I assume that gparted is installed on your system and/or on your live CD.
```
sudo apt-get update
sudo apt-get install gparted
```
3. Boot from your live cd and install boot-repair on it. Learn about boot-repair (how to use, how to install) from the web. Be ready to boot your PC from a recovery flash drive or disc in case anything should go wrong (it never happened up to now and we keep our fingers crossed...) At any rate, you must know how to restore your system from your backup using the method of your choice.
4. I assume that you are able to find out the UUIDs of HDD and usb partitions (via gparted or blkid or...) as well as the device names assigned to them (sda1, sda2, sdb1 etc.).
5. I also assume you are able to produce a text file using your editor of choice.
6. You have to know what it means to be root and you have to know how to use the terminal.
7. Set your PC boot to UEFI mode (not Legacy or Compatibility). In your Boot Order (or Priority) menu, set usb drive (or usb HD) to the first place.

---

### Post by Halbarad on 2016-10-02
Post 3: Procedure (just read Post 4 before starting if you want to know what you are doing)

***A: prepare your usb flash drive***
You can do the following either from a version of Ubuntu installed on your HDD or from your live usb (with gparted installed, see Post 2).
(1) Plug in the target drive and start gparted. Any files present in it are going to be deleted. Find out its  /dev/name (you can also use the utility "Disks" for that).
(2) Unmount all the partitions in your target drive (in case you have mounted partitions)
(3) Make a new GPT partition table on your target usb drive with gparted
(4) With gparted, make a 300 MB FAT32 partition, set the flags "boot" and "efi" (or "esp" if "efi" is not there)
(5) With gparted, make a large partition (at least 8GB, 16 is better) EXT4 and label it "root" (although the label is not necessary)
(6) With gparted, make a new 1GB swap partition
(6b) IF you want to use part of your drive for sharing data with Windows, move your partitions to the end of the flash drive (with gparted) and leave the free space for a new NTFS partition (it is better if the NTFS partition is the last to be made, just leave the free space at the beginning for the moment). Windows does not always recognize partitions in a usb drive, it may only recognize the first one (quite erratically).
(7) Shutdown. Plug your target drive off and plug in your live usb with the Ubuntu flavor you wish to install.  Switch on and wait for the live Ubuntu to boot.

***B: install Ubuntu flavor from live CD***
The following steps require that you are working from an Ubuntu OS live in your live usb drive. Double check that boot-repair is installed.
(1) Plug in your target flash drive and find out its /dev name -- it would probably be /dev/sdc if you have only one internal HDD and you have your live usb on. Let's call it /dev/sdx -- just replace the "x" with the appropriate letter.
(2) Click the button for installing the OS on your PC.
(3) Select the language etc. Decide about installation options. When you get to the drive installation window, select "Something else" -- do **not** choose to install alongside the existing system or to wipe out HDD.
(4) Select your /dev/sdx1 (the EFI partition: FAT32 300 MB; in case it is given another number, just act on that partition) and press "change"; use it as efi partition -- regrettably, the installer will still install on sda1
(5) Select your /dev/sdx2, press change, use it as EXT4 partition; mount at "/"
(6) Select your /dev/sdx3, press change, use it as swap
(7) Go on with the installation. At the end, choose to close the window but to keep using the live CD.

***C: restore your main system***
(1) Unmount any mounted partitions on your target drive, unplug it.
(2) Run boot-repair and follow its directions -- you might check, in advanced options, that it is setting your grub to boot to the correct partition in your internal HDD. As an alternative, restore your EFI partition and boot configuration in any other way you have previously chosen when you have backed up. boot-repair always worked for me and I can see no reasons why it shouldn't.
(3) Shutdown. Remove the live usb drive. Boot to your main system (the one installed on the internal HDD).

***D: Tweak the usb flash drive***
(1) You are now in your working main system. Plug in the target drive with the Ubuntu installation. Find out its partition names /dev/sdxy. Find out the UUIDs of sdx1 (EFI) sdx2 (root) and sdx3 (swap) with gparted (right click on partition and select "information") or "sudo blkid /dev/sdxy" and write them down.
(2) The root partition of your target drive should have been automatically mounted when you have plugged in the flash drive. Mount the EFI partition of the target drive:
```
sudo mkdir /mnt/efi
sudo mount /dev/sdx1 /mnt/efi
```
(3) keeping the UUID of sdx1 (EFI) and sdx2 (partition root in target drive) in a sheet of paper or in the clipboard produce the crucial text file grub.cfg ("CGC" hereafter) opening your text editor as root (e.g. sudo leafpad for a Lubuntu user, sudo gedit, etc.). You should produce a text file containing exactly the following three lines, but you have to replace the expression between "<>" with the UUID of your EFI partition in your target drive:
```
search.fs_uuid <YOUR EFI UUID in target flash drive> root hd1,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```Save as grub.cfg.
Again: use gedit or leafpad as you please, but open your editor as root and save as root (root must be the owner of the file) somewhere in your home directory.

(4) CAREFUL HERE -- the contents of your own EFI partition might differ from one install to another, so I am going to give you the files that you must have in the EFI partition of the target drive at the end of the job. You can also copy and paste the list of commands I produce below. 
Some of these files MIGHT be redundant, in efi/Boot or in efi/EFI/Boot. No harm. All of these files must be copied from a working install of Ubuntu in your HDD: you can't do this from a live usb.
Supposing that the grub.cfg you have generated in (3) is in your current directory and is called "grub.cfg", that you have already made the dirs /mnt and /mnt/efi and that your EFI partition in the flash drive is sdx1, this is the list of commands you need in order to rebuild the above structure. If you have already mounted your efi partition in the target drive on /mnt/efi, just skip over the first command in the list.
```
sudo mnt /dev/sdx1 /mnt/efi
sudo mkdir /mnt/efi/Boot
sudo mkdir /mnt/efi/ubuntu
sudo mkdir /mnt/efi/EFI
sudo mkdir /mnt/efi/EFI/Boot
sudo mkdir /mnt/efi/EFI/ubuntu
sudo mkdir /mnt/efi/EFI/ubuntu/fw
sudo cp /boot/efi/EFI/Boot/bootx64.efi /mnt/efi/Boot/
sudo cp /boot/efi/EFI/Boot/bootx64.efi.grub /mnt/efi/Boot/
sudo cp grub.cfg  /mnt/efi/Boot/
sudo cp grub.cfg  /mnt/efi/EFI/Boot/
sudo cp /boot/efi/EFI/ubuntu/grubx64.efi /mnt/efi/Boot/
sudo cp /boot/efi/EFI/ubuntu/MokManager.efi /mnt/efi/Boot/
sudo cp /boot/efi/EFI/ubuntu/shimx64.efi /mnt/efi/ubuntu/
sudo cp grub.cfg /mnt/efi/ubuntu/
sudo cp /boot/efi/EFI/Boot/bootx64.efi /mnt/efi/EFI/Boot/
sudo cp /boot/efi/EFI/Boot/bootx64.efi.grub /mnt/efi/EFI/Boot/
sudo cp /boot/efi/EFI/ubuntu/grubx64.efi /mnt/efi/EFI/Boot/
sudo cp /boot/efi/EFI/ubuntu/MokManager.efi /mnt/efi/EFI/Boot/
sudo cp /boot/efi/EFI/ubuntu/fwupx64.efi /mnt/efi/EFI/ubuntu/
sudo cp grub.cfg /mnt/efi/EFI/ubuntu/
sudo cp /boot/efi/EFI/ubuntu/grubx64.efi  /mnt/efi/EFI/ubuntu/
sudo cp /boot/efi/EFI/ubuntu/MokManager.efi /mnt/efi/EFI/ubuntu/
sudo cp /boot/efi/EFI/ubuntu/shimx64.efi /mnt/efi/EFI/ubuntu/
sudo umount /mnt/efi

```
You can make a bash file from the commands above (in this case, run it as root) or add a semicolon and a backslash at the end of each one but the last one and run it from terminal as a single very long command. Or you can copy and paste the commands one by one.

(5)  in etc/fstab of the root partition of the target flash drive, replace the  UEFI boot UUID with the UUID of sdx1 (if you've lost it, find it out with sudo blkid /dev/sdx1). You have to do this for the file etc/fstab of your flash drive's root partition, which should be mounted in /media/... and NOT for the /etc/fstab of your running system (!!)
The UUID of your root partition should already be correct in the flash drive's fstab: just check.
While you are tweaking fstab add noatime option to root partition
```
ext4  noatime,errors=remount-ro 0  1

```Check the swap file in fstab; if it lists a swapfile from your HDD (normally sda) replace that UUID with the UUID of your flash drive swap file. (That is, unless you wish to use your flash drive only in the PC you are now using, in which case it may be convenient to use the HDD swap file.)
Now you can remove journaling from the flash drive root partition (to reduce wear). From terminal write:
```
sudo tune2fs -O ^has_journal /dev/sdxy
```
Replace sdxy with the device name of your root partition in the flash drive. sdxy should normally be sdb2, unless you have more than one HDD or you have another flash drive or ext. HDD plugged in.


(6) If you want to minimize the use of swap file, change the system swappiness value: in the root partition of your target flash drive edit etc/sysctl.conf as root. Then, change or add this line to the file:
```
vm.swappiness = 0
```
(You could also change the value while your system will be running: from terminal		sysctl vm.swappiness=0)
(cat /proc/sys/vm/swappiness from terminal to find out current swappiness value *in your running OS*)
If you are low on RAM it is better to keep swappiness to 60 or 50.

After every update, your grub will also give you the option to start all the operating systems that are present in your HDD; if you are running your OS from another computer, just do not choose those options in the grub menu.

---

### Post by Halbarad on 2016-10-02
Post 4: Explanations
STRATEGY. The standard Ubuntu installer is buggy: if you try to install to usb drive it uses the boot EFI partition of your internal HDD as boot partition. Therefore it overwrites your grub configuration and "breaks your system" -- but in a way that can be easily mended. The main strategy of my procedure is: use the installer, repair the system, then tweak the usb key and do that which the installer should have done. The latter is mainly done by copying several system files to the usb drive EFI partition and adding a basic grub configuration to it.
EFI PARTITION. The EFI partition is the key partition for booting a UEFI system. It is a FAT32 partition that can be placed anywhere on the disk or drive -- it need not sit at the beginning of the disk. Its contents are some directories. When Ubuntu is running, the EFI partition from which it has been booted is mounted in /boot/efi. The naming of the directories within the EFI partition is insane. From your root directory you have e.g. /boot/efi/EFI/Boot, but also /boot/efi/Boot. You have two grub configuration files (one very short, one quite long) that perform entirely different tasks and are both called "grub.cfg". It's like a labyrinth built by a deranged programmer. Let's hope it's just "like" it. Within the EFI partition you find several directories, one for every OS installed on the disk. If you have a multiboot Windows/Linux Ubuntu you will have EFI/ubuntu and EFI/Microsoft.
If you use the standard installer to install to the usb flash drive, the EFI partition in it will be empty at the end. You actually have to create it before the installation and to fill it up after it. Luckily this is no big deal, once you know what to do.

---

### Post by Halbarad on 2016-10-02
Post 5: Ubuntu to go? (UEFI) Should be easy
Post 5 only contains some advice for going on experimenting by yourself. I've never tried it yet. Sorry, I'm too busy. But I guess it should be easy. The way for generating an "Ubuntu to go", that is a clone of your working system (on HDD) that entirely resides on usb key but is portable and UEFI bootable, is a variant on the present procedure. Instead of installing a new system, you just copy to the flash drive the contents of all the system partitions in your internal HDD. This replaces steps B and C in the post (3) above. For example, if your "internal" Ubuntu is in two partitions: "/" and "home" you just make two analogous partitions in your flash drive and copy the contents to them. No need that the target partitions have the same size as the original ones (provided that you have enough space for copying everything to them). Be careful about the owners of the files: do not copy the home dir as root. To do the copying you have to run your liveCD, so that your HDD partitions are not mounted. The contents of the EFI partition are copied as above: post 3, D. In addition to this, you have to modify your /boot/grub/menu.lst replacing the UUID of the root partition in your HDD with the UUID of the root partition in your flash drive. Also remember to tweak the /etc/fstab in the root partition of your usb drive so that it points to the copies of the Ubuntu system partitions on your usb drive. After the first boot into your flash drive clone, I guess you had better run update-grub. Remember that your grub, after every update, will also give you the option to start all the operating systems that are present in your HDD; if you will later run your OS in another computer, just remember not to choose those options.

---

### Post by ajgreeny on 2016-10-02
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate and should be a better fit.

---

### Post by PopsTheSailor on 2017-02-03
Post 3, step 4 says to set flags for both boot and efi. There is no efi flag option when you right click and select manage flags. How do you set the efi flag?

---

### Post by oldfred on 2017-02-04
With UEFI, parted/gparted is using the boot flag to assign the correct GUID for the ESP - efi system partition. 
You should not have boot flag on any other partition, only one per drive.

The ESP must be FAT32 and Windows uses 100MB, but we often suggest 300 to 500MB if larger drive for possible future use.
A few systems require a partition with a boot flag, grub does not use one for BIOS boot and boot flag for UEFI is only for the ESP/UEFI boot.

If using gdisk to assign GUID for ESP it is code ef00.
And gdisk uses code ef02 for the bios_grub flagged partition if you want BIOS boot or option for BIOS boot.

```
Model:   (scsi)
Disk /dev/sdc: 31.6GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  536MB   535MB   fat32        USB_ESP    boot, esp
 4      536MB   538MB   2097kB               bios_grub  bios_grub
 2      538MB   15.2GB  14.7GB  ext4         root
 3      15.2GB  31.6GB  16.4GB  ext4         usb_data

```

---

### Post by Halbarad on 2017-02-07
Hi, sorry for replying so late, I had some trouble with my wireless. I checked with gparted and the activated flag option is esp (in addition to boot). I seem to remember that I had an efi flag option when I wrote this stuff -- maybe my memory is deceiving me or there was some update to gparted.

By the way, I keep using my usb flash drive which is twice as fast as my hd install. Backing up the OS to another usb stick is also a no-brainer with dd.

I hope the procedure will work for you too...

---

### Post by nico-d-be on 2017-08-26
Thanks for the extended guide. I've followed it to the letter with the only changes the ones listed bellow, but have had no success; UEFI does not show the option to boot, even after disabling secure boot in the windows system on which I installed. On a Mac the stick actually does show up in the boot manager, but trying to boot it sends me to the typical "broken-grub" text interface ("Minimal BASH line editing is suported ..."). Would you have any hints on where to look for the root of this problem?

Small changes in step D(4):
[LIST]
[*]Instead of bootx64.efi.grub my internal SSD EFI partition had bootx64.efi.grb; I assumed these do the same.
[*]Instead of MokManager.efi I had mmx64.efi, not so sure about this one but still replaced each occurence of MokManager by mmx64
[/LIST]

---

### Post by oldfred on 2017-08-27
They did rename MokManager to mmx64.

Not sure about bootx64.efi.grb?
I have always just copied shimx64.efi or grubx64.efi to /EFI/Boot/bootx64.efi.
But Ubuntu's full install grub is hard coded to find more boot files in /EFI/ubuntu, so both folders required. And /EFI/ubuntu/grub.cfg that calls (configfile) the full grub.cfg in install must be there.

---

### Post by Halbarad on 2017-08-29
Hi, I think Oldfred is right (as usual...). The trouble is with the boot, so I ***guess*** that your trouble may have to do with the grub file(s). I'd point out a couple of things:
(1) A 'tutorial' like the one I have provided is nothing but a a temporary patch, which works (or at least used to work in all my tests) de facto but it is not based on a detailed understanding of the procedures followed by the Ubuntu programmers. The only thing I can say is that such procedures, as well as the file system organization, look piecemeal and a bit disorderly. Therefore it is only too likely that an update can introduce new methods in ways that are totally not perspicuous. It goes without saying that the only real fix will be there when we are able to regularly install Ubuntu to a flash drive in a direct way, i.e. via Startup Disk Creator or an equivalent tool. ***However***, so far as Ubuntu UEFI boot goes, more is more. That is, I think you can add more grub or grb files and only the required files will be used. I mean, I would try this on a broken flash drive installation.
(2) My guide is for Ubuntu 16.04 -- in my frantic attempt to describe all the least details, I idiotically forgot to mention this crucial fact.
I hope you can find a way out. As to my two flash drives with Ubuntu installations, they keep working and updating without a glitch.
In case you don't succeed, I'd advise you to try Sudodus' ISOs ([https://ubuntuforums.org/showthread.php?t=2213631]("https://ubuntuforums.org/showthread.php?t=2213631"))

---

