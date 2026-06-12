---
title: "Elementary OS fails to boot"
date: 2014-08-11
forum: Ubuntu/Debian BASED
---

### Post by cperkins141 on 2014-08-11
Tried to set up a dual boot machine with windows 8.1 along with the new elementary os beta 1.  Boots into the grub command line.  I can get into windows with some finicking but elementary os does not boot.
Also ran boot-repair here's the output: [http://paste2.org/Yz4B0bKL](http://paste2.org/Yz4B0bKL)
Let me know if there is anything else you need from me to help.  Thanks in advance

---

### Post by oldfred on 2014-08-11
I do not see anything wrong.

It does say it reinstalled grub without error as error code 0 is no error.

       Reinstall the GRUB of sda8 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Post the copy of grub.cfg in your /efi/elementary. It should just be 3 lines with a configfile entry to point to your main install in sda8. Script has not been updated to automatically print that.

---

### Post by cperkins141 on 2014-08-11
> **oldfred said:**
> I do not see anything wrong.

It does say it reinstalled grub without error as error code 0 is no error.

Reinstall the GRUB of sda8 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Post the copy of grub.cfg in your /efi/elementary. It should just be 3 lines with a configfile entry to point to your main install in sda8. Script has not been updated to automatically print that.
Sorry I am having trouble finding grub.cfg as I have no /efi/elementary.  Not located at /boot/grub either.

---

### Post by oldfred on 2014-08-11
Bootinfoscript does not show the grub file, but does show the folder.

```
 sda2: ______________________________________________
File system: vfat
Boot sector type: Windows 8/2012: FAT32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /EFI/Boot/bootx64.efi /EFI/elementary/MokManager.efi
[COLOR=#ff0000]/EFI/elementary[/COLOR]/grubx64.efi
/EFI/elementary/shimx64.efi
/EFI/Microsoft/Boot/bootmgfw.efi
/EFI/Microsoft/Boot/bootmgr.efi
/EFI/Microsoft/Boot/memtest.efi


```

If using Windows it may not mount the efi partition. Better to use live installer and from Nautilus file browser look for it. If it is really missing that may be the problem.

---

### Post by cperkins141 on 2014-08-11
> **oldfred said:**
> Bootinfoscript does not show the grub file, but does show the folder.

```
 sda2: ______________________________________________
File system: vfat
Boot sector type: Windows 8/2012: FAT32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /EFI/Boot/bootx64.efi /EFI/elementary/MokManager.efi
[COLOR=#ff0000]/EFI/elementary[/COLOR]/grubx64.efi
/EFI/elementary/shimx64.efi
/EFI/Microsoft/Boot/bootmgfw.efi
/EFI/Microsoft/Boot/bootmgr.efi
/EFI/Microsoft/Boot/memtest.efi


```

If using Windows it may not mount the efi partition. Better to use live installer and from Nautilus file browser look for it. If it is really missing that may be the problem.
I am in a live install but of elementary tho.  Hidden files are enabled:  only found /EFI/Boot and /EFI/Microsoft

---

### Post by oldfred on 2014-08-11
Try this. If already mounted by Nautilus in Live installer unmount it first as you can only mount a partition once.

You should not need sudo from live installer:

 mount /dev/sda2 /mnt
cd /mnt/efi
ls -l

---

