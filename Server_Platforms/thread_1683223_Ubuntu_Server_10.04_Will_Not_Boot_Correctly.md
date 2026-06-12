---
title: "Ubuntu Server 10.04 Will Not Boot Correctly"
date: 2011-02-07
forum: Server Platforms
---

### Post by BlueVark on 2011-02-07
I am having very frustrating, constant boot problems with my new server setup.  This is the first Ubuntu server I have used so I'm not too sure about how to resolve these issues.  Any advice would be greatly appreciated. 

_Setup_:  I am running Ubuntu 10.04 Server on a small HD with the standard 3 partitions.  I have all my data on a (software) RAID 1 setup with two other matching HDs.  I also have an external HD that I occasionally mount for backup purposes. (see copy of Fstab below)

_Problem_:  When I boot/reboot the server it will hang up because it tries to boot on the wrong partition/drive.  I have to physically turn the machine off/on a number of times before it will finally boot correctly.  I have changed the Fstab to use the UUID system, but this hasn't helped.  I have changed the order of the Fstab, but this hasn't helped.  I have made sure the BIOS is using the correct boot order, but this hasn't helped.  It seems there is something else in the Operating System that is setup wrong, but I don't know what it could be.  

Is there something that I am missing?  Is there some other way to make sure the machine will boot to the correct partition?  

Thanks for looking and I would appreciate any advice as I need this server to be more reliable before I commit any serious data to it.  

Copy of current Fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
#
UUID=10f16be5-44f3-4c3e-8175-2312c52a71a5  /  ext4  errors=remount-ro  0  1
UUID=725c2f90-1430-4926-b1b5-af1f4ab9bac9 /boot  ext2  defaults  0  2
UUID=c49a175c-fac7-48ee-a540-185a3b677cdb  swap  swap  0  0
UUID=4bbee805-505c-4364-8612-1361fbb9891f  /mymounts/raid  ext4  defaults  0  0 
UUID=0C14D32B14D31694  /mymounts/ext1  ntfs  noauto  0  0
UUID=2FB5-7FA0  /mymounts/zip1  vfat  uid=1000,gid=1000,noauto  0  0 
#

---

### Post by P4man on 2011-02-07
Do you always get the grub menu? If you do, try adding 
rootdelay=90 
to your kernel options. Maybe one of the drives isnt spinning up/reacting fast enough.

---

### Post by BlueVark on 2011-02-07
Thanks P4man,

I'll give that a try.  How do I get the file and/or what it the file name I need to set in the delay?  

Thanks again.

---

### Post by P4man on 2011-02-07
Click the link in my signature to see how to set kernel options

---

### Post by BlueVark on 2011-02-07
Thanks again to P4man,

I found the file, but would like to confirm where to put your suggested "rootdelay=90" comment.  Does it go on the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet" within the quotes like this:  
GRUB_CMDLINE_LINUX_DEFAULT="quiet rootdelay=90" ? 
Or does this go somewhere else?

Sorry for so many questions this is way beyond my Ubuntu knowledge.  Thanks again.

---

### Post by P4man on 2011-02-07
Yep thats correct. And dont forget to run update-grub.
But again, that only has a chance of working if grub loads every time, even the times it fails to boot.
Also feel free to try a bigger number, some machines need even more than 10 seconds, so try 150 or whatever (thats 15 seconds).

---

### Post by BlueVark on 2011-02-07
Hey P4man,

Thanks again for the information, but bad news on my end...I changed the grub file as you suggested and still have the same problem.  I had to cycle the computer on/off 5 times before it finally booted correctly.  I am completely out of ideas on how to fix this issue.  

Anyone else have any idea what could be causing this boot problem?

---

### Post by cariboo on 2011-02-07
I haven't used raid in a while, but the array is usually mapped to a device, usually something like:

```
/dev/mapper/nvidiaramdomstring
```

have you tried the device instead of using uuid?

---

### Post by BlueVark on 2011-02-07
Yes, I initially had all the HD partitions, including the RAID, mapped as devices with the Fstab file.  This was how I first started and the problem was the same.  I did some research and it was suggested that I change from devices to UUID, but obviously that hasn't helped.  There must be some other file/setting that is causing the boot order to be intermittently incorrect.  I just don't know enough about Ubuntu Server to find that setting.  

I am impressed with the server setup when it works.  If I could only get this problems sorted out I would have a very secure, home server.  

Thanks again for your help.

---

### Post by P4man on 2011-02-08
Is it possible you have grub MBR accidentally installed on to on of both raid drives? Can you run bootinfo script and report the output? Details here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by BlueVark on 2011-02-08
I'm pretty sure that grub is only loaded on the boot HD.  However, I ran the script as you suggested.  I don't see anything unusual, but remember this is a picture after the server booted correctly.  I'm not sure how to get a picture of when it doesn't boot correctly.  Do you see anything in the attached file that could be causing the problem?

Thanks again for the help. 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

mikenet-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

