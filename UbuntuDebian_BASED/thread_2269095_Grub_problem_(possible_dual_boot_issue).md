---
title: "Grub problem (possible dual boot issue)"
date: 2015-03-13
forum: Ubuntu/Debian BASED
---

### Post by donkeyotay2 on 2015-03-13
Afternoon All,
I have an HP Pavillion laptop with which I would like to dual boot Ubuntu-Mate & Windows 8.1 (which was preloaded). When I boot I get the minimal grub command prompt. I have run the Boot-repair program from a live session to no effect.

Would somebody be able to help me please, as this exceeds my little knowledge. The Pastebin URL is: [http://paste.ubuntu.com/10590599/](http://paste.ubuntu.com/10590599/)

Many thanks in advance.
Don

---

### Post by oldfred on 2015-03-13
Moved to Other OS since Mate not Ubuntu.
Did you have OpenSuse before?

HP does not let you boot anything but Windows by description, so you have to do a work around. Most copy grub or shim to be bootx64.efi and then boot the hard drive entry in UEFI menu.

Not sure what Boot-Repair has done. It used to create the 25_custom, but does not anymore. Was that an old copy of Boot-Repair?

Backup entire efi partition before making any changes:

       From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies. Your efi partition is sda2.

   sudo mount /dev/sda2 /mnt
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, Boot-Repair already did one backup, but not sure what that is now?
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

      You can delete the old OpenSuse entries, first delete the opensuse folder in the efi partition or it will re-add them to UEFI.
 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

