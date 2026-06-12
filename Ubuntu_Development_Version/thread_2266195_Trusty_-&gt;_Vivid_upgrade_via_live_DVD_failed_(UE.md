---
title: "Trusty -&gt; Vivid upgrade via live DVD failed (UEFI dual-boot)"
date: 2015-02-20
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-02-20
Let the fun begin, thanks ***ventrical*** :guitar:

Now that I have a UEFI box to do some testing on I decided to try stuff I'd never try in the real world. During 14.04.2 testing I set up a Win 8.1 + Trusty dual-boot with only minor issues:

[http://ubuntuforums.org/showthread.php?t=2264348](http://ubuntuforums.org/showthread.php?t=2264348)

Then last night I decided to try the upgrade option offered by the live DVD:

[ATTACH=CONFIG]260111[/ATTACH]

I quickly got this error warning:

[ATTACH=CONFIG]260112[/ATTACH]

But that didn't altogether surprise me (or concern me since an /EFI/boot partition did exist) so I proceeded and got the obligatory format warning:

[ATTACH=CONFIG]260113[/ATTACH]

Then things started getting ugly with this error warning:

[ATTACH=CONFIG]260114[/ATTACH]

I pondered that a bit .................. should I click on Go back or Continue? I clicked on Continue expecting the upgrade/installation to complete but with a broken /EFI/boot which i figured would be fun to try and fix - yes, my idea of fun is strange - but the upgrade/installation didn't run long until it was obvious ubiquity had frozen:

[ATTACH=CONFIG]260115[/ATTACH] 

So I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1423830](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1423830)

Any thoughts at all????????????????

I'm stumped for sure :-k

---

### Post by grahammechanical on 2015-02-20
How did sda2 get there? Did you create it especially? Or did the Windows installer create it? Can you show us what is in it?

It is clear that Ubiquity did not recognise sda2 as a legitimate efi boot partition. This is what Boot Repair reported one user having in their efi boot partition. From what I have seen peering into various Boot Repair reports it is fairly typical

> File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

Source:

[http://ubuntuforums.org/showthread.php?t=2265865](http://ubuntuforums.org/showthread.php?t=2265865)

Regards.

---

### Post by ventrical on 2015-02-21
@knoob

  Already been there , done that.  ummm .. umm .. um... you had the solution there from oldfred in another forum.

 I'll look in a bit if you don't already have it :)

regards..

---

### Post by kansasnoob on 2015-02-21
> **ventrical said:**
> @knoob

  Already been there , done that.  ummm .. umm .. um... you had the solution there from oldfred in another forum.

 I'll look in a bit if you don't already have it :)

regards..

So I'm guessing that the /UEFI/boot partition should be unmounted before proceeding? If so shouldn't the installer just do that?

---

### Post by ventrical on 2015-02-22
> **kansasnoob said:**
> So I'm guessing that the /UEFI/boot partition should be unmounted before proceeding? If so shouldn't the installer just do that?

 I chose both options and they both broke the system, gparted would not work. I would assume that the installer would know what to do. I think that  it is part of why we are still doing these tests well into 15.04 and previous 14.04.2. This is partly a Windows installer bug but mostly an Ubuntu Ubiquity/gparted bug. For the NEW_USER it has become a nightmare ... so we have to keep chipping away at it.

The test case is always that:

 Windows be installed first in UEFI mode.

Ubuntu is next installed in UEFI mode where Ubiquity should detect the Windows bootloader , offer to resize the partition in an 'alongside' scenario and successfully install GRuB and the UEFI shims required without breaking the  GRub routine..

On a hdd larger than 2TB (3TB) one has to choose 'extend' from the Windows 8,10 installer. Xubuntu will detect Windows bootloader and install correctly and then reboot into GRub ONCE. It's after you shutdown your PC and then restart it is where things start to go south. On the newer UEFI it will show two identical ubuntu boot entries and if you use efibootmgr to switch the boot priority it will also not work. It will also not work on more recent Intel motherboards as I get errors telling be that the efi shell hasn't enough memory.

Regards..

---

### Post by kansasnoob on 2015-02-22
I replaced that broken/failed upgrade OS with a fresh install of Precise using the Something else option and it worked almost flawlessly. The *[COLOR="#FF0000"]almost[/COLOR]* comes into play because Windows did not exist in the grub menu, but Boot Repair fixed that easily.

Next up is using ubiquity to upgrade Precise to Trusty, then Trusty to Utopic, and then Utopic to Vivid. All of which will go flawlessly, eh?

The installer team is really, really going to hate me now :biggrin:

---

### Post by kansasnoob on 2015-02-22
Basically same issue with Precise -> 14.04.2. I selected Upgrade:

[ATTACH=CONFIG]260147[/ATTACH]

Then the same error warning:

[ATTACH=CONFIG]260148[/ATTACH]

But this time I clicked on Go back which automatically took me to the advanced partitioning screen (you can see there that an EFI partition does exist):

[ATTACH=CONFIG]260149[/ATTACH]

But I knew that manual partitioning would work so I clicked on Back and selected Erase 12.04.5:

[ATTACH=CONFIG]260150[/ATTACH]

Then I was warned what would actually happen:

[ATTACH=CONFIG]260151[/ATTACH]

It looked good so I went for it and things worked very, very well. No problem at all with grub-efi this time, Windows was recognized and there was no bloat requiring a manual edit of grub configuration.

So it looks like only the Upgrade option fails to recognize the /EFI/boot partition properly.

Right now I'm going for a Windows + Trusty + Utopic multi-boot to see how grub-efi handles that :guitar:

---

### Post by kansasnoob on 2015-02-22
That triple-boot went off mostly without a hitch. I'd first selected upgrade just to be sure it was borked in Utopic as well:

[ATTACH=CONFIG]260158[/ATTACH]

But this time I decided to proceed a bit further before quitting or going back:

[ATTACH=CONFIG]260155[/ATTACH]

So after going back I chose alongside:

[ATTACH=CONFIG]260156[/ATTACH]

