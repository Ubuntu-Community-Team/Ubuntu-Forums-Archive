---
title: "Fresh install on't boot into anything"
date: 2012-05-11
forum: Server Platforms
---

### Post by AbsenteeSurgeon on 2012-05-11
**System Info:** (brand new)
Mobo: BIOSTAR TA870U3+
CPU: AMD Phenom II x2 (unlocked to x4)
HDD: Western Digital Black 500GB (OS)
HDD: 2x 1TB storage drives (formatted to NTFS in windows)
HDD: 2TB storage (wiped to ext2)

**Problem:**
Installed everything no problem with the OpenSSH package. Reset the computer. Boots into black screen with cursor ticking at the top right.

**What I've tried:**
Re-install changing no settings
Re-install without MBR
Holding shift during the system boot (trying to get to GRUB, no luck)

Any ideas? Thanks!

---

### Post by darkod on 2012-05-11
Grub might not have installed, which could explain why Shift is not displaying the menu.

Can you boot it with the desktop live cd, and run the boot info script from the link in my signature. It will show many details. Post the results as explained there.

---

### Post by AbsenteeSurgeon on 2012-05-11
> **darkod said:**
> Grub might not have installed, which could explain why Shift is not displaying the menu.

Can you boot it with the desktop live cd, and run the boot info script from the link in my signature. It will show many details. Post the results as explained there.

