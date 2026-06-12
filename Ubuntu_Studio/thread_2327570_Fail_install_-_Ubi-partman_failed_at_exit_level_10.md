---
title: "Fail install - Ubi-partman failed at exit level 10"
date: 2016-06-12
forum: Ubuntu Studio
---

### Post by Matthew_Abd-El-Aha on 2016-06-12
I'm attempting to install Ubuntu Studio 16.04 64-bit on an ASUS X555UJ.

I have done some searches and found a few other people with similar situations and none of the following advice has helped:

* Disabling fast start.
* Disabling secure boot.
* Disabling CSM.
* Enabling EFI (cannot find shell in the filesystem).
* Addind nodmraid and/or pci=nomsi to the GRUB boot command.

The md5sum is intact so I'm all out of gum.

EDIT: /var/log/syslog is 2GB! It won't open! When I restart the system it has this untintelligible scrolling error, all I can make out is perhaps some kind of PCI bus error?

---

### Post by oldfred on 2016-06-12
I had just about given up on this user.
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3) 

But it turns out the pci=nomsi is vital on several models of Asus.

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

Some other issues that may be important:
 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)

---

### Post by Matthew_Abd-El-Aha on 2016-06-13
Okay, so now I have all the stuff disabled and running pci=nomsi in the install Ubuntu without trying mode and it has worked except after the installation I am getting this:

"The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot."

Solutions?

---

### Post by oldfred on 2016-06-13
Did you partition in advance and not create an ESP - efi system partition.
Or do you not have the ESP on sda? Grub only installs to sda's ESP.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

In a few cases we have seen "locked" FAT32 partitions, which is not really possible, but may be from corruption. Either chkdsk from Windows or this from Ubuntu clears it.
       Change this example with sdb1 to your ESP.
 sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by Matthew_Abd-El-Aha on 2016-06-13
I've created partitions in advance and the EFI partition is there by default.

---

### Post by Matthew_Abd-El-Aha on 2016-06-14
Summary of the entire process:

* Asus x555UJ gives "ubi-partman failed at exit level 10" error during installation process.
* Held F2 and disabled fast boot, secure boot and CSM.
* In grub, pressing "e" on the option to try ubuntu and adding pci=nomsi before the quiet splash parameter.
* Pressed F10.
* Opened ubiquity installer and at the partition manager screen I changed the original grumpy FAT32 Windows boot partition to a sparkly new EFI partition.

I am still receiving the "The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot." error message.

Here is the boot-info log: [http://paste2.org/n5JxLjt5](http://paste2.org/n5JxLjt5)

I'm attempting boot-repair now.

Here's the new boot-info log: [http://paste2.org/tZCADJHz](http://paste2.org/tZCADJHz)

Lets restart and check this out.

---

### Post by oldfred on 2016-06-14
Windows only boots in UEFI mode from gpt partitioned drives.
But you also have syslinux which is a Windows type BIOS boot loader in MBR. Do not try to boot in BIOS mode. 

Your second report shows Microsoft & Ubuntu folders in ESP.
But still no entry for ubuntu in UEFI boot menu.
sudo efibootmgr -v

Did you try running the repairs with Boot-Repair?

---

### Post by Matthew_Abd-El-Aha on 2016-06-14
Boot-repair worked like a charm! :D

However I have changed the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub to "pci=nomsi quiet splash" yet booting continues to error unless I hit e and manually type in the pci=nomsi parameter manually.

Should this be in the GRUB_CMDLINE_LINUX rather than the DEFAULT line?

EDIT: I will mark this thread [SOLVED] and post a summary once the boot loader is sorted.

---

### Post by Matthew_Abd-El-Aha on 2016-06-14
Okay, I don't know why but when I restarted my laptop and hit "e" at GRUB boot loader the pci=nomsi parameter was actually present.

Looks like it's all sorted, in summary the problem and procedure was as follows:

* Asus x555UJ gives "ubi-partman failed at exit level 10" error during installation process.
* Held F2 and disabled fast boot, secure boot and CSM.
* In grub, pressing "e" on the option to try ubuntu and adding pci=nomsi before the quiet splash parameter.
* Pressed F10.
* Opened ubiquity installer and at the partition manager screen I  changed the original grumpy FAT32 Windows boot partition to a sparkly  new EFI partition.
* Still failed so obtained boot-info to post boot details, ran boot-repair and all went well.
* Sealed the deal by editing /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT line /etc/default/grub to "pci=nomsi quiet splash".

Credit to user oldfred and others who have reported and helped on similar issues on similar devices.

---

