---
title: "Grub fails to install in a VirtualBox installation of Ubuntu MATE Groovy Aug 01, 2020"
date: 2020-08-01
forum: Ubuntu Development Version
---

### Post by jagsdesai on 2020-08-01
**Note: I am just trying to figure out what and how the installation setup have changed since Focal 20.04 to Groovy 20.10**

Also, I have read this post: ```
https://ubuntuforums.org/showthread.php?t=2447379
``` but it sounds different issue from the one I am having.

I was having the exact same issue with July 06, 2020 ISO of Ubuntu MATE daily live too, and here are the bug reports I have filed:

```
https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1886580

https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1889989
```

** The issue:**
Though I'm trying to install Ubuntu MATE Groovy in a VirtualBox installation, I like to make it clear that, this is a desktop PC with old-style BIOS (No UEFI at all).
Also, EFI is not selected in VirtualBox settings.

Version:
Ubuntu MATE 20.10 daily live ISO I'm installing from is of Aug 01, 2020
VirtualBox version is: VirtualBox-6.1.97-139665-Linux_amd64, and it runs Ubuntu MATE 20.04 Focal with kernel version 5.7.11

When I first tried to install it with just two partitions (like I always have up until now),

(1) First EXT4 partition of 22GB, and
(2) Second SWAP partition of 3GB;

installer displayed:

Error-1:
"No EFI System Partition was found. This system will likely not be able to boot successfully, and the installation process may fail. Please go back and add an EFI System Partition, or continue at your own risk".

and upon clicking Continue, it displayed:

Error-2:
"The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked as a "Reserved BIOS boot area" and should be at leat 1 MB in size. Note that thi is not the same as a partition mounted on /boot.

If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition".

So I went back and created:
(1) EFI partition 1GB
(2) Reserved BIOS boot area partition 1GB
(3) / EXT4 partition 20GB
(4) SWAP partition 3GB

So even with "EFI" and "biosgrub" partitions, grub fails to install on either SDA/SDA1/SDA2/SDA3 with a message,

"Bootloader install failed: Sorry, an error occurred and it was not possible to install the bootloader at the specified location".

Many thanks in advance.

Imgur albums:

```
July 06, 2020: https://imgur.com/a/xKf8nNM

Aug  01, 2020: https://imgur.com/a/sjMi756
```

---

### Post by SeijiSensei on 2020-08-01
On VMs I just install the whole shebang into a single disk image. I don't do any partitioning at all.

---

### Post by jagsdesai on 2020-08-01
> **SeijiSensei said:**
> On VMs I just install the whole shebang into a single disk image. I don't do any partitioning at all.

Thanks for the reply. 

The very reason to create a new VM with Ubuntu MATE Groovy desktop daily live iso is to know the new things (if any) in it, and how the installation have changed (if at all) from 20.04 to 20.10

Otherwise I have two 20.04 VMs up and running just fine on Ubuntu MATE 20.04

---

### Post by Bashing-om on 2020-08-01
jagsdesai; Hello

BootHole vulnerability ?
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass)

Are you also affected:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1889509](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1889509)

[INDENT]hard to make a distinction
[/INDENT]

---

### Post by SeijiSensei on 2020-08-01
I still don't see a reason to partition the VirtualBox disk image. I partition physical hard drives, but they're usually 500GB or larger, and I sometimes have multiple flavors of Ubuntu installed, so I need to be able to select among them at boot.  I usually also assign a separate partition for /home. But partitioning a virtual drive that's just 30-50 GB seems like overkill.

Also, you should be able to edit the repository list in /etc/apt/sources.list on a 20.04 machine to use "groovy" instead of "focal", e.g.,

```
deb http://us.archive.ubuntu.com/ubuntu/ **groovy** main restricted
```

then run

```

sudo apt update
sudo apt upgrade

```

grub2 was automatically updated on my 20.04 systems in the past couple of days, and again today, presumably to fix the BootHole vulnerability.

---

### Post by jagsdesai on 2020-08-01
> **Bashing-om said:**
> jagsdesai; Hello

BootHole vulnerability ?
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass)

Are you also affected:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1889509](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1889509)
[INDENT]hard to make a distinction
[/INDENT]


Thanks for the reply. 

The issue I am having is that, **Grub fails to install**. Vulnerable or not, Grub should get installed.

And as I have said previously, "The very reason to create a new VM with Ubuntu MATE Groovy desktop daily  live iso is to know the new things (if any) in it, and how the  installation have changed (if at all) from 20.04 to 20.10".

This is not my main system,.. not even the VM that I would use beyond installations.

---

### Post by jagsdesai on 2020-08-01
> **SeijiSensei said:**
> I still don't see a reason to partition the VirtualBox disk image.

Here's reason #1: I can install any version (including Ubuntu MATE 20.04) of Ubuntu, and Debian up until Ubuntu MATE 20.10, inside a VirtualBox VM, with partitioning of my choosing.. but the installation fails on 20.10.

Reason #2: Try out the development version and report bugs (if I find any). And that's why I have submitted two bug reports on Launchpad (which by the way, the installer ask you to submit right after the installation fails).

