---
title: "Trying to format partition"
date: 2017-05-26
forum: Windows
---

### Post by enigma1992 on 2017-05-26
I am trying to change one of my partitions in order to install  windows 10 on my Ubuntu new DELL laptop but I am having some problems. I entered "Disks" option and when trying to format on of my partitions  to NTFS I got a message says :

"error unmounting /dev/sda3:Command-Line 'unmount " /dev/sda3"" exited with non-zero exit status 32: unmount: /:target is busy (in some cases useful info about processes that use the device is found by lsof(8) or fuser(1)).
(udisks-error-quark, 14)"

How can i solve this ?

---

### Post by oldfred on 2017-05-26
Are you using live installer.
Generally all partitioning requires partitions to be unmounted.

Is system UEFI or BIOS.
Windows only installs to gpt partitioned drives in UEFI boot mode.
Windows only installs to MBR(msdos) partitioned drives in BIOS boot mode.

While in BIOS mode it can install to one primary NTFS partition with boot flag, with UEFI it requires lots of partitions. Best to then let Windows installer add its own partitions.

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

### Post by enigma1992 on 2017-05-26
Hey, thanks for the answer.
I solved it by deleting all of the partitions via boot and then created new partition for windows.

Thanks!

---

