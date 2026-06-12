---
title: "Observations about Ubuntu 22.04 Installer"
date: 2022-07-01
forum: Ubuntu, Linux and OS Chat
---

### Post by tea for one on 2022-07-01
Having tried to help forum members with Ubuntu boot problems, I have found that some of my recent advice has been inaccurate.
Therefore I thought that I would test a Legacy/mbr installation.
I have an Intel NUC6AYH purchased in 2019, where I can enable/disable both Legacy and UEFI modes.

Having disabled UEFI mode, I booted into a live session of Ubuntu 22.04 in Legacy mode.
I opened Gparted and chose msdos as the partition table.
I then installed Ubuntu 22.04 choosing normal installation and allowed the installer to automatically create the partitions.
Here is the result:-
```
test@test-NUC6CAYH:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" 
[COLOR="#0000FF"]Legacy[/COLOR]
test@test-NUC6CAYH:~$ sudo parted -l
[sudo] password for test: 
Model: ATA C300-CTFDDAC064M (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR="#0000FF"]gpt[/COLOR]
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   64.0GB  63.5GB  ext4

test@test-NUC6CAYH:~$ 
```
The installer created 3 partitions, including an ESP.
Msdos partition table was changed to gpt without my intervention.

I then powered off the PC and accessed the UEFI Set Up.
I disabled Legacy and enabled UEFI.

The PC booted in UEFI mode without problem.
The phrase "How you boot the installation USB is how you install" is not completely accurate.

I do not know if this outcome is peculiar to my PC and I would be interested to hear other comments.

---

### Post by sudodus on 2022-07-01
I would like to ask: Is your system in the NUC bootable both in legacy mode and UEFI mode or only in UEFI mode?

So the installer Ubiquity in 22.04 LT switches from MSDOS partition table to GPT. I suppose this happens 'only' when you let the computer use the whole device?

Did you try manual partitioning? Then it should not happen.

---

### Post by Dennis N on 2022-07-01
> I do not know if this outcome is peculiar to my PC and I would be interested to hear other comments.
It's not just your PC. When you install in BIOS mode and select the "Erase and Instsall" option, You get an both an ESP and bios_grub. If your disk is manually partitioned before you start the installer, then you might be able to avoid this, but I'm not sure.

---

### Post by tea for one on 2022-07-01
> **sudodus said:**
> I would like to ask: Is your system in the NUC bootable both in legacy mode and UEFI mode or only in UEFI mode?
I can boot internal and external devices in both Legacy and /or UEFI mode - user choice.
> So the installer Ubiquity in 22.04 LT switches from MSDOS partition table to GPT. I suppose this happens 'only' when you let the computer use the whole device?
Yes, I'm sure you are right. I used the whole device and let the installer decide everything.
I was surprised to see gpt when I booted into the installed OS.
> Did you try manual partitioning? Then it should not happen.
Thanks to your prompt, I have now.
I created an msdos partition table plus one ext4 partition of 30GB ((the complete disk is 64GB) and then allowed the installer to format it.
Here it is:-
```
test@test-NUC6CAYH:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" 
[COLOR="#0000FF"]Legacy[/COLOR]
test@test-NUC6CAYH:~$ sudo parted -l
[sudo] password for test: 
Model: ATA C300-CTFDDAC064M (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR="#0000FF"]msdos[/COLOR]
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.2GB  [COLOR="#0000FF"]32.2GB[/COLOR]  primary  ext4         boot


test@test-NUC6CAYH:~$ 
```
Old school installation on one partition, although the installer did ask me to create an ESP (which I ignored) even when I had booted in Legacy mode.

---

### Post by tea for one on 2022-07-01
> **Dennis N said:**
>  When you install in BIOS mode and select the "Erase and Install" option, You get an both an ESP and bios_grub.
And GPT

---

### Post by oldfred on 2022-07-01
Was ESP mounted in fstab? 
That is my second check on which way it is really installed.

Also guilty of saying how you boot installer, it then how you install.
And pretty sure that was how it used to be.
I like to see gpt used & even the install of UEFI boot files.  I would hope that if Windows is in BIOS/MBR mode, it would not convert to gpt.
Often users do not know how they booted installer & then do not know default boot mode of installed system.

UEFI hardware really should have UEFI installs, so this may be the result of that?
I saw where a while back they allowed install of both grub-pc & grub-efi-amd64. But updates then would only update one or the other based on how booted.

Now very new systems are UEFI only or UEFI class 3.
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)
Several other vendors seem to be doing the same.

---

### Post by tea for one on 2022-07-01
> **oldfred said:**
> Was ESP mounted in fstab? 
I don't know now because my last test was Legacy with msdos partition table (only one partition).
I'll re-install and report back.
Ah, when booting in Legacy mode or UEFI mode?
> Also guilty of saying how you boot installer, it then how you install.
Yes, me too - it's all becoming a bit complicated now.
Notwithstanding the perennial problem of Ubuntu on an external drive and the installer looking for the ESP on the internal drive.

---

### Post by Dennis N on 2022-07-01
The installer has been doing this at least as far back as Ubuntu 20.04, as I noted in this post:
[https://ubuntuforums.org/showthread.php?t=2460010&p=14030262#post14030262](https://ubuntuforums.org/showthread.php?t=2460010&p=14030262#post14030262)
And there were other weird things, like ms-dos default and placing / on a logical rather than primary partition.

---

### Post by tea for one on 2022-07-01
> **Dennis N said:**
> The installer has been doing this at least as far back as Ubuntu 20.04, as I noted in this post:
[https://ubuntuforums.org/showthread.php?t=2460010&p=14030262#post14030262](https://ubuntuforums.org/showthread.php?t=2460010&p=14030262#post14030262)
And there were other weird things, like ms-dos default and placing / on a logical rather than primary partition.
Your memory is second to none.
I notice that I also contributed in that thread but my memory escapes me more often than not ;)

---

### Post by tea for one on 2022-07-02
> **oldfred said:**
> Was ESP mounted in fstab? 
That is my second check on which way it is really installed.

Legacy installation of Ubuntu 22.04 and booted in Legacy mode.
```
test@test-NUC6CAYH:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
Legacy
test@test-NUC6CAYH:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME    SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT
sda    59.6G disk                       
&#9500;&#9472;sda1    1M part                       
&#9500;&#9472;sda2  513M part vfat       1%  506.7M /boot/efi
&#9492;&#9472;sda3 59.1G part ext4      17%   44.8G /
test@test-NUC6CAYH:~$ 
```

---

### Post by guiverc on 2022-07-02
If you don't want the ESP, the Ubuntu Desktop installer `ubiquity` can be used to install without one, which is the default of the `calamares` installer used by Lubuntu/Ubuntu-Studio.  By default `ubiquity` does create an ESP for recent releases; ISOs using `calamares` do not.

The creation of ESP does **not** impact boot though; as old BIOS boxes I use in QA just ignore it (*they have no choice, a box/firmware from 2005 doesn't know what the partition is for*).

---

### Post by tea for one on 2022-07-03
The calamares installer seems to make more pertinent default choices when booting in Legacy mode i.e. not including an ESP.

Using default choices, the Ubuntu 22.04 installer creates 3 partitions during a Legacy installation.
The tricky part arises when a user supplies a boot-repair report with both both BIOS boot and EFI partitions.
Sometimes, it is difficult to offer correct advice due to the presence of the two boot partitions.

A default Ubuntu 22.04 installation in UEFI mode only creates two partitions so a boot-repair report would be easier to follow.

---