And gave the new install just a bit of room:

[ATTACH=CONFIG]260157[/ATTACH]

The only problem is that only the new Utopic install and Windows appear in the grub menu, and update-grub doesn't pick it up either:

```
lance@lance-INTEL-desktop:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found linux image: /boot/vmlinuz-3.16.0-23-generic
Found initrd image: /boot/initrd.img-3.16.0-23-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
done

```

Now what surprises me is this:

```
lance@lance-INTEL-desktop:~$ apt-cache policy grub-efi
grub-efi:
  Installed: (none)
  Candidate: 2.02~beta2-15
  Version table:
     2.02~beta2-15 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages

```

I need to do some more reading of **[COLOR="#800080"]oldfred[/COLOR]**'s excellent thread :D

Oh, you can see Trusty is still there:

```
lance@lance-INTEL-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD2500AAKX-3 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  316MB   315MB   ntfs            Basic data partition          hidden, diag
 2      316MB   420MB   105MB   fat32           EFI system partition          boot, esp
 3      420MB   555MB   134MB                   Microsoft reserved partition  msftres
 4      555MB   63.5GB  63.0GB  ntfs            Basic data partition          msftdata
**[COLOR="#FF0000"] 5      63.5GB  217GB   154GB   ext4[/COLOR]**
 7      217GB   248GB   30.7GB  ext4
 6      248GB   250GB   2072MB  linux-swap(v1)

```

I'd bet Boot Repair will fix this but I'm definitely going to take some time to read the boot info summary.

EDIT: Boot Repair made things worse this time, but with Vivid Beta 1 coming out next week I moved back to a Something else install with Vivid. In case someone gets curious here's the post-repair boot info link:

