---
title: "Ubiquity"
date: 2015-10-15
forum: Ubuntu Development Version
---

### Post by P-I H on 2015-10-15
I have 2 disks sda a 640 GB HD and sdb a 120GB SSD. I installed Wily, choosed "Use the Whole disk" and selected the SSD disk. There was no problem with the installation.
BIOS was set to install from the SSD, but after restart the the system didn't boot.
I changed boot disk in BIOS to the 640 GB HD and the system booted OK. I expected to boot Ubuntu 14.10, but Ubuntu 15.10 was started.
Obviously grub was installed on sda and not as expected on sdb.
I found a bug report on Launchpad
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1476178](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1476178)

---

### Post by ajgreeny on 2015-10-15
Unfortunately the only way to put grub exactly where you want it is to use the "Something Else" option when installing; if you choose to use "Whole disk" the system will default to using the first hard disk for grub, ie, in your case the HDD, not the SSD.

It may be possible to sort out your problem by using Grub-Repair in my signature and running the Boot-info script, then posting back here the report with the pastebin link you should see.

That will show us what has gone on here, where the OSs are installed (are there two OSs or just one?) and where grub is now installed; perhaps grub is now on both drives.  What happens if you run command ```
sudo update-grub
``` in the 15.10 Wily installation; does it then find the other OS if there is one, or is that not what you want?  You might also simply need to sort out which disk is the SSD with command ```
sudo parted -l
``` and then run ```
sudo grub-install /dev/sdx
``` where /sdx is the SSD.

---

### Post by P-I H on 2015-10-15
I think this is a major problem with Ubiquity. In case you select to install Ubuntu on a disk that isn't sda, you expect grub to be placed on the disk you have selected. 
On this new install of wily, grub didn't start when I booted from the SSD, which was sdb. Before I made a new install, there was a wily version and grub on the SSD. I suppose the "old" grub had the wrong information and didn't finish the boot.

To fix the problem I run
```
sudo grub-install /dev/sdb
```

---

### Post by kansasnoob on 2015-10-15
> **P-I H said:**
> I think this is a major problem with Ubiquity. In case you select to install Ubuntu on a disk that isn't sda, you expect grub to be placed on the disk you have selected. 
On this new install of wily, grub didn't start when I booted from the SSD, which was sdb. Before I made a new install, there was a wily version and grub on the SSD. I suppose the "old" grub had the wrong information and didn't finish the boot.

To fix the problem I run
```
sudo grub-install /dev/sdb
```

After just using the "grub-install" command you'll find that after each kernel upgrade dpkg places grub back where the installer originally put it. To avoid that you need to run:

```
sudo dpkg-reconfigure grub-pc
```

**Important note**: The package name 'grub-pc' is different/wrong for UEFI installs but I don't recall the proper package name for EFI installs :redface:

---

### Post by QDR06VV9 on 2015-10-15
> **kansasnoob said:**
> After just using the "grub-install" command you'll find that after each kernel upgrade dpkg places grub back where the installer originally put it. To avoid that you need to run:

```
sudo dpkg-reconfigure grub-pc
```

**Important note**: The package name 'grub-pc' is different/wrong for UEFI installs but I don't recall the proper package name for EFI installs :redface:

+1
I think it is "grub-efi" now. But I Could be wrong.

---

### Post by tista on 2015-10-15
Greetings,

Grub for EFI is named **grub-efi-amd64**.

Regards.

---

### Post by P-I H on 2015-10-16
Thanks to all.

This is an old system and
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure grub-pc[/FONT][/COLOR]
```
was OK

---

