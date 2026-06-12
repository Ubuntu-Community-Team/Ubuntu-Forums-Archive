---
title: "Guide to hibernation dual-boot Ubuntu 16.04 and Windows 7"
date: 2016-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by numessanguis on 2016-08-18
[SIZE=2]**Reason for this guide**[/SIZE]
There is a lot on hibernation around the internet, but when I tried to activate hibernate in combination with dual boot Ubuntu 16.04 and Windows 7, I noticed much was outdated or scattered all over the interwebz.
So therefore I would like to post all information I gathered in a single post, hopefully helping others.

[SIZE=2]**General information / remarks**[/SIZE]
[LIST]
[*]**Don't just follow the steps in this guide, make sure you know what you do and at your own risk (I'm writing this from memory). **
[*]Hibernation is turned off by default in policykit from Ubuntu 12.04 ([https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394))
 
[*]To enable Hibernate, you need a SWAP PARTITION (not a swap file: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)) 
[*]**Windows 8 / 10:** Probably this guide works the same for you, but you first have to disable fast boot. 
[*]Watch out with using Hibernate and switching between Windows and Ubuntu, you **risk data corruption** on your shared paritions. **Always unmount the shared partition(s) before hibernating** ([http://superuser.com/questions/211079/what-do-i-have-to-take-care-of-when-hibernating-both-ubuntu-and-windows-dual-bo](http://superuser.com/questions/211079/what-do-i-have-to-take-care-of-when-hibernating-both-ubuntu-and-windows-dual-bo)) 
[*]**Warnings of corruption:** [http://superuser.com/questions/39532/hibernating-and-booting-into-another-os-will-my-filesystems-be-corrupted](http://superuser.com/questions/39532/hibernating-and-booting-into-another-os-will-my-filesystems-be-corrupted)  
[/LIST]

**My setup**
[LIST]
[*]BIOS (not UEFI) 
[*]SSD NTFS with Windows 7 (first in boot order) 
[*]SSD ext4 with Ubuntu 16.04 
[*]HDD NTFS for data 
[*]RAM: 16GB 
[/LIST]
 
 **SWAP PARTITION**
If you already have a swap partition with at least the size of your RAM (if you want to be on the safe side, use a swap partition of double the size of your RAM), you can skip the swap partition step and go to HIBERNATE step.
To check whether you have a swap partition (shows nothing if you don't have it, else the following):
```
$ sudo swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sdb2 partition  17G   0B   -1
```

Or to also check your RAM size (total is 0 if you don't have a swap partition active):
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        2,3G         12G        143M        1,1G         12G
Swap:           16G          0B         16G
```

**gparted**
If you don't have a swap partition yet, we're going to make one now using `gparted`.
If you have unallocated disk space on your HDD / SSD, I think you can just use `gparted` while running Ubuntu. It doesn't come standard with your Ubuntu installation, so use:
```
sudo apt install gparted
```

If you don't have any unallocated space left (which is likely the case), we have to resize your Ubuntu partition first (or some other partition, but that's outside the scope of this guide).
You cannot resize a partition while it is in use, so you need to make a LiveUSB (or CD) first.
Download your Ubuntu distribution and follow this guide: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)


[LIST=1]
[*]Restart your computer and boot from the USB stick and select `Try Ubuntu without installing`. 
[*]Select `Search your computer` and type: `GParted Partition Editor` (which is standard included in the LiveUSB) 
[*]Select your drive with Ubuntu on it in the right-top corner (in my case: `/dev/sdb`) 
[*]Right-click your partition with Ubuntu and select `Resize/Move` (in my case `/dev/sdb1` with File System `ext4`) 
[*]Change the `Free space following (MiB)` from `0` to a minimum of your RAM size and if you want to be on the safe side, double of your RAM size. (not preceding, because then you probably corrupt your
[LIST]
[*]To see your RAM in MiB (see `Mem`) (other commands: [http://www.cyberciti.biz/faq/ram-size-linux/]("http://www.cyberciti.biz/faq/ram-size-linux/%29:")  )```
free -m
``` 
[*]To calculate between GB, GiB and MiB: [http://www.dr-lex.be/info-stuff/bytecalc.html](http://www.dr-lex.be/info-stuff/bytecalc.html) 
[*]I have 15998 MiB, so I made my swap partition 17 GiB (17407 MiB) 
[/LIST]
  
[*]Right-click your now unallocated space and select `New` 
[*]Leave the default options, except change File system from `ext4` --> `linux-swap` 
[*]Press the checkmark icon &#10003; to apply all changes when you're sure. 
[*]Shutdown your computer, remove your USB and reboot into Ubuntu. 
[*]Congratulations, you made a swap partition! but it's not activated yet :p 
[/LIST]

**Get UUID of swap partition**
Based on: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

To get a nice overview of your HDD/SSD and partitions:
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

but to get the actual swap partition, run:
```
sudo fdisk -l
```
and find something that looks similar to:
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048 464465919 464463872 221,5G 83 Linux
/dev/sdb2       464465920 500117503  35651584    17G 82 Linux swap / Solaris
```

Referring to your device based on where it is mounted is not really robust and can change if you for example plug in a USB stick. Therefore we need the UUID of our swap partition (in this case `/dev/sdb2`, but change XY to your own):
```
sudo blkid /dev/sdXY
/dev/sdb2: UUID="735b3be3-779c-4d21-a944-b033225f3ab4" TYPE="swap" PARTUUID="352a5b25-02"
```

We need this UUID for later so notate this somewhere: UUID=735b3be3-779c-4d21-a944-b033225f3ab4 (but with your own UUID).

**Activate swap partition**
[LIST=1]
[*]Make a backup of your fstab file:
[LIST]
[*]```
sudo cp /etc/fstab /etc/fstab.bak
``` 
[/LIST]
  
[*]Edit your `fstab` file to include the UUID of your swap partition:
[LIST=1]
[*]```
sudo nano /etc/fstab
``` 
[*]Add the following line (with `xxx` being your UUID): ```
UUID=xxx none            swap    sw                0       0
``` 
[*]Save the file and exit (ctrl+x --> y --> enter) 
[/LIST]
  
[*]Reboot your computer 
[*]Check if swap partition still exist with:
[LIST]
[*]```
$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sdb2                               partition    17825788    0    -1
``` 
[/LIST]
      
[/LIST]

Edit grub so your swap partition can be used at resume


[LIST=1]
[*]Backup your `grub` file
[LIST]
[*]```
sudo cp /etc/default/grub /etc/default/grub.bak
``` 
[/LIST]
  
[*]Edit your grub file:
[LIST=1]
[*]```
sudo nano /etc/default/grub
``` 
[*]Edit the line `GRUB_CMDLINE_LINUX=""` (with xxx being your own UUID) --> ```
GRUB_CMDLINE_LINUX="resume=UUID=xxx"
``` 
[*]Save the file and exit (ctrl+x --> y --> enter) 
[/LIST]
  
[*]```
sudo update-grub
``` 
[*]Create a resume file an add your UUID with the following commands:
[LIST=1]
[*]```
sudo nano /etc/initramfs-tools/conf.d/resume
``` 
[*]resume=UUID=xxx 
[*]Save the file and exit (ctrl+x --> y --> enter) 
[/LIST]
  
[*]```
sudo update-initramfs -u
``` 
[*]Reboot! 
[/LIST]


**HIBERNATE in start menu**
Based on: [http://askubuntu.com/a/487282](http://askubuntu.com/a/487282)

First we try if hibernate works, otherwise you either missed something above, my guide is incomplete or your computer needs something specific. Try hibernate with the following code:
```
sudo pm-hibernate
```
In my case my computer starts with: `Resuming hibernate` and then boots into W7...
but if I restart my computer again, press in my BIOS boot options and select my SSD with Ubuntu, Grub starts, I select Ubuntu and it indeed resumes :)

To add hibernate as option to the start menu we first have to create the file: `com.ubuntu.enable-hibernate.pkla` and then add the hibernate information
[LIST=1]
[*]```
sudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
``` 
[*]Paste the following in it: ```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=yes
``` 
[*]Save the file 
[*]Reboot and you have your hibernate option! 
[/LIST]

**Problem**
After the first hibernation I get a resume hibernation and always have to boot to Windows 7. After that I can restart and choose W7 or Ubuntu. Probably because I have my W7 SSD as first boot priority. I tried removing:
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

but to no avail. If anyone has suggestion on how to only get resume hibernation when the Ubuntu SSD is selected,
and not skip BIOS at startup, that would be a nice addition to this guide.

---

### Post by ajgreeny on 2016-08-18
*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate for the post which is not a support request.

---

### Post by numessanguis on 2016-12-11
To reduce the risk of bricking your Windows so that it won't start, you can disable auto-mount and/or write access to your drives such as your Windows drive:
[https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu](https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu)

In case you suffer data-corruption, take a look here:
[https://ubuntuforums.org/showthread.php?t=2346064](https://ubuntuforums.org/showthread.php?t=2346064)

And IMPORTANT, auto unmount drives on hibernate if your setup allows you (to prevent data-corruption):
[https://ubuntuforums.org/showthread.php?t=2346082&p=13581281#post13581281](https://ubuntuforums.org/showthread.php?t=2346082&p=13581281#post13581281)

---