mikenet-swap_1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders, total 12594960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758    12,593,151    12,091,394   5 Extended
/dev/sda5             501,760    12,593,151    12,091,392  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   320,159,384   320,159,322  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   320,143,319   320,143,257  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/mikenet-root 10f16be5-44f3-4c3e-8175-2312c52a71a5   ext4                                     
/dev/mapper/mikenet-swap_1 c49a175c-fac7-48ee-a540-185a3b677cdb   swap                                     
/dev/md0         4bbee805-505c-4364-8612-1361fbb9891f   ext4                                     
/dev/sda1        725c2f90-1430-4926-b1b5-af1f4ab9bac9   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        PF61nV-Zk2N-6SmR-tk2b-nx2J-gHl4-XC8031 LVM2_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2ade0cac-f0a1-3c6e-1451-030b2a098687   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2ade0cac-f0a1-3c6e-1451-030b2a098687   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
mikenet-root
mikenet-swap_1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/mikenet-root /                        ext4       (rw,errors=remount-ro)
/dev/md0         /mymounts/raid           ext4       (rw)
/dev/sda1        /boot                    ext2       (rw)


============================= sda1/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root='(mikenet-root)'
search --no-floppy --fs-uuid --set 10f16be5-44f3-4c3e-8175-2312c52a71a5
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux	/vmlinuz-2.6.32-28-generic-pae root=/dev/mapper/mikenet-root ro   quiet rootdelay=90
	initrd	/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	echo	'Loading Linux 2.6.32-28-generic-pae ...'
	linux	/vmlinuz-2.6.32-28-generic-pae root=/dev/mapper/mikenet-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux	/vmlinuz-2.6.32-27-generic-pae root=/dev/mapper/mikenet-root ro   quiet rootdelay=90
	initrd	/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	echo	'Loading Linux 2.6.32-27-generic-pae ...'
	linux	/vmlinuz-2.6.32-27-generic-pae root=/dev/mapper/mikenet-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux	/vmlinuz-2.6.32-26-generic-pae root=/dev/mapper/mikenet-root ro   quiet rootdelay=90
	initrd	/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/vmlinuz-2.6.32-26-generic-pae root=/dev/mapper/mikenet-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux	/vmlinuz-2.6.32-24-generic-pae root=/dev/mapper/mikenet-root ro   quiet rootdelay=90
	initrd	/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/vmlinuz-2.6.32-24-generic-pae root=/dev/mapper/mikenet-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 725c2f90-1430-4926-b1b5-af1f4ab9bac9
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-generic-pae
    .0GB: initrd.img-2.6.32-26-generic-pae
    .0GB: initrd.img-2.6.32-27-generic-pae
    .0GB: initrd.img-2.6.32-28-generic-pae
    .0GB: vmlinuz-2.6.32-24-generic-pae
    .0GB: vmlinuz-2.6.32-26-generic-pae
    .0GB: vmlinuz-2.6.32-27-generic-pae
    .0GB: vmlinuz-2.6.32-28-generic-pae

=========================== mikenet-root/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
#
UUID=10f16be5-44f3-4c3e-8175-2312c52a71a5  /  ext4  errors=remount-ro  0  1
#
UUID=725c2f90-1430-4926-b1b5-af1f4ab9bac9 /boot  ext2  defaults  0  2
#
UUID=c49a175c-fac7-48ee-a540-185a3b677cdb  swap  swap  0  0
#
UUID=4bbee805-505c-4364-8612-1361fbb9891f  /mymounts/raid  ext4  defaults  0  0 
#
UUID=0C14D32B14D31694  /mymounts/ext1  ntfs  noauto  0  0
#
UUID=2FB5-7FA0  /mymounts/zip1  vfat  uid=1000,gid=1000,noauto  0  0 
#

=============== mikenet-root: Location of files loaded by Grub: ===============


    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```

---

### Post by P4man on 2011-02-08
I see sdc1 is marked as bootable, and  apparently still has windows bootloader, as well as on the other raid drive. Perhaps remove the boot flag first, you can do that with gparted. You could also try removing the windows bootloader, but Im not sure how to do that without messing up the raid.

---

### Post by BlueVark on 2011-02-08
I will try and use gparted to unmark the sdc1.  

I can't imagine there is really a windows boot-loader on the RAID drive.  Both of those disks were reformatted and changed to ext4.  Could that be some kind of mislabeling?  How could I confirm that there is really a windows boot-loader on those drives?  I am willing to reformat them again if that is what it takes to get this booting correctly.

---

### Post by P4man on 2011-02-08
Formatting doesnt touch the master boot record, which holds the bootloader. If you want to erase that, you can use this but USE WITH CAUTION:

```
dd if=/dev/zero of=/dev/sd[COLOR="Red"]c[/COLOR] bs=512 count=1
```

where c would be the drive letter. This probably messes up the raid as well, as I think most softraids put some metadata on the MBR, but I could be wrong there. Either way, just clearing the bootable flag might do it. IF not, double/triple check your BIOS settings and consider clearing the CMOS

---

### Post by BlueVark on 2011-02-08
Thanks again P4man for all your help.  I'll give your latest suggestions a try later this evening...I've got to run to other tasks this afternoon.

---

