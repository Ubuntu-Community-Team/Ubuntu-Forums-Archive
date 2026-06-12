---
title: "GRUB Rescue randomly started happening?"
date: 2017-02-22
forum: Windows
---

### Post by mew351 on 2017-02-22
My computer recently blue screened (running Windows 10 as my daily driver) and after I started the computer GRUB Rescue randomly popped up... I used to run Linux Mint and I uninstalled it correctly, I made sure it worked and everything, restarted my computer and then come tonight, I randomly had this happen to me...


Doing these commands did nothing...
    
```
bootrec.exe /fixmbr 
bootrec.exe /fixboot
bootrec.exe /rebuildbcd
```

After I did the RebuildBCD one it said

```
Total identified Windows installations: 1
[1] F:/Windows
Add installation to boot list? Yes(Y)/No(N)/All(A): (I chose A)
```

It then said

```
The requested system device cannot be found
```


I have absolutely no idea what to do, it says this on GRUB Rescue


```
"error: no such device: 55d44464-8342-487c-16e350dedb7c"
```


I've tried doing all the generic answers I found online yet nothing has worked, I wasn't even able to get it to boot to the grub menu, so why would it go to GRUB Rescue if I uninstalled GRUB?

Here is the boot repair info that I got from Boot Repair Disk

```
[COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [/COLOR][COLOR=#666666][[/COLOR][COLOR=#000000]Boot-Info 23Nov2014[/COLOR][COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 55d44464-8342-487c-89a2-16e350dedb7c root hd0,msdos6 
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR][COLOR=#BB4444]'/boot/grub'[/COLOR]
    C/243
    ---------------------------------------------------------------------------
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 32776 of /dev/sdb1 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000365289472 bytes
64 heads, 32 sectors/track, 1907697 cylinders, total 3906963456 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,049 3,906,959,359 3,906,957,311   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8210 MB, 8210350080 bytes
255 heads, 63 sectors/track, 998 cylinders, total 16035840 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *          2,048    16,035,839    16,033,792   c W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        002605C12605B924                       ntfs       
/dev/sdb1        96E0-EE9E                              vfat       BOOT-REPAIR
/dev/zram0       687e34a2-7311-4d24-aceb-45be6a7ddf59   swap       
/dev/zram1       7f6220f9-8508-4e4c-a93b-d9ccb98496c2   swap       
/dev/zram2       61b79a77-ccfd-4b78-88a6-3174005cabd0   swap       
/dev/zram3       f523c0b4-ef86-45f0-b08b-2fdbbb493713   swap       
/dev/zram4       f19fb43c-e467-4acb-a749-9d88b2dce267   swap       
/dev/zram5       c375d309-5159-4ce0-b8c4-de5113fdf175   swap       
/dev/zram6       70ca9b38-05de-4f59-9dc4-80dd58dc47a4   swap       
/dev/zram7       9088baf6-90a6-44ad-b753-6057ca931b12   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -l /dev/disk/by-id"[/COLOR] output: [COLOR=#666666]======================[/COLOR]

total 0
lrwxrwxrwx 1 root root  9 Feb 22 01:54 ata-Optiarc_DVD_RW_AD-7240S -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 22 01:55 ata-WDC_WD20EURS-63S48Y0_WD-WCAZAK872735 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 22 01:54 ata-WDC_WD20EURS-63S48Y0_WD-WCAZAK872735-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Feb 22 01:55 usb-USB_DISK_2.0_05318C5AC51830F257FCA3B6-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 22 01:54 usb-USB_DISK_2.0_05318C5AC51830F257FCA3B6-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 22 01:55 wwn-0x50014ee2b29d47ea -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 22 01:54 wwn-0x50014ee2b29d47ea-part1 -> ../../sda1

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sda1        /media/lubuntu/002605C12605B924 fuseblk    [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,default_permissions,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sdb1        /cdrom                   vfat       [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sdb1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------

[COLOR=#AA22FF]**if **[/COLOR]loadfont /boot/grub/font.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray

menuentry [COLOR=#BB4444]"Boot-Repair-Disk session"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]==============================[/COLOR] sdb1/syslinux.cfg: [COLOR=#666666]==============================[/COLOR]

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: write error: Broken pipe
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/2010/mounts[COLOR=#666666])[/COLOR] leaked on lvs invocation. Parent PID 8534: bash
File descriptor 63 [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR]30880[COLOR=#666666]])[/COLOR] leaked on lvs invocation. Parent PID 8534: bash
  No volume groups found

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2017-02-22__01h54 [COLOR=#666666]===================[/COLOR]
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/2010/mounts[COLOR=#666666])[/COLOR] leaked on lvs invocation. Parent PID 4562: /bin/sh
No volume groups found
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/casper/vmlinuz.efi [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --

[COLOR=#666666]===================[/COLOR] os-prober:


[COLOR=#666666]===================[/COLOR] blkid:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"002605C12605B924"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"BOOT-REPAIR"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"96E0-EE9E"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/zram0: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"687e34a2-7311-4d24-aceb-45be6a7ddf59"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"7f6220f9-8508-4e4c-a93b-d9ccb98496c2"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram2: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"61b79a77-ccfd-4b78-88a6-3174005cabd0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"f523c0b4-ef86-45f0-b08b-2fdbbb493713"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram4: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"f19fb43c-e467-4acb-a749-9d88b2dce267"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"c375d309-5159-4ce0-b8c4-de5113fdf175"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram6: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"70ca9b38-05de-4f59-9dc4-80dd58dc47a4"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram7: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"9088baf6-90a6-44ad-b753-6057ca931b12"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]

ls /sys/firmware/efi/vars : VARSTORE_OCMR_TIMING_SETTINGS_NAME-93c483a1-d3fa-4e92-b437-733b2a346e23,VARSTORE_OCMR_SETTINGS_NAME-c05fba7d-7a92-49e0-bcee-233b14dca803,UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,UMAVarB.-8be4df61-93ca-11d2-aa0d-00e098032b8c,UMAVar.-8be4df61-93ca-11d2-aa0d-00e098032b8c,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,SetupHWMFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupAccFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ProfileName1-4b5b31ae-024a-412b-b2f4-5c70632605c7,PNP0604_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0604_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,new_var,NBMemoryLength-490216c0-076a-44d3-a536-ace05c90e386,MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemoryS3SaveVolLength-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveVol-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveNv-b1cfc482-4cb2-4cee-9b00-ce2579ec7186,MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LegacyDevChecksum-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpcModeBU-8be4df61-93ca-11d2-aa0d-00e098032b8c,EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15,del_var,DefaultLegacyDevOrder-3c4ead08-45ae-4315-8d15-a60eaa8caf69,DefaultBootOrder-45cf35f6-0d6e-4d04-856a-0370a5b16f53,CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConErrDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,CMOSfailflag-c89dc9c7-5105-472c-a743-b1621e142b41,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,ASUSProfile1-f0681a2d-faed-4fd7-ac2d-6afa2c0301bf,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AMIMemInfo-43387991-1223-7645-b5bb-aa7675c5c8ef,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to boot.repair@gmail.com

efibootmgr -v
BootCurrent: 0006
Timeout: 3 seconds
BootOrder: 0005,0002,0004,0006
Boot0002* CD/DVD Drive    BIOS[COLOR=#666666]([/COLOR]3,0,00[COLOR=#666666])[/COLOR]P5: Optiarc DVD RW AD-7240S   .
Boot0004* Hard Drive    BIOS[COLOR=#666666]([/COLOR]2,0,00[COLOR=#666666])[/COLOR]WD My Book 111D 1049.
Boot0005* Removable Drive    BIOS[COLOR=#666666]([/COLOR]1,0,00[COLOR=#666666])[/COLOR]WD SES Device 1049.
Boot0006* UEFI: USB DISK 2.0 0119    ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]16,2[COLOR=#666666])[/COLOR]USB[COLOR=#666666]([/COLOR]3,0[COLOR=#666666])[/COLOR]HD[COLOR=#666666]([/COLOR]1,800,f4a800,6f0f8b38[COLOR=#666666])[/COLOR]
[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
Unusual EFI: Please report this message to boot.repair@gmail.com
BIOS is EFI-compatible, and is setup in EFI-mode [COLOR=#AA22FF]**for **[/COLOR]this live-session.
SecureBoot maybe enabled. [COLOR=#666666]([/COLOR]maybe sec-boot, Please report this message to boot.repair@gmail.com[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/lubuntu/002605C12605B924.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: WD My Book 111D [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 2000GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2000GB  2000GB  primary  ntfs         boot


Model: USB DISK 2.0 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 8210MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  8210MB  8209MB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


                                                                          
Error: /dev/zram4: unrecognised disk label


                                                                          
Error: /dev/zram5: unrecognised disk label


                                                                          
Error: /dev/zram6: unrecognised disk label


                                                                          
Error: /dev/zram7: unrecognised disk [COLOR=#B8860B]label[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:512:msdos:WD My Book 111D;
1:1049kB:2000GB:2000GB:ntfs::boot;

BYT;
/dev/sdb:8210MB:scsi:512:512:msdos:USB DISK 2.0;
1:1049kB:8210MB:8209MB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


                                                                          
Error: /dev/zram4: unrecognised disk label


                                                                          
Error: /dev/zram5: unrecognised disk label


                                                                          
Error: /dev/zram6: unrecognised disk label


                                                                          
Error: /dev/zram7: unrecognised disk [COLOR=#B8860B]label[/COLOR]


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sdb1 on /cdrom [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/firmware/efi/efivars [COLOR=#AA22FF]type [/COLOR]efivarfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]lubuntu[COLOR=#666666])[/COLOR]
/dev/sda1 on /media/lubuntu/002605C12605B924 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,default_permissions,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hidraw6 hidraw7 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhci vhost-net watchdog zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  20 00 40 00 01 08 00 00  |........ .@.....|
00000020  00 00 00 00 80 00 80 00  fe 6f df e8 00 00 00 00  |.........o......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  24 b9 05 26 c1 05 26 00  |........[COLOR=#B8860B]$.[/COLOR].&..&.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 fe 01 90 90 66 60 1e  |.............f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk [COLOR=#AA22FF]read [/COLOR]error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.9G  6.4M  7.9G   1% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  1.3M  1.6G   1% /run
/dev/sdb1      vfat       7.7G  614M  7.1G   8% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G  8.0K  7.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      7.9G     0  7.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    1.9T  1.7T  136G  93% /media/lubuntu/002605C12605B924

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 2000.4 GB, 2000365289472 bytes
64 heads, 32 sectors/track, 1907697 cylinders, total 3906963456 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x8e8be90e

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2049  3906959359  1953478655+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8210 MB, 8210350080 bytes
255 heads, 63 sectors/track, 998 cylinders, total 16035840 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x6f0f8b38

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    16035839     8016896    c  W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]


No OS or WinEFI [COLOR=#B8860B]system[/COLOR]

[COLOR=#666666]===================[/COLOR] Recommended repair [COLOR=#000000]The default repair of the Boot-Repair utility will not act on the boot.[/COLOR]
```



Please help me! It's 2:29AM as I'm typing this and I'm so stressed ;-;

---

### Post by howefield on 2017-02-22
Thread moved to the "*Windows*" forum.

---

### Post by mew351 on 2017-02-22
> **howefield said:**
> Thread moved to the "*Windows*" forum.
Oops sorry!

---

