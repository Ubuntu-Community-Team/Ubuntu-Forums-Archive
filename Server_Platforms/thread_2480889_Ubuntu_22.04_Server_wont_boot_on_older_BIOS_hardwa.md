---
title: "Ubuntu 22.04 Server wont boot on older BIOS hardware"
date: 2022-11-13
forum: Server Platforms
---

### Post by fragged on 2022-11-13
I have a machine which does not support UEFI. I created a Ubuntu 22.04 Live Server USB using `dd if=server.iso of=/dev/sdc`. The image boots and installs fine, when I attempt to start the computer post-install, booting fails with 'insert a device with bootable media' error messages.

I have tried forcing the disk into MBR mode (though, I don't _think_ this causes the issue?). I have also attempted to force install grub to the drive, which succeeds using i386 (the system is x64, but afaict all MBR boots are x32). I also updated the BIOS in hopes that it would support UEFI booting, but it had no effect. The disk is a SATA SSD, the motherboard supports IDE emulation over SATA - I have attempted installs both with this enabled and disabled.

I'm unsure if there's something I'm missing, as far as I can tell 22.04 supports BIOS, but support is dwindling. So far all threads I have found on Google have not helped.

Is there something I'm missing here?

---

### Post by MAFoElffen on 2022-11-13
Is the partition table GPT or MSDOS? (while booted with your LiveCD media):
```

sudo fdisk -l | grep -i 'Disklabel type:'

```
If the type is "GPT" and booted as Legacy/CSM BIOS boot, then you also need to create a 1-5 MB, type boot_bios partition, not formatted, for Grub to install other pieces. If not there, it will show like it is installing (without errors), but not be able to boot...

---

### Post by Bashing-om on 2022-11-13
fragged; Hello -

In addition to MAFoElffen's last --

I have this thought:
I too run old hardware with Phoenix Technologies bios - in order to enable AHCI ( Advanced Configuration and Power Interface) to support the swap to a SSD I had to enable raid in my bios setting.

[INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT]

---

### Post by fragged on 2022-11-14
Thanks, I solved it - the motherboard (Asrock X58 Extreme) has 6x SATA II and 6x SATA III. Moving the SSD to the SATA III interface appears to have fixed the issue, if it wasn't for Bashing-om I would not have tried. 

@MFOElffen - thanks for your input also, for those in the future, can I ask a few additional questions?

`If the type is "GPT" and booted as Legacy/CSM BIOS boot, then you also need to create a 1-5 MB, type boot_bios partition, not formatted, for Grub to install other pieces. If not there, it will show like it is installing (without errors), but not be able to boot... `

By default Ubuntu installer did this, I was unclear on whether the partition needed to have a format and file on it (some documentation I've seen indicated it needed a grub i386 binary which acted as a stager to support MBR). So to confirm, the partition is unfomatted and Grub will just write content to (presumably) the first 512 bytes or so? Is there any process for forcing grub to write this partition?

---

### Post by slickymaster on 2022-11-14
*Thread moved to **Server Platforms**.*

---

### Post by oldfred on 2022-11-14
I have used gpt with Ubuntu since 2010. And grub still installs to MBR if in BIOS boot mode, and automatically uses the bios_grub partition if correctly configured as unformatted and with bios_grub flag (if gparted). 

With old BIOS & very old MBR, grub would use the unused space after MBR but before first partition for additional boot data - core.img. MBR too small for all the code grub needs.
But with gpt, the gpt partition tables start immediately after the protective MBR. So MBR exists, but no space for core.img. Thus the bios_grub partition is required.

I started adding both bios_grub & ESP - efi system partition to every new or reformatted drive starting in 2012 when UEFI became the new standard way to boot as Microsoft required UEFI/gpt for all new systems with Windows 8. That way I could convert from BIOS to UEFI without having to totally repartition & reformat a drive.

After using UEFI starting in 2014 for several years and not using BIOS anymore, I now just have an ESP on new or reformatted drives.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