Also, that's why I am posting this in "Ubuntu Development Version" section of Ubuntu Forums.


> **SeijiSensei said:**
> Also, you should be able to edit the repository list in /etc/apt/sources.list on a 20.04 machine to use "groovy" instead of "focal", e.g.,

```
deb http://us.archive.ubuntu.com/ubuntu/ **groovy** main restricted
```

then run

```

sudo apt update
sudo apt upgrade

```

grub2 was automatically updated on my 20.04 systems in the past couple of days, and again today, presumably to fix the BootHole vulnerability.

I guess you did not read or notice what I replied to you previously that:

 "The very reason to create a new VM with Ubuntu MATE Groovy desktop daily  live iso is to know the new things (if any) in it, and how the  installation have changed (if at all) from 20.04 to 20.10

Otherwise I have two 20.04 VMs up and running just fine on Ubuntu MATE 20.04".

---

### Post by QIII on 2020-08-02
Hello!

Although unlikely, the issue may be that VirtualBox is not prepared to support Groovy.  Maybe the MATE team doesn't have 20.10 ready for VirtualBox.  VirtualBox also "taints" the kernel, so some bug reports like failure to install will be shuffled to the back of the queue.

Have you tried a KVM installation?  That might be interesting.  Also, noses might not be turned up at bug reports.

---

### Post by jagsdesai on 2020-08-02
> **QIII said:**
> Hello!

Although unlikely, the issue may be that VirtualBox is not prepared to support Groovy.

Thanks for the reply. Now that could very well be a possibility...

But if that's the case, would the desktop live iso boot normally ? 'Coz from a brief usage, the live environment was working just fine with the net access (and that's how I was able to submit semi-automated bug reports).

Also, other VMs, Ubuntu MATE 20.04, Manjaro MATE, 2 more Ubuntu headless servers, are running just fine on the same host.

By the way, I am using "Development snapshots" of VirtualBox. The version is VirtualBox-6.1.97-139665-Linux_amd64. Host OS is Ubuntu MATE 20.04 with kernel 5.7.11

Lastly, I have never got these (1) EFI system partition, and (2) Reserved BIOS  boot area, error messages up until 20.10 during any virtual  installations.
 
[IMG]https://i.imgur.com/uFvE62s.jpg[/IMG]

[IMG]https://i.imgur.com/nXrHSDl.jpg[/IMG]

---

### Post by P-I H on 2020-08-02
I have installed Groovy in VirtualBox.
The installation failed without the "Enable EFI" setting.
This is however on a computer that supports EFI,  but try to install with the EFI setting.

---

### Post by jagsdesai on 2020-08-02
> **P-I H said:**
> I have installed Groovy in VirtualBox.
The installation failed without the "Enable EFI" setting.
This is however on a computer that supports EFI,  but try to install with the EFI setting.

Yes, I can confirm that the installation went through after selecting "Enable EFI" option in VirtualBox settings, and Groovy runs fine afterwards.

EDIT: Forgot to add, installation went through fine with manual partitioning.

But as I said in my original post, I intentionally did not select it previously, even after few failed installations, as I wanted to know why the Groovy installer needed EFI to be enabled because Focal installer did not need it.

Now this raises a question (if anyone have the answer) that, since this was a VM, I was able to enable the EFI but, how would you install Groovy on an actual hardware with BIOS (no UEFI at all)?

Thank you all.

Screen for Enable EFI option in VirtualBox: ```
https://i.imgur.com/ED7TDIF.jpg
```

---

### Post by saivinoba2 on 2020-10-16
@jagsdesai,

I tested several scenarios today and following are my observations.

1) Groovy ISOs now default to GPT partitioning scheme by default. 
   a) If we booted in BIOS mode, this will create minimum three  partitions, 1M 'BIOS grub', 512M as 'EFI System Partition' for /boot/efi  and remaining for /.
   b) If we booted in UEFI mode, this will create two partitions, 512M  as 'EFI System Partition' for /boot/efi and remaining for /
   c) If we are doing manual partitioning, it is not mandatory to create  a BIOS grub partition. Just and EFI partition and root partition is  sufficient.

2) Focal ISOs default to MBR partitioning if booted in BIOS mode and GPT  if booted in UEFI mode. However, I noticed, for BIOS mode, Focal will  offer following partitioning scheme,
   a) during install but before grub-install: 512M as W95 FAT32 (/dev/sda1) and remaining for / (/dev/sda5, extended partition)
   b) after grub-install: 512M /dev/sda1 will change time to ef (EFI FAT  16/24/32). It will be mounted as /boot/efi (or /target/boot/efi during  install).

For your test case, you can do following.
a) create only EFI partition (200M should be enough). Do not format and choose /boot/efi as mount point. 
b) if you create BIOS grub, then, 
   i) BIOS grub should be the first partition not second. It is enough if it is 1M not 1G. Should not be formatted and no mount point to be assigned.
   ii) create an EFI system partition, do not format and mount as /boot/efi

You had created 1G BIOS grub but as second partition. BIOS grub has to be the first partition.

If you are still planning on testing, please use above suggestion to verify.

---

