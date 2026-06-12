---
title: "UEFI &amp; efi issues"
date: 2015-04-20
forum: Ubuntu Development Version
---

### Post by oldfred on 2015-04-20
Anyone else tried editing efi partition with Vivid?

Just installed Vivid to sdb hard drive when I have Trusty on sda SSD.

I specifically told it to install grub to sdb, and even noticed in list of running tasks a grub install to sdb, but it actually installed grub to sda, overwriting my trusty ubuntu efi partition. Actual only real change was the configfile grub.cfg in /EFI/ubuntu was changed to new GUID & partition for Vivid.
But had reboot error and had to use this to boot trusty on reboot from trusty it booted vidid, but on reboot from vivid it gave the error again. Vivid shutdown issue?
configfile (hd0,3)/boot/grub/grub.cfg

Major issue with Vivid is that all of oldfred's instructions an editing efi partition will not work. They changed default mount of efi partition from defaults to 0077, and then you cannot edit folders or files in efi partition from install. Live install may work and I was able to edit from trusty.

 14.04 fstab entry defaults
drwxr-xr-x 3 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     4096 Mar 24 12:08 grub
        
15.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1
drwx------ 3 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     4096 Mar 26 13:52 grub

    
Also then changed umask=0077 to defaults and did a remount with sudo mount -a, but it did not reset. Only rebooting then reset the permissions.

Also tried changing distributor so in UEFI I could tell them apart.

 #GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="trusty"

And I got different UEFI entries:

 Boot0003* [COLOR=#ff0000]vivid    [/COLOR]HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\VIVID\SHIMX64.EFI)
Boot0004* [COLOR=#ff0000]trusty[/COLOR]    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\trusty\shimx64.efi)

But all entries use the grub.cfg in /EFI/ubuntu or only default works. That has been good for those copying grub into /EFI/Boot to get those UEFI that will not boot anything but Windows, but not so good for me to keep track of which install I want to boot directly from UEFI menu. 

Back to test a full grub install specifying efi install partition to match distributor.

---

### Post by ventrical on 2015-04-21
No matter what I have tried I always get the same thing as long as I have another hdd in the working system. I have read all about a lot of fixes but here is what I do.

[http://ubuntuforums.org/showthread.php?t=2213631&page=2&p=13266283#post13266283](http://ubuntuforums.org/showthread.php?t=2213631&page=2&p=13266283#post13266283)

Regards..

---

### Post by ventrical on 2015-04-21
> **oldfred said:**
> Anyone else tried editing efi partition with Vivid?

Just installed Vivid to sdb hard drive when I have Trusty on sda SSD.

Major issue with Vivid is that all of oldfred's instructions an editing efi partition will not work. They changed default mount of efi partition from defaults to 0077, and then you cannot edit folders or files in efi partition from install. Live install may work and I was able to edit from trusty.

 

The Canonical Community Fund was kind enough to grant me assistance to aquire a new 3TB hdd specifically for testing UEFI. I have done some work but nothing notable to report as of yet. Also other work has called me away temporarily but I commit to continue to follow and contribute to  these threads as best I can.

Regards..

---

