---
title: "I want to uninstall Ubuntu dualboot, but can't get rid of Grub."
date: 2017-01-25
forum: Windows
---

### Post by silacko on 2017-01-25
Hi,
I've been using Ubuntu with dualboot for a couple of months now, but now that I no longer need it, I want to uninstall Ubuntu from my computer. There are two partitions allocated for Ubuntu which I'm going to delete; however, I believe I should restore my Windows Boot Record first.
However, I can't get rid of Grub and go back to Windows Boot Loader. I created a Windows recovery drive, booted my PC with it, opened the command line, and tried writing down the following:
```

bootrec /RebuildBcd
bootrec /fixMbr
bootrec /fixboot

```
And it didn't work. Then, I tried typing: ```
bootsect /nt60 C: /mbr
```
 which sadly didn't work either. It returned the following:
```

C:\WINDOWS\system32>bootsect /nt60 C: /mbr
Target volumes will be updated with BOOTMGR compatible bootcode.
C: (\\?\Volume{b2495490-0560-4f98-b774-b59c745d121a})
    Updated NTFS filesystem bootcode.  The update may be unreliable since the
    volume could not be locked during the update:
        Access denied.
\??\PhysicalDrive0
Bootcode is only updated on MBR partitioned disks.  A different partitioning scheme is used on this disk.
Bootcode was successfully updated on all targeted volumes.

```

I don't know whether this is an error or just a warning, but it simply doesn't work.
I searched some other forums, but I still couldn't find an answer to this. My PC still boots with Grub, and I'm afraid it will be useless if I delete the Ubuntu partitions in this state. What do you think I should do?

---

### Post by howefield on 2017-01-25
Thread moved to the "*Windows*" forum.

Would probably help to know which version Windows you are using ?

---

### Post by silacko on 2017-01-25
I'm using Windows 10 (version 1607). Thanks for replying.

---

### Post by yancek on 2017-01-25
> Bootcode is only updated on MBR partitioned disks.  A different partitioning scheme is used on this disk.

The message above indicates that you are using EFI to boot on your system rather than the older MBR method and the commands you used are for an MBR system and won't do anything, well anything useful.  EFI is the default on windows 8 and 10.   

Also, there is a message about the volume being locked during the update.  I'm not sure, but that might mean you left windows hibernated while running the command.  The link below gives a method to repair the EFI from windows.  The second link below seems a little more detailed but the same process:

[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

[https://blog.d0zingcat.xyz/2015/09/28/Windows/How%20to%20repair%20the%20EFI%20Bootloader%20in%20Windows%2010/](https://blog.d0zingcat.xyz/2015/09/28/Windows/How%20to%20repair%20the%20EFI%20Bootloader%20in%20Windows%2010/)

---

### Post by oldfred on 2017-01-25
With UEFI boot, all boot files are in the ESP - efi system partition.
And UEFI sets boot order, so all you need to do is go into UEFI and reset boot order to have Windows first.

You can also set boot order with Linux live installer using efibootmgr.
And you probably want to remove the Ubuntu/grub entries from UEFI boot. And can delete the /EFI/ubuntu folder in the ESP.

       Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

Similar info in link in my signature on UEFI menu clean up.

---

### Post by silacko on 2017-01-27
Thanks, folks! The solution suggested in [http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/) worked. My PC now boots directly to Windows, and I've deleted the Ubuntu partition successfully.

---

