---
title: "Booting Problem"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Alxl on 2012-03-31
On my desktop I have windows XP (used rarely now), Ubuntu 10.04  and PP.

PP worked very well and I had no real problem till now. But I ran Ubuntu Tweak which apparently removed the latest kernel. 

The result was that at boot,   it said that I need to load kernel first.  So I booted from a live USB and reinstalled Grub where it was all the time on Ubuntu 10.04.

Now I can boot into Ubuntu 10.04 but cannot boot into XP or PP.  So I am now using Ubuntu 10.04 to post this

I am  just an average  computer user and would appreciate suggestions. Is there any way to reinstall the kernel?  When I try to boot XP it says that there is no such device.

---

### Post by Alxl on 2012-03-31
I ran a simple sudo update-grub  and PP came back.

But XP is still missing.

Any suggestion ?

---

### Post by Alxl on 2012-03-31
In PP I did 
:~$ sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-21-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-21-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sda2
done


no mention of XP  on  /dev/sda1   .

---

### Post by Baldrick_NZ on 2012-03-31
> **Alxl said:**
> In PP I did 
:~$ sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-21-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-21-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sda2
done


no mention of XP  on  /dev/sda1   .

Are all 3 O/S on the same hard drive, or are the Ubuntu's on one drive and XP on another?

Are you using a laptop, desktop or other?

By the looks of things, you have the latest kernel installed - 3.2.0-21

---

### Post by bennachie on 2012-03-31
I'm not sure quite what sequence of events has led to this outcome, but suspect that the best approach may now be to do a fresh install of PP to sda3, using manual partitioning, and leaving sda1 and sda2 undisturbed. This does tend to be the point where you start to wish that you had created a separate home partition (I have learned the hard way that this makes beta testing a more relaxing experience), but I assume all your data can be retrieved from either sda1 or sda2 as required.

However, I'd be pretty confident that you'll get XP back that way.

---

### Post by Baldrick_NZ on 2012-03-31
> **bennachie said:**
> I'm not sure quite what sequence of events has led to this outcome, but suspect that the best approach may now be to do a fresh install of PP to sda3, using manual partitioning, and leaving sda1 and sda2 undisturbed. This does tend to be the point where you start to wish that you had created a separate home partition (I have learned the hard way that this makes beta testing a more relaxing experience), but I assume all your data can be retrieved from either sda1 or sda2 as required.

However, I'd be pretty confident that you'll get XP back that way.