[http://paste.ubuntu.com/10360792/](http://paste.ubuntu.com/10360792/)

Oh I figured out the proper package name is grub-efi-amd64 which makes sense. And both the most recent Ubuntu install and Windows booted OK from the BIOS boot menu so I know it's just a matter of physically fixing /EFI/boot. What a learning curve!

---

### Post by ventrical on 2015-02-22
> **kansasnoob said:**
> 
I need to do some more reading of **[COLOR=#800080]oldfred[/COLOR]**'s excellent thread :D

I'd bet Boot Repair will fix this but I'm definitely going to take some time to read the boot info summary.

This is about where I am at with this also.

Regards..

---

### Post by kansasnoob on 2015-02-22
> **ventrical said:**
> This is about where I am at with this also.

Regards..

There's a whole lot to wrap my mind around. I can pretty much assure you that I won't be setting up any mega-multi-boot UEFI systems in the near future ;)

---

### Post by kansasnoob on 2015-02-22
OK this Vivid Something else install landed me in the same place as before:

[http://ubuntuforums.org/showthread.php?t=2264348](http://ubuntuforums.org/showthread.php?t=2264348)

Required running Boot Repair first and then following **[COLOR="#800080"]oldfred[/COLOR]**'s instructions:

[http://ubuntuforums.org/showthread.php?t=2264348&p=13223803#post13223803](http://ubuntuforums.org/showthread.php?t=2264348&p=13223803#post13223803)

Just trying to follow those instructions wouldn't work until after I'd run Boot Repair!!!!

But Trusty worked beautifully and Utopic seemed fairly good (just some grub menu bloat) so I'm running through one more Utopic Something else install for comparison.

Then it's proabably time to take a break before Beta 1 testing.

---

### Post by kansasnoob on 2015-02-22
Erase Vivid (leaving Windows alone) and installing Utopic worked fine, of course Trusty (14.04.2) had also worked fine. No tweaks needed and the grub menu is nice and neat:

[ATTACH=CONFIG]260162[/ATTACH]

Even Precise (12.04.5) worked great but had a bloated grub menu:

[ATTACH=CONFIG]260163[/ATTACH]

So Vivid may have an /EFI/boot problem that's also affected Trusty during an alongside install test - that has to be a bug, but I need to tackle my learning curve before I can really follow up on that. It may even be dependent on what method is used to install.

Trusty, Utopic, and Vivid all have the /EFI/boot partition not recognized during upgrade via iso image bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1423830](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1423830)

---

### Post by ventrical on 2015-02-23
I just wanted to see if this copy will work. I am working on a problem with new 3TB hdd in UEFI mode. Here is a text file that bootrepair generated.

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi.backup 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Vivid Vervet (development branch) 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>........G.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 2061992 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sda2         616,448       821,247       204,800 EFI System partition
/dev/sda3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,083,392 2,937,936,091 2,936,852,700 Data partition (Windows/Linux)
/dev/sda5   2,937,937,920 2,606,039,039  -331,898,880 Data partition (Linux)
/dev/sda6   2,606,039,040 2,639,306,751    33,267,712 Swap partition (Linux)

/dev/sda4 overlaps with /dev/sda6
Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1.9 GiB, 2002747392 bytes, 3911616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,909,347     3,909,286   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CCD4AD8AD4AD76FC                       ntfs       Recovery
/dev/sda2        16AF-0B2F                              vfat       
/dev/sda3                                                          
/dev/sda4        16C4DD74C4DD5719                       ntfs       
/dev/sda5        1dcdb015-7a86-4309-b880-8dac07e1af5c   ext4       
/dev/sda6        18bd1c09-e466-4b66-a1ec-8df54294512c   swap       
/dev/sdb1        E839-755B                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 24 00:05 ata-ST3000DM001-1CH166_W1F5QR7M -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 24 00:08 ata-ST3000DM001-1CH166_W1F5QR7M-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 24 00:08 ata-ST3000DM001-1CH166_W1F5QR7M-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 24 00:05 ata-ST3000DM001-1CH166_W1F5QR7M-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 24 00:08 ata-ST3000DM001-1CH166_W1F5QR7M-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Feb 24 00:08 ata-ST3000DM001-1CH166_W1F5QR7M-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 24 00:05 ata-ST3000DM001-1CH166_W1F5QR7M-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Feb 23 23:41 ata-TSSTcorpDVD-ROM_TS-H353C_R60568BZ939222 -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 24 00:05 usb-_USB_Flash_Memory_001D92AD6C3BC8C12398014E-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 24 00:05 usb-_USB_Flash_Memory_001D92AD6C3BC8C12398014E-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 24 00:05 wwn-0x5000c5007c687c9a -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 24 00:08 wwn-0x5000c5007c687c9a-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 24 00:08 wwn-0x5000c5007c687c9a-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 24 00:05 wwn-0x5000c5007c687c9a-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 24 00:08 wwn-0x5000c5007c687c9a-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Feb 24 00:08 wwn-0x5000c5007c687c9a-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 24 00:05 wwn-0x5000c5007c687c9a-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  1dcdb015-7a86-4309-b880-8dac07e1af5c
else
  search --no-floppy --fs-uuid --set=root 1dcdb015-7a86-4309-b880-8dac07e1af5c
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1dcdb015-7a86-4309-b880-8dac07e1af5c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  1dcdb015-7a86-4309-b880-8dac07e1af5c
    else
      search --no-floppy --fs-uuid --set=root 1dcdb015-7a86-4309-b880-8dac07e1af5c
    fi
    linux    /boot/vmlinuz-3.18.0-12-generic.efi.signed root=UUID=1dcdb015-7a86-4309-b880-8dac07e1af5c ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.18.0-12-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1dcdb015-7a86-4309-b880-8dac07e1af5c' {
    menuentry 'Ubuntu, with Linux 3.18.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-12-generic-advanced-1dcdb015-7a86-4309-b880-8dac07e1af5c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  1dcdb015-7a86-4309-b880-8dac07e1af5c
        else
          search --no-floppy --fs-uuid --set=root 1dcdb015-7a86-4309-b880-8dac07e1af5c
        fi
        echo    'Loading Linux 3.18.0-12-generic ...'
        linux    /boot/vmlinuz-3.18.0-12-generic.efi.signed root=UUID=1dcdb015-7a86-4309-b880-8dac07e1af5c ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.18.0-12-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-12-generic-init-systemd-1dcdb015-7a86-4309-b880-8dac07e1af5c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  1dcdb015-7a86-4309-b880-8dac07e1af5c
        else
          search --no-floppy --fs-uuid --set=root 1dcdb015-7a86-4309-b880-8dac07e1af5c
        fi
        echo    'Loading Linux 3.18.0-12-generic ...'
        linux    /boot/vmlinuz-3.18.0-12-generic.efi.signed root=UUID=1dcdb015-7a86-4309-b880-8dac07e1af5c ro  quiet splash $vt_handoff init=/lib/systemd/systemd
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.18.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-12-generic-recovery-1dcdb015-7a86-4309-b880-8dac07e1af5c' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  1dcdb015-7a86-4309-b880-8dac07e1af5c
        else
          search --no-floppy --fs-uuid --set=root 1dcdb015-7a86-4309-b880-8dac07e1af5c
        fi
        echo    'Loading Linux 3.18.0-12-generic ...'
        linux    /boot/vmlinuz-3.18.0-12-generic.efi.signed root=UUID=1dcdb015-7a86-4309-b880-8dac07e1af5c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-16AF-0B2F' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  16AF-0B2F
    else
      search --no-floppy --fs-uuid --set=root 16AF-0B2F
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=1dcdb015-7a86-4309-b880-8dac07e1af5c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=16AF-0B2F  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda6 during installation
UUID=18bd1c09-e466-4b66-a1ec-8df54294512c none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu GNOME without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu GNOME" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
# search path for the c32 support libraries (libcom32, libutil etc.)
path
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  not a COM32/COM32R module
 syslinux/gfxboot.c32               :  not a COM32/COM32R module
 syslinux/ldlinux.c32               :  not a COM32/COM32R module
 syslinux/libcom32.c32              :  not a COM32/COM32R module
 syslinux/libutil.c32               :  not a COM32/COM32R module
 syslinux/vesamenu.c32              :  not a COM32/COM32R module

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5567/mounts) leaked on lvs invocation. Parent PID 16873: bash
File descriptor 63 (pipe:[52382]) leaked on lvs invocation. Parent PID 16873: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-02-24__00h05 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in live-session (Ubuntu Vivid Vervet (development branch), vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
ntfs-3g-mount: bad mount point /mnt/boot-sav/sda1: No such file or directory
mount -r /dev/sda1 : Error code 21
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4
ntfs-3g-mount: bad mount point /mnt/boot-sav/sda4: No such file or directory
mount -r /dev/sda4 : Error code 21
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
mount: mount point /mnt/boot-sav/sda5 does not exist
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: mount point /mnt/boot-sav/sda5 does not exist
mount -r /dev/sda5 : Error code 32

=================== os-prober:
/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda5:Ubuntu Vivid Vervet (development branch) (15.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="Recovery" UUID="CCD4AD8AD4AD76FC" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e3c17cf5-ca51-4d96-924c-dae83f8e9b12"
/dev/sda2: UUID="16AF-0B2F" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="916eaa03-02b7-43a9-a5d0-e89a13c8c24a"
/dev/sda4: UUID="16C4DD74C4DD5719" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="5e157661-14f0-49e3-a57b-378d7adf0099"
/dev/sda5: UUID="1dcdb015-7a86-4309-b880-8dac07e1af5c" TYPE="ext4" PARTUUID="4b191940-2875-463a-8a62-d4a6decadc2b"
/dev/sdb1: UUID="E839-755B" TYPE="vfat" PARTUUID="00057987-01"
/dev/loop0: TYPE="squashfs"
/dev/sda6: UUID="18bd1c09-e466-4b66-a1ec-8df54294512c" TYPE="swap" PARTUUID="7dc931f8-00e8-4118-8b4a-a37ce7817b1c"
/dev/sda3: PARTLABEL="Microsoft reserved partition" PARTUUID="71a459b7-cdc0-43ad-a167-db12da6d1cca"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
ntfs-3g-mount: bad mount point /mnt/boot-sav/sda1: No such file or directory
mount -r /dev/sda1 : Error code 21
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4
ntfs-3g-mount: bad mount point /mnt/boot-sav/sda4: No such file or directory
mount -r /dev/sda4 : Error code 21
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
mount: mount point /mnt/boot-sav/sda5 does not exist
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: mount point /mnt/boot-sav/sda5 does not exist
mount -r /dev/sda5 : Error code 32
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
sda2 is Read-only or full
mkdir: cannot create directory ‘/mnt/boot-sav’: Read-only file system
sda5 is Read-only or full
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
ls: cannot access /mnt/boot-sav/sda1/: No such file or directory
Presence of EFI/Microsoft file detected: /mnt/EFI/Microsoft/Boot/bootmgfw.efi
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda4/: No such file or directory
ls: cannot access /mnt/boot-sav/sda5/: No such file or directory

=================== efibootmgr -v
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0000,0001,0002,000E,0011,000B
Boot0000* SATA4:TSSTcorpDVD-ROM TS-H353C    BIOS(10,0,00)
Boot0001* SATA1:ST3000DM001-1CH166          BIOS(11,0,00)
Boot0002*  USB Flash Memory1.00    BIOS(15,0,00)
Boot0004       BIOS(15,0,00)
Boot000B* UEFI: Built-in EFI Shell     Vendor(5023b95c-db26-429b-a648-bd47664c8012,)AMBO
Boot000E* Windows Boot Manager    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(EFIMicrosoftBootbootmgfw.efi)
Boot0011* UEFI:  USB Flash Memory1.00    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,3e,3ba6a6,00057987)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  316MB   315MB   ntfs            Basic data partition          hidden, diag
2      316MB   420MB   105MB   fat32           EFI system partition          boot, esp
3      420MB   555MB   134MB                   Microsoft reserved partition  msftres
4      555MB   1504GB  1504GB  ntfs            Basic data partition          msftdata
5      1504GB  2984GB  1479GB  ext4
6      2984GB  3001GB  17.0GB  linux-swap(v1)


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 2003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  2002MB  2002MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:4096:gpt:ATA ST3000DM001-1CH1:;
1:1049kB:316MB:315MB:ntfs:Basic data partition:hidden, diag;
2:316MB:420MB:105MB:fat32:EFI system partition:boot, esp;
3:420MB:555MB:134MB::Microsoft reserved partition:msftres;
4:555MB:1504GB:1504GB:ntfs:Basic data partition:msftdata;
5:1504GB:2984GB:1479GB:ext4::;
6:2984GB:3001GB:17.0GB:linux-swap(v1)::;

BYT;
/dev/sdb:2003MB:scsi:512:512:msdos: USB Flash Memory:;
1:31.7kB:2002MB:2002MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL            UUID
sda   disk            2.7T          ST3000DM001-1CH1
sda1  part ntfs       300M Recovery                  CCD4AD8AD4AD76FC
sda2  part vfat       100M                           16AF-0B2F
sda3  part            128M
sda4  part ntfs       1.4T                           16C4DD74C4DD5719
sda5  part ext4       1.4T                           1dcdb015-7a86-4309-b880-8dac07e1af5c
sda6  part swap      15.9G                           18bd1c09-e466-4b66-a1ec-8df54294512c
sdb   disk            1.9G          USB Flash Memory
sdb1  part vfat       1.9G                           E839-755B
sr0   rom            1024M          DVD-ROM TS-H353C
loop0 loop squashfs 957.9M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
sda2     1  0  0         /mnt
sda3     1  0  0
sda4     1  0  0
sda5     1  0  0
sda6     1  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,nodev,noexec,nosuid)
sysfs on /sys type sysfs (rw,nodev,noexec,nosuid)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,nodev,noexec,nosuid,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,nodev,noexec,nosuid,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu-gnome)
/dev/sda2 on /mnt type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri dvd ecryptfs fb0 fd full fuse hpet input kmsg kvm log lp0 mapper mcelog mei0 mem memory_bandwidth net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter watchdog watchdog0 zero
ls /dev/mapper:  control
ls: cannot access /mnt/boot-sav/sda1: No such file or directory

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 09 00 00 00 00 00  |........._......|
00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|
00000040  f6 00 00 00 01 00 00 00  fc 76 ad d4 8a ad d4 cc  |.........v......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 2f 0b af 16 4e  4f 20 4e 41 4d 45 20 20  |..)/...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200
ls: cannot access /mnt/boot-sav/sda4: No such file or directory

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 10 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  d8 d0 0c af 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  19 57 dd c4 74 dd c4 16  |.........W..t...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200
ls: cannot access /mnt/boot-sav/sda5: No such file or directory

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   7.8G  182M  7.6G   3% /
udev           devtmpfs  7.8G  4.0K  7.8G   1% /dev
tmpfs          tmpfs     1.6G 1016K  1.6G   1% /run
/dev/sdb1      vfat      1.9G 1004M  902M  53% /cdrom
/dev/loop0     squashfs  958M  958M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     7.8G   12K  7.8G   1% /tmp
none           tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     7.8G   84K  7.8G   1% /run/shm
none           tmpfs     100M     0  100M   0% /run/user
/dev/sda2      vfat       96M   29M   68M  30% /mnt