Results of the script: [http://sharetext.org/D2H3](http://sharetext.org/D2H3)

I also am going to put a little more context in the post.

---

### Post by oldfred on 2012-05-11
I do not know RAID nor LVM, but I thought the server installer had those drivers. Script is not showing the LVM partitions, and I wonder if that is why grub2 is not booting. Desktop liveCD does not have them by default, so if you ran it from liveCD or USB that is why script is missing LVM info.

Some of the others are for the script to do math and include just a bit more info.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

If you rerun script and it still does not show the LVM internals, you do not need to repost.

You can directly copy & paste in your message, then highlight again and click on the # which adds code tags. That preserves formating and makes it easier to review.

---

### Post by AbsenteeSurgeon on 2012-05-12
> **oldfred said:**
> I do not know RAID nor LVM, but I thought the server installer had those drivers. Script is not showing the LVM partitions, and I wonder if that is why grub2 is not booting. Desktop liveCD does not have them by default, so if you ran it from liveCD or USB that is why script is missing LVM info.

Some of the others are for the script to do math and include just a bit more info.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

If you rerun script and it still does not show the LVM internals, you do not need to repost.

You can directly copy & paste in your message, then highlight again and click on the # which adds code tags. That preserves formating and makes it easier to review.

I'm running a liveCD, and following these steps appears to have brought up some new info (bottom of post). Also, the following line of code threw errors in my terminal:
```
unlzma is equivalent to xz --format=lzma --decompress
```I'm not sure if you meant this as a comment or as code that was supposed to execute. Thanks for your help!

```
Boot Info Script 0.61      [1 April 2012] 
 
 
============================= Boot Info Summary: =============================== 
 
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of  
    the same hard drive for core.img. core.img is at this location and uses an  
    embedded config file: 
     
    --------------------------------------------------------------------------- 
    search.fs_uuid c85147ab-d4cb-426e-966d-1e6a05531724 root  
    set prefix=($root)/grub 
    --------------------------------------------------------------------------- 
    -----. 
 => Windows is installed in the MBR of /dev/sdb. 
 => Windows is installed in the MBR of /dev/sdc. 
 => No boot loader is installed in the MBR of /dev/sdd. 
 
sda1: __________________________________________________________________________ 
 
    File system:       ext2 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:   
    Boot files:         
 
sdb1: __________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7: NTFS 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files:         
 
sdc1: __________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7: NTFS 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files:         
 
sdd1: __________________________________________________________________________ 
 
    File system:       ext2 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:   
    Boot files:        /grub/grub.cfg /grub/core.img 
 
sdd2: __________________________________________________________________________ 
 
    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:  
 
sdd5: __________________________________________________________________________ 
 
    File system:       LVM2_member 
    Boot sector type:  - 
    Boot sector info:  
 
ScottUbuntuFileServer-root': ___________________________________________________ 
 
    File system:        
    Boot sector type:  Unknown 
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type '' 
 
ScottUbuntuFileServer-swap_1': _________________________________________________ 
 
    File system:        
    Boot sector type:  Unknown 
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type '' 
mount: unknown filesystem type '' 
 
============================ Drive/Partition Info: ============================= 
 
Drive: sda _____________________________________________________________________ 
 
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes 
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
 
/dev/sda1    *          2,048 3,907,028,991 3,907,026,944  83 Linux 
 
 
Drive: sdb _____________________________________________________________________ 
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
 
/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS 
 
 
Drive: sdc _____________________________________________________________________ 
 
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
 
/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS 
 
 
Drive: sdd _____________________________________________________________________ 
 
Disk /dev/sdd: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
 
/dev/sdd1               2,048       499,711       497,664  83 Linux 
/dev/sdd2             501,758   976,771,071   976,269,314   5 Extended 
/dev/sdd5             501,760   976,771,071   976,269,312  8e Linux LVM 
 
 
"blkid" output: ________________________________________________________________ 
 
Device           UUID                                   TYPE       LABEL 
 
/dev/loop0                                              squashfs    
/dev/sda1        ecd0e437-0d94-42a3-9619-832f56043423   ext2       2TB Green 
/dev/sdb1        0C4061D54061C654                       ntfs       1 TB Internal (Misc) 
/dev/sdc1        1A0AB4E70AB4C155                       ntfs       1 TB Internal (Media) 
/dev/sdd1        c85147ab-d4cb-426e-966d-1e6a05531724   ext2        
/dev/sdd5        LGr1HX-vf5X-NeLs-w0tq-VUDi-FQAY-YWuk7j LVM2_member  
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64 
 
================================ Mount points: ================================= 
 
Device           Mount_Point              Type       Options 
 
/dev/loop0       /rofs                    squashfs   (ro,noatime) 
/dev/sr0         /cdrom                   iso9660    (ro,noatime) 
 
 
============================= sdd1/grub/grub.cfg: ============================== 
 
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
 
insmod lvm 
insmod part_msdos 
insmod ext2 
set root='(ScottUbuntuFileServer-root)' 
search --no-floppy --fs-uuid --set=root 5dae6f7d-48b0-4a8a-8a8f-724051c825eb 
if loadfont /usr/share/grub/unicode.pf2 ; then 
  set gfxmode=auto 
  load_video 
  insmod gfxterm 
  insmod part_msdos 
  insmod ext2 
  set root='(hd3,msdos1)' 
  search --no-floppy --fs-uuid --set=root c85147ab-d4cb-426e-966d-1e6a05531724 
  set locale_dir=($root)/grub/locale 
  set lang=en_US 
  insmod gettext 
fi 
terminal_output gfxterm 
if [ "${recordfail}" = 1 ]; then 
  set timeout=-1 
else 
  set timeout=2 
fi 
### END /etc/grub.d/00_header ### 
 
### BEGIN /etc/grub.d/05_debian_theme ### 
set menu_color_normal=white/black 
set menu_color_highlight=black/light-gray 
### END /etc/grub.d/05_debian_theme ### 
 
### BEGIN /etc/grub.d/10_linux ### 
function gfxmode { 
    set gfxpayload="$1" 
    if [ "$1" = "keep" ]; then 
        set vt_handoff=vt.handoff=7 
    else 
        set vt_handoff= 
    fi 
} 
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    gfxmode $linux_gfx_mode 
    insmod gzio 
    insmod part_msdos 
    insmod ext2 
    set root='(hd3,msdos1)' 
    search --no-floppy --fs-uuid --set=root c85147ab-d4cb-426e-966d-1e6a05531724 
    linux    /vmlinuz-3.2.0-23-generic root=/dev/mapper/ScottUbuntuFileServer-root ro    
    initrd    /initrd.img-3.2.0-23-generic 
} 
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    insmod gzio 
    insmod part_msdos 
    insmod ext2 
    set root='(hd3,msdos1)' 
    search --no-floppy --fs-uuid --set=root c85147ab-d4cb-426e-966d-1e6a05531724 
    echo    'Loading Linux 3.2.0-23-generic ...' 
    linux    /vmlinuz-3.2.0-23-generic root=/dev/mapper/ScottUbuntuFileServer-root ro recovery nomodeset  
    echo    'Loading initial ramdisk ...' 
    initrd    /initrd.img-3.2.0-23-generic 
} 
### END /etc/grub.d/10_linux ### 
 
### BEGIN /etc/grub.d/20_linux_xen ### 
### END /etc/grub.d/20_linux_xen ### 
 
### BEGIN /etc/grub.d/20_memtest86+ ### 
menuentry "Memory test (memtest86+)" { 
    insmod part_msdos 
    insmod ext2 
    set root='(hd3,msdos1)' 
    search --no-floppy --fs-uuid --set=root c85147ab-d4cb-426e-966d-1e6a05531724 
    linux16    /memtest86+.bin 
} 
menuentry "Memory test (memtest86+, serial console 115200)" { 
    insmod part_msdos 
    insmod ext2 
    set root='(hd3,msdos1)' 
    search --no-floppy --fs-uuid --set=root c85147ab-d4cb-426e-966d-1e6a05531724 
    linux16    /memtest86+.bin console=ttyS0,115200n8 
} 
### END /etc/grub.d/20_memtest86+ ### 
 
### BEGIN /etc/grub.d/30_os-prober ### 
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
 
=================== sdd1: Location of files loaded by Grub: ==================== 
 
           GiB - GB             File                                 Fragment(s) 
 
   0.089460373 = 0.096057344    grub/core.img                                  2 
   0.087568283 = 0.094025728    grub/grub.cfg                                  1 
   0.042882919 = 0.046045184    initrd.img-3.2.0-23-generic                   76 
   0.010010719 = 0.010748928    vmlinuz-3.2.0-23-generic                      21 
 
======================== Unknown MBRs/Boot Sectors/etc: ======================== 
 
Unknown BootLoader on ScottUbuntuFileServer-root' 
 
 
Unknown BootLoader on ScottUbuntuFileServer-swap_1' 
 
 
 
=============================== StdErr Messages: =============================== 
 
xz: (stdin): Compressed data is corrupt 
  One or more specified logical volume(s) not found. 
  One or more specified logical volume(s) not found. 
  One or more specified logical volume(s) not found. 
hexdump: /dev/mapper/ScottUbuntuFileServer-root': No such file or directory 
hexdump: /dev/mapper/ScottUbuntuFileServer-root': No such file or directory 
  One or more specified logical volume(s) not found. 
  One or more specified logical volume(s) not found. 
  One or more specified logical volume(s) not found. 
hexdump: /dev/mapper/ScottUbuntuFileServer-swap_1': No such file or directory 
hexdump: /dev/mapper/ScottUbuntuFileServer-swap_1': No such file or directory 
mdadm: No arrays found in config file or automatically 
            
                                     
        
```

---

### Post by oldfred on 2012-05-12
I think last line is a comment, I have to correct my notes.

It shows a bit more as now you see your LVM partitions, but it did not mount them nor show the UUIDs. You see the UUID in the search line but partition and UUID is not shown in UUID list? Not sure if you have partition issues or driver is still not showing all the info. If a regular partition I would suggest e2fsck, but with LVM, I do not know.

I do not know LVM enough to add more. 

Some with grub errors can use this but I do not know if it works with LVM.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by darkod on 2012-05-12
I am not sure what exactly it does, but I don't like it that it says grub2 uses embedded file. And it went on the disk /dev/sda while it's better to keep it on /dev/sdd where your server is.

Boot into live mode, install the lvm2 package, activate the LVM and check the name of the logical volumes:
sudo apt-get install lvm2
sudo vgchange -ay
lvscan

After that, mount the /boot partition and the root partition temporarily:
sudo mount /dev/VolumeGroup-LogicalVolume /mnt (change VolGr and LogVol with the real values, and note that I think you don't need to use mapper here)
sudo mount /dev/sdd1 /mnt/boot

If you installed 12.04, the grub install procedure was changed a little. Try:
sudo grub-install --boot-directory=/mnt/boot /dev/sdd

If you use version earlier than 11.04, try:
sudo grub-install --root-directory=/mnt /dev/sdd

In case mount root doesn't work with the command above, try with /dev/mapper/VolGr-LogVol.

Make the /dev/sdd disk first option to boot in BIOS.

---

### Post by AbsenteeSurgeon on 2012-05-12
I GOT IT WORKING! Here's how:

I suspect darkod was right: grub was being installed onto the "first" hard drive, not the drive I was installing the server to.  So when my BIOS went to boot from that drive, grub wasn't there.

I solved my problem by unplugging all of my other drives before installation, and then plugging them back in after everything was finished. Disabling them in the BIOS probably would've been equivalent, but I didn't want to take any chances.

Thanks or all of your help!!!

---

