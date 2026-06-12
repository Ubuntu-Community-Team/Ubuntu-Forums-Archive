---
title: "[Q] Configuration PXE Multiboot Server"
date: 2013-11-24
forum: Server Platforms
---

### Post by c.monty on 2013-11-24
Hello!

I want to setup a PXE Multiboot Server following this [tutorial]("https://help.ubuntu.com/community/PXEInstallMultiDistro").
In my setup, all servers DHCP, NFS and TFTP are running on a single host. DHCP and TFTP service is provided by [Dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html").

In this tutorial there are many configuration examples for distros Ubuntu, Fedora, etc.
However I don't know how to adapt this to different distros, e.g. [Clonezilla]("http://clonezilla.org/livepxe.php") and [Desinfec't]("http://www.heise.de/security/artikel/Desinfec-t-vom-Linux-Server-booten-1658049.html").

My understanding is, that the most important config-files (when following this tutorial-approach) are:
/<path/to/file>/pxelinux.cfg/default
/<path/to/file>/<distro>.menu

For the above mentioned Live-distros, I have downloaded the ISO and copied its content to the NFS server.

Clonezilla:
```
root@net2:/# tree nfs/install/clonezilla/amd64/
nfs/install/clonezilla/amd64/
|-- Clonezilla-Live-Version
|-- EFI
|   |-- boot
|   |   |-- bootia32.efi
|   |   |-- bootx64.efi
|   |   |-- grub.cfg
|   |   |-- ocswp-grub2.png
|   |   `-- unicode.pf2
|   `-- images
|       `-- efiboot.img
|-- GPL
|-- boot
|   `-- grub
|       `-- grub.cfg
|-- home
|   `-- partimag
|-- isolinux
|   |-- chain.c32
|   |-- drblwp.png
|   |-- isolinux.bin
|   |-- isolinux.cfg
|   |-- ldlinux.c32
|   |-- libcom32.c32
|   |-- libutil.c32
|   |-- memdisk
|   |-- menu.c32
|   |-- ocswp.png
|   `-- vesamenu.c32
|-- live
|   |-- filesystem.packages
|   |-- filesystem.packages-remove
|   |-- filesystem.squashfs
|   |-- freedos.img
|   |-- initrd.img
|   |-- ipxe.lkn
|   |-- memtest
|   `-- vmlinuz
|-- syslinux
|   |-- chain.c32
|   |-- drblwp.png
|   |-- ldlinux.c32
|   |-- libcom32.c32
|   |-- libutil.c32
|   |-- memdisk
|   |-- menu.c32
|   |-- ocswp.png
|   |-- syslinux.cfg
|   `-- vesamenu.c32
`-- utils
    |-- README.txt
    |-- linux
    |   |-- VERSION.txt
    |   |-- extlinux
    |   |-- makeboot.sh
    |   `-- syslinux
    |-- mbr
    |   `-- mbr.bin
    `-- win32
        |-- VERSION.txt
        |-- makeboot.bat
        |-- syslinux.exe
        `-- syslinux64.exe

14 directories, 48 files

```

From this files I have identified the following that looks promising:
```
root@net2:/# cat nfs/install/clonezilla/amd64/isolinux/isolinux.cfg
[...]
label Clonezilla live
  MENU DEFAULT
  # MENU HIDE
  MENU LABEL Clonezilla live (Default settings, VGA 800x600)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live username=user config quiet noswap edd=on nomodeset locales= keyboard-layouts= ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_batch=no vga=788 ip=frommedia  nosplash i915.blacklist=yes radeonhd.blacklist=yes nouveau.blacklist=yes vmwgfx.enable_fbdev=no
  TEXT HELP
  * Boot menu for BIOS machine
  * Clonezilla live version: 2.2.0-29-amd64. (C) 2003-2013, NCHC, Taiwan
  * Disclaimer: Clonezilla comes with ABSOLUTELY NO WARRANTY
  ENDTEXT

MENU BEGIN Other modes of Clonezilla live
label Clonezilla live 1024x768
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL Clonezilla live (Default settings, VGA 1024x768)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live username=user config quiet noswap edd=on nomodeset locales= keyboard-layouts= ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_batch=no vga=791 ip=frommedia  nosplash i915.blacklist=yes radeonhd.blacklist=yes nouveau.blacklist=yes vmwgfx.enable_fbdev=no
  TEXT HELP
  VGA mode 1024x768. OK for most of VGA cards.
  ENDTEXT
[...]

```

Desinfec't:
```
root@net2:/# tree nfs/install/desinfect/2013/
nfs/install/desinfect/2013/
|-- casper
|   |-- initrd.lz
|   `-- vmlinuz
`-- isolinux
    |-- boot.cat
    |-- chain.c32
    |-- isolinux.bin
    |-- isolinux.cfg
    |-- local.cfg
    |-- os.cfg
    |-- splash.png
    `-- vesamenu.c32

2 directories, 10 files
```

From this files I have identified the following that looks promising:
```
root@net2:/# cat nfs/install/desinfect/2013/isolinux/os.cfg 
label desinfect
  menu label Desinfec't 2013.1 starten
  kernel /casper/vmlinuz
  append BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=/software/desinfect-2013.1.iso quiet splash memtest=4 -- debian-installer/language=de console-setup/layoutcode?=de

```

The main problem for me is to transfer this to a working PXE configuration.
In particular the APPEND options are causing me headache.
  file=/cdrom/preseed/ubuntu.seed
  iso-scan/filename=/software/desinfect-2013.1.iso   

What I'm looking for is a how-to-guide to transfer the config from any ISO = distro to a working PXE config.

Can anybody assist here?

THX

---