=================== fdisk -l:

Disk /dev/loop0: 957.9 MiB, 1004392448 bytes, 1961704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DE5A0386-579E-4CFA-AA7A-967CFCCAE898

Device          Start        End    Sectors  Size Type
/dev/sda1        2048     616447     614400  300M Windows recovery environment
/dev/sda2      616448     821247     204800  100M EFI System
/dev/sda3      821248    1083391     262144  128M Microsoft reserved
/dev/sda4     1083392 2937936091 2936852700  1.4T Microsoft basic data
/dev/sda5  2937937920 5827264511 2889326592  1.4T Linux filesystem
/dev/sda6  5827264512 5860532223   33267712 15.9G Linux swap

Disk /dev/sdb: 1.9 GiB, 2002747392 bytes, 3911616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00057987

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *       62 3909347 3909286  1.9G  c W95 FAT32 (LBA)


No OS or WinEFI system

(zenity:10650): GLib-GObject-WARNING **: The property GtkButton:use-stock is deprecated and shouldn't be used anymore. It will be removed in a future version.

(zenity:10650): GLib-GObject-WARNING **: The property GtkSettings:gtk-button-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(zenity:10650): GLib-GObject-WARNING **: The property GtkImage:stock is deprecated and shouldn't be used anymore. It will be removed in a future version.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems



