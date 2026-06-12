---
title: "Dual Boot Removal"
date: 2018-04-16
forum: Windows
---

### Post by sccjono on 2018-04-16
Hi all. I have a laptop that with your help I set up to dual boot (using Grub) to both Ubuntu & Windows 10. I have now treated myself to a new laptop and I have replicated your instructions and all is well. However, I wish to return the previous laptop to a Windows only machine, to give to my wife, without factory resetting it (I'd really like to avoid setting up Windows again from scratch). How easy is this to do? I guess I need to alter the bootloader to bypass Grub and somehow reclaim the disk space that is currently allocated to Linux. Can this even be done?

Idiot-proof instructions if possible please.

jono

---

### Post by oldfred on 2018-04-16
UEFI or BIOS as instructions are different.
But either way do not delete Ubuntu partitions, until you have reset system to default boot Windows directly from UEFI or BIOS (not thru grub).

Post this:
sudo parted -l

---

### Post by sccjono on 2018-04-17
Thank you for your help. As requested.

```
jono@htl1:~$ sudo parted -l[sudo] password for jono: 
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   492GB   492GB   ntfs         Basic data partition          msftdata
 6      492GB   984GB   492GB   ext4
 4      984GB   985GB   1028MB  ntfs         Basic data partition          hidden, diag
 5      985GB   1000GB  15.0GB  ntfs         Basic data partition          hidden, msftdata
```

---

### Post by oldfred on 2018-04-17
You have UEFI system.

You need to reset UEFI to boot Windows first. You should be able to do that from UEFI directly, or from efibootmgr in Ubuntu.
And then you can remove the /EFI/ubuntu folder in the ESP - efi system partition, your sda1 and then remove the Ubuntu partition sda6. Best to remove partition with gparted, although you can do it from Windows. Its just Windows does not see the ext4 partition correctly.
Then use Windows to expand the NTFS partition to use the unallocated space that was the Linux ext4 partition.

 Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi) 


 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by sccjono on 2018-04-19
OK, I have followed your instructions (which were really clear thank you) and deleted the entry from efibootmgr, I then also deleted the EFI/Ubuntu directory. I have also used gparted to unmount and delete sda6. I am now booting back to Windows automatically. So great stuff and thank you. The last thing I need to do is reclaim the unallocated disk space to add to the Windows C: drive. I'm guessing that is outside the scope of this forum is there any chance you could point me in the right direction?

Thanks
jono

---

### Post by hrsetrdr on 2018-04-19
If the space left from the former Ubuntu install is on the same disc as that which is the C: drive, I believe you can use Windows Disk Management feature to expand that as the ntfs partition.

---

### Post by sccjono on 2018-04-19
D'oh, of course it can. I've been away from Windows for too long. Thank you both.

---

