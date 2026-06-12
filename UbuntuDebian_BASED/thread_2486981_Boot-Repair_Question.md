---
title: "Boot-Repair Question"
date: 2023-05-18
forum: Ubuntu/Debian BASED
---

### Post by arius88 on 2023-05-18
The short version:

My computer crashed mid-update and now it won't boot. I want to use boot-repair to try to fix it so I can decrypt and recover my data, but there's no option to boot from a USB in the boot menu (I tried inserting a bootable USB stick anyway just to be sure; it didn't work). It WILL boot from a DVD, however the Boot-Repair documentation ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) specifically warns against burning it on a DVD if my boot is in EFI mode.

1. Why on earth won't my machine boot from USB when it has perfectly good USB ports? (There's literally an option for "floppy group" but not USB.)
2. How do I determine if my computer is in EFI mode?
3. WHY can't I use a boot-repair DVD if it IS in EFI mode? 
4. Are there any alternatives to boot-repair that I can burn on a DVD that will work? (I have a disk with GParted on it right now but couldn't figure out how to use that to fix anything. There was an option to recover data or something but when I tried to use it the machine spent about 12 hour scanning for hard drives or something like that and never found one.) 


The longer version:

I'm running an old HP computer with Pop!_OS 22.04 on it. The other day I realized that I hadn't thought to update the system in a while. (Most distros prompt you to do this, but not Pop_OS, so I just forgot for a few months.) I ran a rather lengthy upgrade and at a certain point in the process it informed me that it needed to reboot to complete the upgrade. 

Here's the thing: I haven't been able to install a distro that will reliably power down this HP computer, and Pop_OS consistently will not power down. If I tell it to shutdown, it just runs a bit of code, the screen turns grey, and the computer continues running fans and making painful sounds for forever but never actually shuts off. Ever since I installed Pop!_OS several months or maybe a year ago, I've had to hold down the power button every night to turn the machine off. (I'm not looking to fix this problem, I have a better PC up and running now and the HP computer is going in the garbage once I've recovered my data.) So sure enough, when the machine tried to reboot, it got stuck at the grey screen of doom and I had to manually power it down. When I powered it back up, it was all messed up and giving me errors like:

```


Mounting root file system...
Bus Error
Bus Error
cryptsetup: Waiting for encrypted source device UUID=somelonglistofnumbers
mdadm: No devices listed in conf file were found

ALERT! encrypted source device UUID=somelonglistofnumbers does not exist, can't unlock cryptswap.
Check cryptopts=source= bootarg: cat /proc/cmdline or missing modules, devices: cat /proc/modules; ls /dev
Dropping to a shell

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter `help' for list of built-in commands.

(initramfs) _ 


```

There's a blinking cursor, but when I type `help,' or anything else for that matter, nothing happens; it does not appear to accept keyboard input.

I was hoping I could just use boot-repair, but my USB copy won't work and I have no idea if I can use a DVD or not since I don't know if my machine is in EFI mode; I have no idea what to do if I can't use boot-repair.

---

### Post by MAFoElffen on 2023-05-18
I need to say that since this is not Ubuntu, that this might be moved to another section by the Moderators.

I am assuming you didn't do a backup recently... 

Let's see, Pop-OS (based on Ubuntu). Old HP PC (Which Model?), that is EFI, but suspected (by you) that it does not support booting from USB (EFI boot and no USB boot? That would be odd.) 

Boot from DVD... Ubuntu Desktop installer. That may take up to 30 minutes and may time out... If it does boot, use "try" option and open a terminal session.

This is where I shared with the others in the boot-info / boot-repair team how I mount LUKS encrypted systems, to reinstall grub: [https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645](https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645)

---

### Post by yancek on 2023-05-18
> cryptsetup: Waiting for encrypted source device UUID=somelonglistofnumbers

The 'longlistofnumbers' is the UUID.  Each partition on your devices has a UUID from 4-32 characters, depending upon the filesystem type.  If you know which partition contained your root filesystem (sda, sdb, etc.) you can compare it to the output in the error you receive and they will not likely be the same.  I don't know what happened which might have changed your UUID?  When you get the correct UUID with blkid, compare it to the UUID in the grub.cfg menu for PopOS.

Have you ever used a USB to boot a system on it previously?  Have you tried different USB ports? I guess this won't work if you have no option to boot from USB.  How old is this hardware?

---

### Post by arius88 on 2023-05-18
Thanks for the response! I guess I was thinking of this as a general boot-repair/computer issue, and not specifically a POP_OS! issue.
The HP is a Pavilion. I have no idea if it is EFI or not. It's a bit of a Frankenstein computer with some electrical issues. 

I have things to do this afternoon, but later I will try running a Ubuntu installer and check out that link you shared. 
(I may need help making sense of the instructions if you're around and don't mind.)

---

### Post by MAFoElffen on 2023-05-18
First thing to do is to post the results of these two commands, that you can run from a Live Session:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmidecode -t 0,1,4

```

---

### Post by arius88 on 2023-05-18
> **yancek said:**
> The 'longlistofnumbers' is the UUID.  Each partition on your devices has a UUID from 4-32 characters, depending upon the filesystem type.  If you know which partition contained your root filesystem (sda, sdb, etc.) you can compare it to the output in the error you receive and they will not likely be the same.  I don't know what happened which might have changed your UUID?  When you get the correct UUID with blkid, compare it to the UUID in the grub.cfg menu for PopOS.

Have you ever used a USB to boot a system on it previously?  Have you tried different USB ports? I guess this won't work if you have no option to boot from USB.  How old is this hardware?

The relevant partition is sda. I don't know how to compare the partition to the output in the error, use blkid, or view grub.cfg. 

I used a USB stick to install Pop_OS! in the first place, but I may or may not have done that from within a working OS.
I did try different USB ports. 
I have no idea how old the hardware is. More than a decade, I would guess.

Update: i ran "sudo blkid" from a terminal within GParted. The UUIDs shown there match the ones in the error.

---

### Post by yancek on 2023-05-18
Reading through your threads, I don't know that running boot repair and posting the link to it here will be of much help.  It doesn't really seem like a boot issue so I would suggest that you first try unmounting with the command in my earlier post.

---

### Post by arius88 on 2023-05-18
> **MAFoElffen said:**
> I need to say that since this is not Ubuntu, that this might be moved to another section by the Moderators.

I am assuming you didn't do a backup recently... 

Let's see, Pop-OS (based on Ubuntu). Old HP PC (Which Model?), that is EFI, but suspected (by you) that it does not support booting from USB (EFI boot and no USB boot? That would be odd.) 

Boot from DVD... Ubuntu Desktop installer. That may take up to 30 minutes and may time out... If it does boot, use "try" option and open a terminal session.

This is where I shared with the others in the boot-info / boot-repair team how I mount LUKS encrypted systems, to reinstall grub: [https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645](https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645)

Downloading a ubuntu installer now. But in the meantime I wanted to see what i could achieve from the GParted Live DVD command line. 

Ran blkid, then, as per [https://ubuntuforums.org/showthread.php?t=2470405&page=8&p=14081645#post14081645](https://ubuntuforums.org/showthread.php?t=2470405&page=8&p=14081645#post14081645) i tried:

```

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# export DEV="/dev/sda"

root@ubuntu:~# export DM="${DEV##*/}"

```

and got: 

```

-bash: /DEV##*/: No such file or directory 

```
:/

---

### Post by arius88 on 2023-05-18
> **MAFoElffen said:**
> First thing to do is to post the results of these two commands, that you can run from a Live Session:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmidecode -t 0,1,4

```

Okay! the first command yielded
Legacy Mode  (alias CSM alias BIOS mode)

And the second command yielded a pile of data... what am I looking for?

(The computer i am trying to repair is not presently connected to the internet and I have no way of posting my results without spending probably an hour or two copying each line... perhaps I should just return later tonight when I've got the ubuntu installer burned to dvd and am using that.)

---

### Post by oldfred on 2023-05-18
Many here suggest that if a repair takes more than an hour to fix, better to just reinstall & restore from backup.
And if using LVM with encryption, you must have really good backups.  Disk errors within encryption can prevent recovery.
And forced shutdowns can cause disk errors, if system is still really running something as part of shutdown.

chroot & troubleshooting Full system encryption
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)
Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by arius88 on 2023-05-18
Good to hear from you, Fred. Thanks for the super helpful links! I believe the answer to my problem is in there somewhere. Just making a Ubuntu Desktop live DVD and then I'll give that stuff a go.

---

### Post by arius88 on 2023-05-18
I believe my machine uses Legacy BIOS. I am considering opening a terminal and trying the following: 

```



[LIST=1]
[*]Boot into a Live CD. 
[*][Check your keyboard]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess#Check_your_keyboard"). 
[*]Open a terminal. 
[*]To unlock your partition, enter the following command. Replace /dev/SYSTEM_PARTITION with your **system partition**, e.g. /dev/sda5 or /dev/nvme01n1p5. You will be prompted for your system passphrase.
[LIST]
[*]    sudo cryptsetup open --type=luks /dev/SYSTEM_PARTITION system 
[/LIST]
  
[*]Mount your system partition. Replace /dev/EFI_PARTITION with your **EFI System Partition (ESP)**, e.g. /dev/sda2 or /dev/nvme01n1p2.
[LIST]
[*]    sudo mkdir /mnt/root
    sudo mount /dev/mapper/system-root /mnt/root
    sudo mount /dev/mapper/system-boot /mnt/root/boot
    sudo mount /dev/EFI_PARTITION /mnt/root/boot/efi 
[/LIST]
  
[*]Enter something called chroot (don't worry about what it means).
[LIST]
[*]    sudo mount --bind /dev /mnt/root/dev
    sudo mount --bind /run /mnt/root/run
    sudo chroot /mnt/root
    mount --types=proc proc /proc
    mount --types=sysfs sys /sys 
[/LIST]
  
[*]Fix Grub. This might take a couple of minutes to run.
[LIST]
[*]    refreshgrub 
[/LIST]
  
[*]Enter the following command.
[LIST]
[*]    exit 
[/LIST]
  
[*]Close all open windows, and reboot your computer. 
[/LIST]



```

... as suggested here: [https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)

Question: I noticed some stuff about EFI in there. Does this mean that the person who recommended this approach is assuming I am using EFI and not Legacy BIOS? Do I need to modify the code to make it work on my Legacy BIOS system?

---

### Post by arius88 on 2023-05-18
Alternatively, I opened a terminal while trying a live version of Ubuntu 20.04 (22.04 wouldn't fit on a DVD) and entered this:

```


udisksctl unlock -b /dev/sdb5
udisksctl mount -b /dev/mapper/ubuntu--vg-root


```

...as suggested here: [https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

The first command prompted me for my password and successfully decrypted the partition (in my case, sda2) and returned "Unlocked /dev/sda2 as /dev/dm-0." Yay!
But the second command failed to mount the drive, returning an [COLOR=#ff0000]error[/COLOR]: "Error looking up object for device /dev/mapper/ubuntu--vg-root." Booooo.... :(

---

### Post by oldfred on 2023-05-18
If a BIOS install, you do not need to mount the ESP - efi system partition with a chroot. Some BIOS installs may now have an ESP as I believe the installer was adding a FAT32 partition with all installs.

Generally DVDs are not recommended anymore. Newest versions do not fit, but you can put lighter weight flavors or repair versions on DVDs.
Its just that in the past I burned many "coasters" or bad burns. Used one or two as actual coasters for several years. 
With flash drive it is reusable and can hold more data. I now even have moved on from most flash drive use, as found my external SSD is almost as fast as it was when it was an internal drive with USB3 port.

If system is so old as to be BIOS only or over 10 years old, best not to use Ubuntu. There are lighter weight flavors for old or limited systems.
I use Kubuntu which is more of a middle weight system but seems full featured.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

It was my understanding that Pop used SystemD boot not grub, so that also changes some things. 

Do not know PopOS nor LVM with encryption, nor POP os, so best to ask for help on a site supporting Pop.

---

### Post by MAFoElffen on 2023-05-19
This command
```

sudo dmidecode -t 0,1,4

```
Which you said displayed a bunch of data, was for our benefit to look at and determine what you have as hardware, and it's capabilities (in the BIOS)...

For example, it shows what Make, model of PC it is, the BIOS vendor, the BIOS version and revision, and the capabilities of the boot modes.

The previous command showed you were currenlty boot in a Legacy BIOS / CSM mode, instead of as UEFI... But the second command would have shown if the BIOS had the capability of booting as UEFI, but that the current setting was allowing it to boot as Legacy.

Do you now understand that 'that' kind of information might be useful? LOL.

When you did the other commands, you skipped over where the variable was set to a specific "storage device"...

Please run the UbuntuForums 'system-info' script... and post the URL of where it uploads to a pastebin. From the information in that report... I will come up with commands for you to unlock and mount your PC.

---

