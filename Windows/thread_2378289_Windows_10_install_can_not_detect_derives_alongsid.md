---
title: "Windows 10 install can not detect derives alongside with Ubuntu 17.10"
date: 2017-11-21
forum: Windows
---

### Post by dannal on 2017-11-21
I first installed Ubuntu 17.10, then I want to install windows 10 alongside to make a dual boot system. When I installed windows 10, the installment can not find any drives. When I boot with Ubuntu, I still can see all the drives. Before Windows 10 installment, I format the drive to NTFS, this partition was shrined from the drive Ubuntu was installed.

Any ideas?

Thanks!

---

### Post by yancek on 2017-11-22
Were actually able to install windows 10 or did that fail?

When you refer to 'drives' are you talking about multiple actual physical hard drives or simply partitions on one physical drive?  I ask that because windows uses those terms interchangably.

What are you able to do now, can you boot Ubuntu?
Did you format a 'partition' on the drive ntfs for a windows install?  Formatting the entire drive (if you only have one would have overwritten Ubuntu?)
A default windows system won't be able to access any Linux partition with a Linux filesystem, that's by design.  If you were able to boot windows you would be able to see in Disk Management the Linux partitions shown as "Healthy partition/drive" or something similar.

When you went to install windows 10, did you select the Custom install option?  If you do that you will be able to select a specific ntfs partition on which to install windows.
Is Ubuntu a UEFI install?  

If you are still able to boot Ubuntu installed, open a terminal and run this command and post the output here:

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

Also, run the command below from Ubuntu and post the output.  If you cannot boot the installed Ubuntu, boot the installation media and from a terminal run the following command and post the output.

```
sudo parted -l
```  Lower Case Letter L in the command.

---

### Post by dannal on 2017-11-22
Thanks Yancek! I reinstalled the Intel RSTe SCU/SATA Management Utility and can find hard drives right now. Now I have a warring: "......The selected disk has an MBR partition table.On EFI system, windows can only be installed to GPT disks......". I am wondering can I install windows in the partition shrunken from the SSD which Ubuntu was installed in? or can I change the partition from MBR to GPT for windows? or other suggestions?

Thanks in advanced!

---

### Post by oldfred on 2017-11-22
Windows only boots with BIOS from MBR partitoned drives. And boot drive must be a primary NTFS partition with boot flag.
Windows only boots with UEFI from gpt partitioned drives. It requires multiple partitions so best to just let it install into available unallocated space.

How you boot install media UEFI or  is then how it installs, but then drive if pre-partitioned it must matchhow you boot and want to install.

With new UEFI hardware best to have all installs in the newer UEFI boot configuration. But you can force the 35 year old BIOS/MBR configuration if desired.

Probably best to backup Ubuntu (you can then confirm your backup procedures are good). Install Windows in UEFI boot mode after erasing drive & converting to gpt. And then reinstall Ubuntu and restore your data.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

