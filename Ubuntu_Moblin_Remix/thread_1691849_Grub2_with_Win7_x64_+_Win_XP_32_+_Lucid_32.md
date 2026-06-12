---
title: "Grub2 with Win7 x64 + Win XP 32 + Lucid 32"
date: 2011-02-20
forum: Ubuntu Moblin Remix
---

### Post by fusebox on 2011-02-20
Hello folks

I've Just installed in the following order

[LIST=1]
[*]XP
[*]Lucid
[*]Win 7 x64
[/LIST]

The last install messed grub2 but i fixed it with a live CD
The problem is i'm unable to boot into the window$ installations,

Grub2 boots lucid nicely but it gives me a flashing underscore when i select the other entries.

Any fix for this?

herez my partition info

/dev/sda1 -> XP 
/dev/sda3 -> Stuff
/dev/sda3 -> Lucid
/dev/sda4 -> extended
    /dev/sda5 ->Swap
    /dev/sda6 ->Win7 X64

Herez my grub.cnf (entries only)

[HTML]### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e74fee0d-537c-453f-9aa5-c8a19b034af0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e74fee0d-537c-453f-9aa5-c8a19b034af0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6681b99a666d0be0
	drivemap -s (hd0) ${root}
	chainloader +1
}

menuentry "Windows 7 x64 ( loader) (on /dev/sda6)" {
	insmod ntfs
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d48ee71f8ee6f93e
	drivemap -s (hd0) ${root} 
	chainloader +1
}[/HTML]

---

### Post by oldfred on 2011-02-20
Your win7 is in a logical partition so it can only boot thru the XP partition.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Post this so we can see your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by fusebox on 2011-02-20
Thanks for the quick reply

Sorry to cut you short but I've just discovered some more info

I overlooked the fact that Win7 installed it's bootloader in the XP partition
which then boots win7 from the logical partition (and also XP id need be from its partition)

Is there a way to let grub2 cork with this config?

---

### Post by fusebox on 2011-02-20
Here's The Feedback from **boot_info_script**
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 556. But according to the info from fdisk, 
                       sda6 starts at sector 324192256.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,414,374   102,414,312   7 HPFS/NTFS
/dev/sda2         102,414,375   163,830,869    61,416,495   7 HPFS/NTFS
/dev/sda3         163,840,000   320,090,111   156,250,112  83 Linux
/dev/sda4         320,090,112   488,392,064   168,301,953   5 Extended
/dev/sda5         320,095,188   324,191,699     4,096,512  82 Linux swap / Solaris
/dev/sda6         324,192,256   488,390,655   164,198,400   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,279,609   488,279,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6681B99A666D0BE0                       ntfs       XPPR                          
/dev/sda2        70E00706596C3CD5                       ntfs       STUFF                         
/dev/sda3        e74fee0d-537c-453f-9aa5-c8a19b034af0   ext3       Lucid                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8bf2e0af-05a8-4487-becd-8eff5b1b1aec   swap                                     
/dev/sda6        D48EE71F8EE6F93E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4CCC23C12AEA5859                       ntfs       STUFF                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /media/XPPR              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/WIN7              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/STUFF             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e74fee0d-537c-453f-9aa5-c8a19b034af0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e74fee0d-537c-453f-9aa5-c8a19b034af0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e74fee0d-537c-453f-9aa5-c8a19b034af0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6681b99a666d0be0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda2 during installation
/dev/sdb5 none            swap    sw              0       0

/dev/sda1    /media/XPPR    ntfs-3g    errors=remount-ro,user,auto,noexec,umask=0    0    0
/dev/sda6    /media/WIN7    ntfs-3g    errors=remount-ro,user,auto,noexec,umask=0    0    0
/dev/sdb1    /media/STUFF    ntfs-3g    errors=remount-ro,user,auto,noexec,umask=0    0    0

=================== sda3: Location of files loaded by Grub: ===================


  98.5GB: boot/grub/core.img
  98.5GB: boot/grub/grub.cfg
  98.5GB: boot/initrd.img-2.6.32-21-generic
  98.5GB: boot/vmlinuz-2.6.32-21-generic
  98.5GB: initrd.img
  98.5GB: vmlinuz

```

---

### Post by oldfred on 2011-02-20
Grub will boot the XP partition and then you can choose which windows to boot.

If you install both windows in primary partitions, you would be able to move boot flag and run repairs. Then grub could directly boot both.

There are some instructions here on getting XP to boot from a logical partition, but not win7.

---

### Post by fusebox on 2011-02-20
Before i repaired grub2 (After installing win7 last)
BCD booted fine then gave me an option for win7 or XP. It worked OK

After updaing grub2, at boot it hands over to BCD which just shows a blinking underscore.

BCD was able to boot win7 (which is on a logical partition) from sda1 (which is primary)

Is there any way to allow BCD to perform this hat trick again by configuring grub.cfg?

As in Grub2 -> BCD (sda1) -> win7 (logical sda6)

I'm trying to avoid moving my partitions around coz of lack of time and disk space. And i dont wan't to nuke any of my installations.

---

### Post by oldfred on 2011-02-20
As near as I can tell it should work. If you resized the XP partition, it may need chkdsk run until there are no errors.

One minor thing that sometimes causes issues is that you have a grub4dos file/folder in window. I would delete this:

/grldr

Sometimes you have to run windows repairs on the partition.
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by fusebox on 2011-02-20
Ok then. 

It seems the workaround i'm looking for is elusive. I'll sort it out your way (maybe with some modifications)
 but i'll have to buy another hard disk..... i could use the extra space anyway

Thank you for your time. I appreciate your help.

---