(zenity:10674): GLib-GObject-WARNING **: The property GtkButton:use-stock is deprecated and shouldn't be used anymore. It will be removed in a future version.

(zenity:10674): GLib-GObject-WARNING **: The property GtkSettings:gtk-button-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(zenity:10674): GLib-GObject-WARNING **: The property GtkImage:stock is deprecated and shouldn't be used anymore. It will be removed in a future version.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/sda1
fsck from util-linux 2.25.2

fsck -fyM /dev/sda2
fsck from util-linux 2.25.2
fsck.fat 3.0.27 (2014-11-12)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
Automatically removing dirty bit.
/EFI/ubuntu  and
/EFI/Microsoft/Boot/BCD
share clusters.
Truncating second to 0 bytes.
/EFI/Microsoft/Boot/BCD
File size is 36864 bytes, cluster chain length is 29696 bytes.
Truncating file to 29696 bytes.
/EFI/ubuntu
Has a large number of bad entries. (90/91)
Not dropping it in auto-mode.
/EFI/ubuntu/\FF\FF\FF\FF\FF\FF\FF\FF.
Bad short file name (\FF\FF\FF\FF\FF\FF\FF\FF.).
Auto-renaming it.
Renamed to FSCK0000.000
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.001
/EFI/ubuntu/2
Bad short file name (2).
Auto-renaming it.
Renamed to FSCK0000.002
/EFI/ubuntu/c
Bad short file name (c).
Auto-renaming it.
Renamed to FSCK0000.003
/EFI/ubuntu/\C8\FF\FF\FF  Bad short file name (\C8\FF\FF\FF).
Auto-renaming it.
Renamed to FSCK0000.004
/EFI/ubuntu/u
Bad short file name (u).
Auto-renaming it.
Renamed to FSCK0000.005
/EFI/ubuntu/9o\C49\BCG\D0.
Bad short file name (9o\C49\BCG\D0.).
Auto-renaming it.
Renamed to FSCK0000.006
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.007
/EFI/ubuntu/8
Bad short file name (8).
Auto-renaming it.
Renamed to FSCK0000.008
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.009
/EFI/ubuntu/z211;\BCG\D0.
Bad short file name (z211;\BCG\D0.).
Auto-renaming it.
Renamed to FSCK0000.010
/EFI/ubuntu/4
Bad short file name (4).
Auto-renaming it.
Renamed to FSCK0000.011
/EFI/ubuntu/-d43d7e9.9b8
Bad short file name (-d43d7e9.9b8).
Auto-renaming it.
Renamed to FSCK0000.012
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.013
/EFI/ubuntu/h
Bad short file name (h).
Auto-renaming it.
Renamed to FSCK0000.014
/EFI/ubuntu/Descript.ion
Bad short file name (Descript.ion).
Auto-renaming it.
Renamed to FSCK0000.015
/EFI/ubuntu/t
Bad short file name (t).
Auto-renaming it.
Renamed to FSCK0000.016
/EFI/ubuntu/`h
Bad short file name (`h).
Auto-renaming it.
Renamed to FSCK0000.017
/EFI/ubuntu/1e4-95d6.-80
Bad short file name (1e4-95d6.-80).
Auto-renaming it.
Renamed to FSCK0000.018
/EFI/ubuntu/y\C4Y;\BCG\D0.
Bad short file name (y\C4Y;\BCG\D0.).
Auto-renaming it.
Renamed to FSCK0000.019
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.020
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.021
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.022
/EFI/ubuntu/\E8\FF\FF\FFlf
Bad short file name (\E8\FF\FF\FFlf).
Auto-renaming it.
Renamed to FSCK0000.023
/EFI/ubuntu/9
Bad short file name (9).
Auto-renaming it.
Renamed to FSCK0000.024
/EFI/ubuntu/\C0\FF\FF\FF
Bad short file name (\C0\FF\FF\FF).
Auto-renaming it.
Renamed to FSCK0000.025
/EFI/ubuntu/
Bad short file name ( ).
Auto-renaming it.
Renamed to FSCK0000.026
/EFI/ubuntu/\FF\FF\FF\FF\FF\FF\FF\FF.
Bad short file name (\FF\FF\FF\FF\FF\FF\FF\FF.).
Auto-renaming it.
Renamed to FSCK0000.027
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.028
/EFI/ubuntu/Element
Bad short file name (Element).
Auto-renaming it.
Renamed to FSCK0000.029
/EFI/ubuntu/b
Bad short file name (b).
Auto-renaming it.
Renamed to FSCK0000.030
/EFI/ubuntu/4
Bad short file name (4).
Auto-renaming it.
Renamed to FSCK0000.031
/EFI/ubuntu/e
Bad short file name (e).
Auto-renaming it.
Renamed to FSCK0000.032
/EFI/ubuntu/-
Bad short file name (-).
Auto-renaming it.
Renamed to FSCK0000.033
/EFI/ubuntu/9
Bad short file name (9).
Auto-renaming it.
Renamed to FSCK0000.034
/EFI/ubuntu/a
Bad short file name (a).
Auto-renaming it.
Renamed to FSCK0000.035
/EFI/ubuntu/e
Bad short file name (e).
Auto-renaming it.
Renamed to FSCK0000.036
/EFI/ubuntu/5
Bad short file name (5).
Auto-renaming it.
Renamed to FSCK0000.037
/EFI/ubuntu/8
Bad short file name (8).
Auto-renaming it.
Renamed to FSCK0000.038
/EFI/ubuntu/}
Bad short file name (}).
Auto-renaming it.
Renamed to FSCK0000.039
/EFI/ubuntu/-
Bad short file name (-).
Auto-renaming it.
Renamed to FSCK0000.040
/EFI/ubuntu/0
Bad short file name (0).
Auto-renaming it.
Renamed to FSCK0000.041
/EFI/ubuntu/8
Bad short file name (8).
Auto-renaming it.
Renamed to FSCK0000.042
/EFI/ubuntu/2
Bad short file name (2).
Auto-renaming it.
Renamed to FSCK0000.043
/EFI/ubuntu/{
Bad short file name ({).
Auto-renaming it.
Renamed to FSCK0000.044
/EFI/ubuntu/1
Bad short file name (1).
Auto-renaming it.
Renamed to FSCK0000.045
/EFI/ubuntu/b
Bad short file name (b).
Auto-renaming it.
Renamed to FSCK0000.046
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.047
/EFI/ubuntu/h
Bad short file name (h).
Auto-renaming it.
Renamed to FSCK0000.048
/EFI/ubuntu/\D8\FF\FF\FFvk
Bad short file name (\D8\FF\FF\FFvk).
Auto-renaming it.
Renamed to FSCK0000.049
/EFI/ubuntu/U
Bad short file name (U).
Auto-renaming it.
Renamed to FSCK0000.050
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.051
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.052
/EFI/ubuntu/z211;\BCG\D0.
Bad short file name (z211;\BCG\D0.).
Auto-renaming it.
Renamed to FSCK0000.053
/EFI/ubuntu/
Bad short file name ().
Auto-renaming it.
Renamed to FSCK0000.054
/EFI/ubuntu/\E0\FF\FF\FFvk
Bad short file name (\E0\FF\FF\FFvk).
Auto-renaming it.
Renamed to FSCK0000.055
/EFI/ubuntu/\C8\FF\FF\FFU
Bad short file name (\C8\FF\FF\FFU).
Auto-renaming it.
Renamed to FSCK0000.056
/EFI/ubuntu/H
Bad short file name (H).
Auto-renaming it.
Renamed to FSCK0000.057
/EFI/ubuntu/hbin
Bad short file name (hbin).
Auto-renaming it.
Renamed to FSCK0000.058
/EFI/ubuntu/210\FD\FF\FF{
Bad short file name (210\FD\FF\FF{).
Auto-renaming it.
Renamed to FSCK0000.059
/EFI/ubuntu/-
Bad short file name (-).
Auto-renaming it.
Renamed to FSCK0000.060
/EFI/ubuntu/e
Bad short file name (e).
Auto-renaming it.
Renamed to FSCK0000.061
/EFI/ubuntu/2
Bad short file name (2).
Auto-renaming it.
Renamed to FSCK0000.062
/EFI/ubuntu/1
Bad short file name (1).
Auto-renaming it.
Renamed to FSCK0000.063
/EFI/ubuntu/{
Bad short file name ({).
Auto-renaming it.
Renamed to FSCK0000.064
/EFI/ubuntu/1
Bad short file name (1).
Auto-renaming it.
Renamed to FSCK0000.065
/EFI/ubuntu/e
Bad short file name (e).
Auto-renaming it.
Renamed to FSCK0000.066
/EFI/ubuntu/-
Bad short file name (-).
Auto-renaming it.
Renamed to FSCK0000.067
/EFI/ubuntu/d
Bad short file name (d).
Auto-renaming it.
Renamed to FSCK0000.068
/EFI/ubuntu/5
Bad short file name (5).
Auto-renaming it.
Renamed to FSCK0000.069
/EFI/ubuntu/4
Bad short file name (4).
Auto-renaming it.
Renamed to FSCK0000.070
/EFI/ubuntu/8
Bad short file name (8).
Auto-renaming it.
Renamed to FSCK0000.071
/EFI/ubuntu/0
Bad short file name (0).
Auto-renaming it.
Renamed to FSCK0000.072
/EFI/ubuntu/c
Bad short file name (c).
Auto-renaming it.
Renamed to FSCK0000.073
/EFI/ubuntu/c
Bad short file name (c).
Auto-renaming it.
Renamed to FSCK0000.074
/EFI/ubuntu/b
Bad short file name (b).
Auto-renaming it.
Renamed to FSCK0000.075
/EFI/ubuntu/b
Bad short file name (b).
Auto-renaming it.
Renamed to FSCK0000.076
/EFI/ubuntu/2
Bad short file name (2).
Auto-renaming it.
Renamed to FSCK0000.077
/EFI/ubuntu/d
Bad short file name (d).
Auto-renaming it.
Renamed to FSCK0000.078
/EFI/ubuntu
"." is missing. Can't fix this yet.
/EFI/ubuntu
".." is missing. Can't fix this yet.
/EFI/ubuntu/FSCK0000.000
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.001
Start cluster beyond limit (808517631 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.001
File size is 486262 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.002
Start cluster beyond limit (1852178431 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.002
File size is 222828 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.003
Start cluster beyond limit (842072064 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.004
Start cluster beyond limit (7209052 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.004
File size is 7471207 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.005
Contains a free cluster (65535). Assuming EOF.
/EFI/ubuntu/FSCK0000.005
File size is 2124654 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.006
Contains a free cluster (65535). Assuming EOF.
/EFI/ubuntu/FSCK0000.006
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.007
File size is 88 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.008
Start cluster beyond limit (1718353920 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.008
File size is 808464689 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/\D8l
Directory has non-zero size. Fixing it.
/EFI/ubuntu/\D8l
Start cluster beyond limit (1699217408 > 98305). Truncating file.
/EFI/ubuntu/Element.\A0\FF\FF
Directory has non-zero size. Fixing it.
/EFI/ubuntu/Element.\A0\FF\FF
Start does point to root directory. Deleting dir.
/EFI/ubuntu/FSCK0000.010
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.011
Start cluster beyond limit (862006580 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.011
File size is 912536889 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.012
Start cluster beyond limit (1802386265 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.012
File size is 30427068 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.013
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.013
File size is 1528 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.014
Start cluster beyond limit (11272242 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.014
File size is 11 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.015
Start cluster beyond limit (6488063 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.015
File size is 91756 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/P
Directory has non-zero size. Fixing it.
/EFI/ubuntu/P
Start cluster beyond limit (1724383232 > 98305). Truncating file.
/EFI/ubuntu/Element
Directory has non-zero size. Fixing it.
/EFI/ubuntu/Element
Start cluster beyond limit (3801205 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.016
Start cluster beyond limit (6815852 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.016
File size is 32 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/210\FF\FF\FFnk
Start cluster beyond limit (16777216 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.017
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.018
Start cluster beyond limit (2100559871 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.018
File size is 2124654 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.019
Contains a free cluster (65535). Assuming EOF.
/EFI/ubuntu/FSCK0000.019
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.020
File size is 57 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/xh
Directory has non-zero size. Fixing it.
/EFI/ubuntu/xh
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/Type
Directory has non-zero size. Fixing it.
/EFI/ubuntu/Type
Start cluster beyond limit (1203503104 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.021
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.021
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.022
Start cluster beyond limit (552293 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.022
File size is 1937010277 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.023
Start cluster beyond limit (1816526847 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.023
File size is 1076086 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.024
Start cluster beyond limit (1635215730 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.024
File size is 1701601889 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.025
Start cluster beyond limit (1835008 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.026
Start cluster beyond limit (1377535 > 98305). Truncating file.
/EFI/ubuntu/\A8\FF\FF\FFnk
Start cluster beyond limit (1745354752 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.027
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.028
Start cluster beyond limit (808517631 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.028
File size is 91756 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/\E0h
Directory has non-zero size. Fixing it.
/EFI/ubuntu/\E0h
Start cluster beyond limit (2097152 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.029
Start cluster beyond limit (3473464 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.029
File size is 2949175 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.030
Start cluster beyond limit (3735602 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.030
File size is 6553645 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.031
Start cluster beyond limit (3604603 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.031
File size is 6553657 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.032
Start cluster beyond limit (6553701 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.032
File size is 3145783 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.033
Start cluster beyond limit (3342436 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.033
File size is 3604532 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.034
Start cluster beyond limit (3604525 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.034
File size is 3145826 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.035
Start cluster beyond limit (6553656 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.035
File size is 3538992 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/Microsoft/Boot/bg-BG/bootmgfw.efi.mui  and
/EFI/ubuntu/FSCK0000.036
share clusters.
Truncating second to 69632 bytes.
/EFI/ubuntu/FSCK0000.036
File size is 6488119 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.037
Start cluster beyond limit (3211316 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.037
File size is 6422573 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.038
Start cluster beyond limit (3539046 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.038
File size is 6422585 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.039
Start cluster beyond limit (6488112 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.039
File size is 3276856 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.040
Start cluster beyond limit (2949219 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.040
File size is 6553650 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.041
Start cluster beyond limit (3735605 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.041
File size is 6422577 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.042
Start cluster beyond limit (6619193 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.042
File size is 6553653 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.043
Start cluster beyond limit (6422583 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.043
File size is 125 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.044
Start cluster beyond limit (6422578 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.044
File size is 3211309 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.045
Start cluster beyond limit (3211364 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.045
File size is 3538992 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.046
Start cluster beyond limit (1802386313 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.046
File size is 30427068 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.047
Start cluster beyond limit (4294901760 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.047
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.048
File size is 8 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/Elements.\E8\FF\FF
Directory has non-zero size. Fixing it.
/EFI/ubuntu/Elements.\E8\FF\FF
Start cluster beyond limit (1698955264 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.049
Contains a free cluster (93554). Assuming EOF.
/EFI/ubuntu/FSCK0000.049
File size is 1701994871 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/Variable.P\FF\FF
Directory has non-zero size. Fixing it.
/EFI/ubuntu/Variable.P\FF\FF
Start cluster beyond limit (917504 > 98305). Truncating file.
/EFI/ubuntu/T
Start cluster beyond limit (3801171 > 98305). Truncating file.
/EFI/ubuntu/T
File size is 2097218 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.050
Start cluster beyond limit (7471205 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.050
File size is 32 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/Microsoft/Boot/BCD  and
/EFI/ubuntu/FSCK0000.051
share clusters.
Truncating second to 0 bytes.
/EFI/ubuntu/FSCK0000.051
File size is 84090112 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/Microsoft/Boot/BOOTMGR.EFI  and
/EFI/ubuntu/FSCK0000.052
share clusters.
Truncating second to 771072 bytes.
/EFI/ubuntu/FSCK0000.052
File size is 119 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.053
Contains a free cluster (65535). Assuming EOF.
/EFI/ubuntu/FSCK0000.053
File size is 4294967295 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.054
File size is 52 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.055
Contains a free cluster (93541). Assuming EOF.
/EFI/ubuntu/FSCK0000.055
File size is 7630437 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.056
Start cluster beyond limit (4325459 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.056
File size is 2097218 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.057
Start cluster beyond limit (2097152 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.059
Start cluster beyond limit (3604528 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.059
File size is 3342392 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.060
Start cluster beyond limit (2949171 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.060
File size is 3604580 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.061
Start cluster beyond limit (3735649 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.061
File size is 3539000 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.062
Start cluster beyond limit (3604577 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.062
File size is 6488163 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.063
Start cluster beyond limit (3407925 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.063
File size is 125 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.064
Start cluster beyond limit (6422579 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.064
File size is 3211309 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.065
Start cluster beyond limit (3145782 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.065
File size is 3539046 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.066
Start cluster beyond limit (3145826 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.066
File size is 3539000 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.067
Start cluster beyond limit (2949220 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.067
File size is 2949170 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.068
Start cluster beyond limit (6356992 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.068
File size is 3473531 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.069
Start cluster beyond limit (6357041 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.069
File size is 6619185 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.070
Start cluster beyond limit (6553657 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.070
File size is 6422585 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.071
Start cluster beyond limit (3473506 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.071
File size is 6422573 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.072
Start cluster beyond limit (3670061 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.072
File size is 3211362 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.073
Start cluster beyond limit (8192049 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.073
File size is 3604579 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.074
Start cluster beyond limit (2949221 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.074
File size is 2949172 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.075
Start cluster beyond limit (3145827 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.075
File size is 3735654 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.076
Start cluster beyond limit (3342434 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.076
File size is 3670064 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
/EFI/ubuntu/FSCK0000.077
Start cluster beyond limit (3604529 > 98305). Truncating file.
/EFI/ubuntu/FSCK0000.077
File size is 3276899 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
Reclaimed 3383 unused clusters (3464192 bytes) in 4 chains.
Performing changes.
/dev/sda2: 263 files, 29341/98304 clusters

fsck -fyM /dev/sda4
fsck from util-linux 2.25.2

fsck -fyM /dev/sda5
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 160325/90292224 files (0.1% non-contiguous), 6464338/361165824 blocks
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4

Boot successfully repaired.

You can now reboot your computer.

```

I had originally installed Windows 10 in UEFI mode and then installed xubuntu 'alongside' . It initially rebooted into grub with Windows boot loader otpion and Ubuntu and it worked but after shut down it would only boot into Windows. Now xubuntu is not included in UEFI boot when I press F11 so I used boot repair and it says it is repaired and I am going down for reboot.

---

### Post by ventrical on 2015-02-23
The ubuntu UEFI entry is no where to be found with efibootmgr nor with the system UEFI Shell so I am going to erase the vivid vervet partiton and reinstall with gnome 3 in UEFI mode.

Here goes.

...

---

### Post by ventrical on 2015-02-23
Gnome3 installed seamlessly on the old partition. I shut down and it booted right into GRuB and I selected 'ubuntu' from the GRuB menu. Now this happened before with xubuntu. It booted to gGRub and I was able to run xubuntu desktop but on the Second boot it boot into Windows and I could not choose 'ubuntu' from the UEFI shell because there were two entries and it would keep rolling back to Windows.

```

ventrical@ventrical-MS-7798:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0002,000E,000B,0000,0001
Boot0000* SATA4:TSSTcorpDVD-ROM TS-H353C    BIOS(10,0,00)
Boot0001* SATA1:ST3000DM001-1CH166          BIOS(11,0,00)
Boot0002* Windows Boot Manager    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3...............
Boot0004       BIOS(15,0,00)
Boot0005* ubuntu    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\ubuntu\shimx64.efi)
Boot000B* UEFI: Built-in EFI Shell     Vendor(5023b95c-db26-429b-a648-bd47664c8012,)AMBO
Boot000E* ubuntu    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\Ubuntu\grubx64.efi)
ventrical@ventrical-MS-7798:~$ 

```

so I get 
Boot0005* ubuntu

which is active

and

Boot000E* ubuntu

which is also active. One is grub64.efi and the other the shim64.efi but If I try to shutdown and reboot it will go to Windows Tech Preview which is:

Boot0002* which is NEXT in the boot order. On my last install I tried to re-arrange the order but then lost the UEFI entries all together. So this is where I am stuck with this.

OK.. since this is testing I am going to shut down and restart and see if there has been any improvement- then probably do it all over again :)

Regards..

---

### Post by kansasnoob on 2015-02-23
> **ventrical said:**
> Gnome3 installed seamlessly on the old partition. I shut down and it booted right into GRuB and I selected 'ubuntu' from the GRuB menu. Now this happened before with xubuntu. It booted to gGRub and I was able to run xubuntu desktop but on the Second boot it boot into Windows and I could not choose 'ubuntu' from the UEFI shell because there were two entries and it would keep rolling back to Windows.

```

ventrical@ventrical-MS-7798:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0002,000E,000B,0000,0001
Boot0000* SATA4:TSSTcorpDVD-ROM TS-H353C    BIOS(10,0,00)
Boot0001* SATA1:ST3000DM001-1CH166          BIOS(11,0,00)
Boot0002* Windows Boot Manager    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3...............
Boot0004       BIOS(15,0,00)
Boot0005* ubuntu    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\ubuntu\shimx64.efi)
Boot000B* UEFI: Built-in EFI Shell     Vendor(5023b95c-db26-429b-a648-bd47664c8012,)AMBO
Boot000E* ubuntu    HD(2,96800,32000,916eaa03-02b7-43a9-a5d0-e89a13c8c24a)File(\EFI\Ubuntu\grubx64.efi)
ventrical@ventrical-MS-7798:~$ 

```

so I get 
Boot0005* ubuntu

which is active

and

Boot000E* ubuntu

which is also active. One is grub64.efi and the other the shim64.efi but If I try to shutdown and reboot it will go to Windows Tech Preview which is:

Boot0002* which is NEXT in the boot order. On my last install I tried to re-arrange the order but then lost the UEFI entries all together. So this is where I am stuck with this.

OK.. since this is testing I am going to shut down and restart and see if there has been any improvement- then probably do it all over again :)

Regards..

What some people consider fun, eh? I always seem to be able to get the boot issues cured if I read olfred's thread long enough and use just the right formula, but I still don't understand 90% of what I'm doing.

One thing I'm fairly well convinced of is that building a super-mega-multi-boot testing box with UEFI enabled would be a ridiculous waste of time. But we should be able to perform enough tests and report enough bugs to eventually make simple dual-boots safe and fairly safe.

---

### Post by ventrical on 2015-02-24
That was my original take a while back . That basically UEFI was a waste of time (even reported by oldfred <if it ain't broke - don't fix it> but it  is new technology that we all have to get used to .. so now and again it helps to iron out the bugs, especially in the spirit of helping noobs.

---