I've had the same prob before too, turned out to be a loose connection on my separate XP drive. Once fixed, I ran ```
sudo grub-update
```and then XP showed up again.

I'd hate for the OP go through an exhaustive process of re-install only to find it didn't fix the prob. Worth a look first I reckon, assuming he has two drives ofcourse..

---

### Post by Alxl on 2012-03-31
To avoid further misunderstandings, I now have both Ubuntu 10.04.4 LTS (10.04) on /dev/sda2     and Ubuntu PP on /dev/sda6    and both are working.     Updating grub from a live USB and updating grub did that

And  now I have done    'sudo grub-update '  twice  (once in 10.04  and once in 11.04)  and XP did not re-apear for me.

GParted shows /dev/sda1 as having 'Unknown' File System  (XP is actually here) but also mentions 'boot'  for Flags.

---

### Post by LostFarmer on 2012-03-31
download and run 'boot_info-scrip' and post the resaults.txt

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

can you mount and read the files on XP partition ?

---

### Post by bennachie on 2012-03-31
Simply running update-grub from a live CD (or from an existing installation, for that matter) won't necessarily solve the problem - you actually need to reinstall the Grub. The usual sequence of commands in the terminal window, which I had assumed you had used, is:

sudo fdisk -l 
[to check that everything is where you think it is]

sudo mkdir /media/sdax	
[where “x” is the / partition for “home” OS]

sudo mount /dev/sdax /media/sdax
sudo grub-install –root-directory=/media/sdax /dev/sda
exit

After rebooting to the installed “home” OS, then run:

sudo update-grub

---

### Post by Alxl on 2012-03-31
Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    64,184,319    64,184,257   7 NTFS / exFAT / HPFS
/dev/sda2          64,311,296   134,115,327    69,804,032  83 Linux
/dev/sda3         400,603,134   976,771,071   576,167,938   5 Extended
/dev/sda5         400,603,136   404,506,623     3,903,488  82 Linux swap / Solaris
/dev/sda6         404,516,763   467,957,384    63,440,622  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 507 MB, 507379712 bytes
147 heads, 21 sectors/track, 321 cylinders, total 990976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63       989,183       989,121   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        e714520b-e43d-45bb-9768-43aff2e0ffd1   ext4       Ubuntu10.04
/dev/sda5        a553e957-1b02-4a9c-8342-0851cc2213ec   swap       
/dev/sda6        a02b1cc0-35c8-4ef7-9778-82e5867048e1   ext4       ubuntu12_04
/dev/sdb1        1CE5-6922                              vfat       0_5GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/0_5GB             vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=e714520b-e43d-45bb-9768-43aff2e0ffd1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
    echo    'Loading Linux 2.6.32-40-generic ...'
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=e714520b-e43d-45bb-9768-43aff2e0ffd1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-40-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e714520b-e43d-45bb-9768-43aff2e0ffd1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.2.0-21-generic-pae (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a02b1cc0-35c8-4ef7-9778-82e5867048e1
    linux /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=a02b1cc0-35c8-4ef7-9778-82e5867048e1 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.2.0-21-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-21-generic-pae (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a02b1cc0-35c8-4ef7-9778-82e5867048e1
    linux /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=a02b1cc0-35c8-4ef7-9778-82e5867048e1 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-21-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=e714520b-e43d-45bb-9768-43aff2e0ffd1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6e496efe-b2ff-4766-b956-a4ceab2b5cdc none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.32-40-generic              2
               =                boot/vmlinuz-2.6.32-40-generic                 1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
    linux    /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=a02b1cc0-35c8-4ef7-9778-82e5867048e1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-21-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
    echo    'Loading Linux 3.2.0-21-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=a02b1cc0-35c8-4ef7-9778-82e5867048e1 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a02b1cc0-35c8-4ef7-9778-82e5867048e1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-40-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root e714520b-e43d-45bb-9768-43aff2e0ffd1
    linux /boot/vmlinuz-2.6.32-40-generic root=UUID=e714520b-e43d-45bb-9768-43aff2e0ffd1 ro quiet splash
    initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Ubuntu, with Linux 2.6.32-40-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root e714520b-e43d-45bb-9768-43aff2e0ffd1
    linux /boot/vmlinuz-2.6.32-40-generic root=UUID=e714520b-e43d-45bb-9768-43aff2e0ffd1 ro single
    initrd /boot/initrd.img-2.6.32-40-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a02b1cc0-35c8-4ef7-9778-82e5867048e1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a553e957-1b02-4a9c-8342-0851cc2213ec none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-21-generic-pae           3
               =                boot/vmlinuz-3.2.0-21-generic-pae              1
               =                initrd.img                                     3
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by Alxl on 2012-03-31
@[LostFarmer]("http://ubuntuforums.org/member.php?u=1268688")

I cannot mount or read the XP partition.
Hope that the 'Boot Info Script' will show what the problem is.

@bennachie  I actually did re-install grub initially - I did boot from a live USB and installed grub 2 

Thank you all

---

### Post by LostFarmer on 2012-03-31
in a root terminal run 'testdisk', it may or may not be installed.

do a web search for how to use.  you will need to get to the 'advanced' option ,hi light the XP partition and press enter.  What does it say about the boot sector data.  

For some reason your XP boot record is bad, 'testdisk' normally can fix it.  After 'testdisk' it may require running XP's recovery console and run 'fixboot'.

---

### Post by Alxl on 2012-03-31
> **LostFarmer said:**
> in a root terminal run 'testdisk', it may or may not be installed.

do a web search for how to use.  you will need to get to the 'advanced' option ,hi light the XP partition and press enter.  What does it say about the boot sector data.  

For some reason your XP boot record is bad, 'testdisk' normally can fix it.  After 'testdisk' it may require running XP's recovery console and run 'fixboot'.

Thanks I installed testdisk but it's getting late so I'll do the rest tomorrow eve

---

### Post by Alxl on 2012-04-02
I run Testdisk in advanced  and clicked on 'Boot' for a Boot disk Recovery.  It did the recovery and ended saying that Boot sector is OK. (pls see attachment).

GParted now says that the partition is NTFS (previously it was 'unknown') and to run  ' chkdsk /f ' in Windows. (pls see attachment).

 How does one run ' chkdsk /f 'in Windows?    XP reinstallation CD?

But I still cannot mount XP.  And it does not pay for me to reinstall XP since it would also delete Linux.

Thanks

---

### Post by LostFarmer on 2012-04-02
> How does one run ' chkdsk /f 'in Windows?    XP reinstallation CD?  You would need a MS install cd not a recovery cd.  Can do a web search and find a recovery console cd.

I do not know how but one can force a mount of the XP partition, but it is not a good idea nor do I know then what.

I would try renunning 
grub-update
 and see what happens. XP may now be listed and when booted may fix itself.

---

### Post by Alxl on 2012-04-02
Unfortunately update-grub did work.

So I booted from the XP Reinstallation DVD  and went to 'repair Win XP installation using recovery console' which did not accept 'chkdsk \f'  but  let me use 'FIXBOOT' and this partially worked since now update-grub lists Windows XP and I can mount XP.  

But when trying to boot XP, got this error : 'load needed DLLs for kernel' .

So I tried to learn about this new problem and found that I need to reinstall NTOSKRNL.FX_  but that did not work (it did not find it in the cd) ; somewhere else it says to reinstall HAL.DL_  and this apparently worked.

BUt the same error appears:  'load needed DLLs for kernel'

---

