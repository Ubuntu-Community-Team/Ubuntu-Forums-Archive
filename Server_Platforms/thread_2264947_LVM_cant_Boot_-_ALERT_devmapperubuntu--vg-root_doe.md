---
title: "LVM cant Boot - ALERT /dev/mapper/ubuntu--vg-root does not exist DROPPING to Shell -"
date: 2015-02-11
forum: Server Platforms
---

### Post by LouisinLondon on 2015-02-11
Help needed - hopefully someone has had this issue where after a reboot the server just goes to BusyBox
(initramfs)

What I've tried already unsuccessfully is:
from Live Disk
==================
[COLOR=#333333][FONT=UbuntuRegular]sudo su
apt-get install lvm2
vgchange -a y[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular](do any lvm management you need here, I didn't need any.)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]mkdir /mnt/system[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]mount /dev/mapper/ubuntu--vg-root /mnt/system[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]mount /dev/sda1 /mnt/system/boot[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]for i in /dev/pts /dev /proc /sys; do mount -B $i /mnt/system$i; done[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]chroot /mnt/system[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]update-initramfs -k all -c[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]exit[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]for i in /dev/pts /dev /proc /sys; do umount /mnt/system$i; done[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]umount /mnt/system/boot[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]umount /mnt/system[/FONT][/COLOR]
==================
Second Thing I've tried is:

Last resort was to use BootRepair :
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
Also not happy - same result

Here's the Boot info and copied into the post at the bottom

[http://paste.ubuntu.com/10172826/](http://paste.ubuntu.com/10172826/)


=========== What I'm trying next  Fixing LVM in initfs ============
from the post:
[http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd](http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd)
starting at:
[COLOR=#333333][FONT=UbuntuRegular]"You hit the problem right on the head: the initramfs does not have LVM support. Here's how to fix it:"[/FONT][/COLOR]

But I don't think I should copy all the .deb files as shown in the post


========== BOOTINFO ==================
```

Boot Info Script e7fc706 + Boot-Repair extra info [Boot-Info 23Nov2014]




============================= Boot Info Summary: ===============================


=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for (,msdos1)/grub on this drive.


sda1: __________________________________________________________________________


File system: ext2
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files: /grub/grub.cfg /grub/core.img


sda2: __________________________________________________________________________


File system: Extended Partition
Boot sector type: -
Boot sector info: 


sda5: __________________________________________________________________________


File system: LVM2_member
Boot sector type: -
Boot sector info: 


ubuntu-vg-root: ________________________________________________________________


File system: 
Boot sector type: Unknown
Boot sector info: 
Mounting failed: mount: unknown filesystem type ''


ubuntu-vg-swap_1: ______________________________________________________________


File system: 
Boot sector type: Unknown
Boot sector info: 
Mounting failed: mount: unknown filesystem type ''
mount: unknown filesystem type ''


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 274.9 GB, 274877906944 bytes
255 heads, 63 sectors/track, 33418 cylinders, total 536870912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition Boot Start Sector End Sector # of Sectors Id System


/dev/sda1 * 2,048 499,711 497,664 83 Linux
/dev/sda2 501,758 536,868,863 536,367,106 5 Extended
/dev/sda5 501,760 536,868,863 536,367,104 8e Linux LVM




"blkid" output: ________________________________________________________________


Device UUID TYPE LABEL


/dev/loop0 squashfs 
/dev/mapper/ubuntu--vg-root 7ac6de90-7465-4c46-9317-bff2e6db2bbd ext4 
/dev/mapper/ubuntu--vg-swap_1 261d12c0-3a89-4492-92ca-f9606b7842bc swap 
/dev/sda1 15893ded-64d9-420b-907a-86831f8417f4 ext2 
/dev/sda5 XkdnOb-cmqR-0ztU-8fW4-QLT9-DVnq-YjaIun LVM2_member 
/dev/sr0 iso9660 Boot-Repair-Disk 64bit
/dev/zram0 a27e23b5-12b5-4e81-82d8-b5723021642a swap 
/dev/zram1 6574aff0-3e49-49b8-867b-9eba3254a54c swap 
/dev/zram2 989d2566-089f-481a-a41e-b55bcc900e52 swap 
/dev/zram3 77e57a22-8da4-48e5-862f-87140df0727d swap 


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root 9 Feb 11 12:40 ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001 -> ../../sr0
lrwxrwxrwx 1 root root 10 Feb 11 12:41 dm-name-ubuntu--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Feb 11 12:41 dm-name-ubuntu--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Feb 11 12:41 dm-uuid-LVM-AOguRyYkAamTywoUqWOvBWeGMKVkAFpuH0eug0kYMS7eXQI8n2JEsHDPQ3vpKSkV -> ../../dm-0
lrwxrwxrwx 1 root root 10 Feb 11 12:41 dm-uuid-LVM-AOguRyYkAamTywoUqWOvBWeGMKVkAFpuL5HfSt9zt5VzrxFlQuOXK2eEdQSutpgD -> ../../dm-1


========================= "ls -R /dev/mapper/" output: =========================


/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1


================================ Mount points: =================================


Device Mount_Point Type Options


/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sr0 /cdrom iso9660 (ro,noatime)




============================= sda1/grub/grub.cfg: ==============================


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
set root='(ubuntu-vg-root)'
search --no-floppy --fs-uuid --set=root 7ac6de90-7465-4c46-9317-bff2e6db2bbd
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
set timeout=-1
else
set timeout=60
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    linux    /vmlinuz-3.11.0-15-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash $vt_handoff
    initrd    /initrd.img-3.11.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    echo    'Loading Linux 3.11.0-15-generic ...'
    linux    /vmlinuz-3.11.0-15-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.11.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-76-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    linux    /vmlinuz-3.2.0-76-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-76-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-76-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    echo    'Loading Linux 3.2.0-76-generic ...'
    linux    /vmlinuz-3.2.0-76-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-76-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-75-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    linux    /vmlinuz-3.2.0-75-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-75-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-75-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    echo    'Loading Linux 3.2.0-75-generic ...'
    linux    /vmlinuz-3.2.0-75-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-75-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    linux    /vmlinuz-3.2.0-70-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-70-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15893ded-64d9-420b-907a-86831f8417f4
    echo    'Loading Linux 3.2.0-70-generic ...'
    linux    /vmlinuz-3.2.0-70-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-70-generic
}
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on ubuntu-vg-root




Unknown BootLoader on ubuntu-vg-swap_1






=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/2007/mounts) leaked on lvs invocation. Parent PID 21732: bash
File descriptor 63 (pipe:[25990]) leaked on lvs invocation. Parent PID 21732: bash
File descriptor 9 (/proc/2007/mounts) leaked on lvchange invocation. Parent PID 22394: bash
File descriptor 63 (pipe:[25990]) leaked on lvchange invocation. Parent PID 22394: bash
skip_dev_dir: Couldn't split up device name ubuntu-vg-root
Volume group "ubuntu-vg-root" not found
Skipping volume group ubuntu-vg-root
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
File descriptor 9 (/proc/2007/mounts) leaked on lvchange invocation. Parent PID 22394: bash
File descriptor 63 (pipe:[25990]) leaked on lvchange invocation. Parent PID 22394: bash
skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1
Volume group "ubuntu-vg-swap_1" not found
Skipping volume group ubuntu-vg-swap_1
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory


ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-02-11__12h40 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
BLKID BEFORE LVM ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: UUID="15893ded-64d9-420b-907a-86831f8417f4" TYPE="ext2"
/dev/sda5: UUID="XkdnOb-cmqR-0ztU-8fW4-QLT9-DVnq-YjaIun" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="7ac6de90-7465-4c46-9317-bff2e6db2bbd" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="261d12c0-3a89-4492-92ca-f9606b7842bc" TYPE="swap"
/dev/zram0: UUID="a27e23b5-12b5-4e81-82d8-b5723021642a" TYPE="swap"
/dev/zram1: UUID="6574aff0-3e49-49b8-867b-9eba3254a54c" TYPE="swap"
/dev/zram2: UUID="989d2566-089f-481a-a41e-b55bcc900e52" TYPE="swap"
/dev/zram3: UUID="77e57a22-8da4-48e5-862f-87140df0727d" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/2007/mounts) leaked on vgscan invocation. Parent PID 2463: /bin/bash
Reading all physical volumes. This may take a while...
Found volume group "ubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/2007/mounts) leaked on vgchange invocation. Parent PID 2463: /bin/bash
2 logical volume(s) in volume group "ubuntu-vg" now active
File descriptor 9 (/proc/2007/mounts) leaked on lvscan invocation. Parent PID 2463: /bin/bash
LVSCAN:
ACTIVE '/dev/ubuntu-vg/root' [214.18 GiB] inherit
ACTIVE '/dev/ubuntu-vg/swap_1' [16.00 GiB] inherit
Is there RAID on this computer? no
File descriptor 9 (/proc/2007/mounts) leaked on lvs invocation. Parent PID 4444: /bin/sh
File descriptor 9 (/proc/2007/mounts) leaked on vgs invocation. Parent PID 4565: grub-probe
File descriptor 9 (/proc/2007/mounts) leaked on vgs invocation. Parent PID 4565: grub-probe
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s): 32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-root
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


=================== os-prober:
/dev/mapper/ubuntu--vg-root:Ubuntu 12.04.5 LTS (12.04):Ubuntu:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: UUID="15893ded-64d9-420b-907a-86831f8417f4" TYPE="ext2"
/dev/sda5: UUID="XkdnOb-cmqR-0ztU-8fW4-QLT9-DVnq-YjaIun" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="7ac6de90-7465-4c46-9317-bff2e6db2bbd" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="261d12c0-3a89-4492-92ca-f9606b7842bc" TYPE="swap"
/dev/zram0: UUID="a27e23b5-12b5-4e81-82d8-b5723021642a" TYPE="swap"
/dev/zram1: UUID="6574aff0-3e49-49b8-867b-9eba3254a54c" TYPE="swap"
/dev/zram2: UUID="989d2566-089f-481a-a41e-b55bcc900e52" TYPE="swap"
/dev/zram3: UUID="77e57a22-8da4-48e5-862f-87140df0727d" TYPE="swap"


[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-root


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda1recordfail=1/grub/grubenv :
recordfail=1








=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root 4096 Sep 5 14:50 grub.d
total 60
-rwxr-xr-x 1 root root 7806 Dec 6 2013 00_header
-rwxr-xr-x 1 root root 5522 Dec 10 2012 05_debian_theme
-rwxr-xr-x 1 root root 7877 Dec 6 2013 10_linux
-rwxr-xr-x 1 root root 6449 Dec 6 2013 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27 2011 20_memtest86+
-rwxr-xr-x 1 root root 6675 Dec 6 2013 30_os-prober
-rwxr-xr-x 1 root root 1388 Dec 10 2012 30_uefi-firmware
-rwxr-xr-x 1 root root 214 Dec 10 2012 40_custom
-rwxr-xr-x 1 root root 95 Dec 10 2012 41_custom
-rw-r--r-- 1 root root 483 Dec 10 2012 README








=================== mapper/ubuntu--vg-root/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=15893ded-64d9-420b-907a-86831f8417f4 (sda1)


=================== mapper/ubuntu--vg-root/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=f72eb440:a00faf6a:5db799ca:0349c33a name=mirror:1
ARRAY /dev/md/0 metadata=1.2 UUID=43debb14:5374fc55:a8c69b52:c9d71ab8 name=mirror:0


# This file was auto-generated on Mon, 04 Feb 2013 13:09:19 +0000
# by mkconf $Id$






=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda1    : sda,    is-sepboot,    grubenv-ng    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
mapper/ubuntu--vg-root    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/ubuntu--vg-root.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes




=================== parted -l:


Model: VMware Virtual disk (scsi)
Disk /dev/sda: 275GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number Start End Size Type File system Flags
1 1049kB 256MB 255MB primary ext2 boot
2 257MB 275GB 275GB extended
5 257MB 275GB 275GB logical lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 230GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number Start End Size File system Flags
1 0.00B 230GB 230GB ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number Start End Size File system Flags
1 0.00B 17.2GB 17.2GB linux-swap(v1)








Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.




Error: /dev/sr0: unrecognised disk label






Error: /dev/zram0: unrecognised disk label






Error: /dev/zram1: unrecognised disk label






Error: /dev/zram2: unrecognised disk label






Error: /dev/zram3: unrecognised disk label


=================== parted -lm:


BYT;
/dev/sda:275GB:scsi:512:512:msdos:VMware Virtual disk;
1:1049kB:256MB:255MB:ext2::boot;
2:257MB:275GB:275GB:::;
5:257MB:275GB:275GB:::lvm;


BYT;
/dev/mapper/ubuntu--vg-root:230GB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:230GB:230GB:ext4::;


BYT;
/dev/mapper/ubuntu--vg-swap_1:17.2GB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:17.2GB:17.2GB:linux-swap(v1)::;






Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.




Error: /dev/sr0: unrecognised disk label






Error: /dev/zram0: unrecognised disk label






Error: /dev/zram1: unrecognised disk label






Error: /dev/zram2: unrecognised disk label






Error: /dev/zram3: unrecognised disk label




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw)
/dev/mapper/ubuntu--vg-root on /mnt/boot-sav/mapper/ubuntu--vg-root type ext4 (rw)




=================== ls:
/sys/block/dm-0 (filtered): alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered): alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/fd0 (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered): agpgart autofs block bsg btrfs-control cdrom char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dri ecryptfs fb0 fd fd0 full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom ubuntu-vg vga_arbiter vhci vhost-net vmci zero
ls /dev/mapper: control ubuntu--vg-root ubuntu--vg-swap_1
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


=================== df -Th:


Filesystem Type Size Used Avail Use% Mounted on
/cow overlayfs 7.9G 6.3M 7.9G 1% /
udev devtmpfs 7.9G 12K 7.9G 1% /dev
tmpfs tmpfs 1.6G 960K 1.6G 1% /run
/dev/sr0 iso9660 614M 614M 0 100% /cdrom
/dev/loop0 squashfs 549M 549M 0 100% /rofs
none tmpfs 4.0K 0 4.0K 0% /sys/fs/cgroup
tmpfs tmpfs 7.9G 8.0K 7.9G 1% /tmp
none tmpfs 5.0M 0 5.0M 0% /run/lock
none tmpfs 7.9G 0 7.9G 0% /run/shm
none tmpfs 100M 16K 100M 1% /run/user
/dev/sda1 ext2 236M 146M 78M 66% /mnt/boot-sav/sda1
/dev/mapper/ubuntu--vg-root ext4 211G 83G 118G 42% /mnt/boot-sav/mapper/ubuntu--vg-root


=================== fdisk -l:


Disk /dev/sda: 274.9 GB, 274877906944 bytes
255 heads, 63 sectors/track, 33418 cylinders, total 536870912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023592


Device Boot Start End Blocks Id System
/dev/sda1 * 2048 499711 248832 83 Linux
/dev/sda2 501758 536868863 268183553 5 Extended
/dev/sda5 501760 536868863 268183552 8e Linux LVM


Disk /dev/mapper/ubuntu--vg-root: 230.0 GB, 229973688320 bytes
255 heads, 63 sectors/track, 27959 cylinders, total 449167360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000




Disk /dev/mapper/ubuntu--vg-swap_1: 17.2 GB, 17175674880 bytes
255 heads, 63 sectors/track, 2088 cylinders, total 33546240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000




/boot detected. Please check the options.
=================== Advices
Warning: continuing without internet would leave your system unbootable. Please connect internet.
Do you want to continue?




=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would purge (in order to enable-raid enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options: sda1/boot,
Additional repair would be performed: unhide-bootmenu-10s




=================== Advice in case of suggested repair
Warning: continuing without internet would leave your system unbootable. Please connect internet.
Do you want to continue?




=================== User settings
The settings chosen by the user will purge (in order to enable-raid enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options: sda1/boot,
Additional repair will be performed: unhide-bootmenu-60s




/boot added in mapper/ubuntu--vg-root/fstab
Mount sda1 on /mnt/boot-sav/mapper/ubuntu--vg-root/boot
chroot /mnt/boot-sav/mapper/ubuntu--vg-root apt-get -y --force-yes update
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://download.opensuse.org](http://download.opensuse.org) Release: The following signatures were invalid: KEYEXPIRED 1397815516


W: Failed to fetch [http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_12.04/Release](http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_12.04/Release)


W: Some index files failed to download. They have been ignored, or old ones used instead.
Purge the GRUB of mapper/ubuntu--vg-root
grub-pc available


The following extra packages will be installed:
grub-common grub-pc-bin grub2-common
Suggested packages:
multiboot-doc grub-emu xorriso desktop-base
The following packages will be upgraded:
grub-common grub-pc grub-pc-bin grub2-common
4 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
DEBCHECK debOK, grub-pc
DEBCHECK debOK
shim-signed available
linux-signed-generic NOT available (apt-cache policy problem)
Please type: sudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" dpkg --configure -ansudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -fynsudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -y --force-yes dmraidnsudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" dmraid -aynsudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -y --force-yes lvm2nsudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get purge -y --force-yes grub*-common shim-signed


=================== sda1recordfail=1/grub/grubenv :
recordfail=1








=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root 4096 Sep 5 14:50 grub.d
total 60
-rwxr-xr-x 1 root root 7806 Dec 6 2013 00_header
-rwxr-xr-x 1 root root 5522 Dec 10 2012 05_debian_theme
-rwxr-xr-x 1 root root 7877 Dec 6 2013 10_linux
-rwxr-xr-x 1 root root 6449 Dec 6 2013 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27 2011 20_memtest86+
-rwxr-xr-x 1 root root 6675 Dec 6 2013 30_os-prober
-rwxr-xr-x 1 root root 1388 Dec 10 2012 30_uefi-firmware
-rwxr-xr-x 1 root root 214 Dec 10 2012 40_custom
-rwxr-xr-x 1 root root 95 Dec 10 2012 41_custom
-rw-r--r-- 1 root root 483 Dec 10 2012 README








=================== mapper/ubuntu--vg-root/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=15893ded-64d9-420b-907a-86831f8417f4     (sda1)


=================== mapper/ubuntu--vg-rootrecordfail=1/grub/grubenv :
recordfail=1








=================== mapper/ubuntu--vg-root/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=f72eb440:a00faf6a:5db799ca:0349c33a name=mirror:1
ARRAY /dev/md/0 metadata=1.2 UUID=43debb14:5374fc55:a8c69b52:c9d71ab8 name=mirror:0


# This file was auto-generated on Mon, 04 Feb 2013 13:09:19 +0000
# by mkconf $Id$








=================== mapper/ubuntu--vg-root/proc/mdstat :
Personalities :
unused devices: <none>








=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root 4096 Feb 11 12:47 grub.d
total 4
-rwxr-xr-x 1 root root 1588 Nov 27 2011 20_memtest86+




/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=15893ded-64d9-420b-907a-86831f8417f4     (sda1)


=================== mapper/ubuntu--vg-root/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=f72eb440:a00faf6a:5db799ca:0349c33a name=mirror:1
ARRAY /dev/md/0 metadata=1.2 UUID=43debb14:5374fc55:a8c69b52:c9d71ab8 name=mirror:0


# This file was auto-generated on Mon, 04 Feb 2013 13:09:19 +0000
# by mkconf $Id$








=================== mapper/ubuntu--vg-root/proc/mdstat :
Personalities :
unused devices: <none>






Then type: sudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -y --force-yes grub-pc


=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root 4096 Feb 11 12:48 grub.d
drwxr-xr-x 2 root root 4096 Feb 11 12:47 grub.d.bak
total 56
-rwxr-xr-x 1 root root 7806 Sep 17 15:30 00_header
-rwxr-xr-x 1 root root 5522 Sep 17 15:15 05_debian_theme
-rwxr-xr-x 1 root root 7877 Sep 17 15:30 10_linux
-rwxr-xr-x 1 root root 6449 Sep 17 15:30 20_linux_xen
-rwxr-xr-x 1 root root 6675 Sep 17 15:30 30_os-prober
-rwxr-xr-x 1 root root 1388 Sep 17 15:30 30_uefi-firmware
-rwxr-xr-x 1 root root 214 Sep 17 15:30 40_custom
-rwxr-xr-x 1 root root 95 Sep 17 15:30 41_custom
-rw-r--r-- 1 root root 483 Sep 17 15:30 README








=================== mapper/ubuntu--vg-root/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=15893ded-64d9-420b-907a-86831f8417f4     (sda1)


=================== mapper/ubuntu--vg-root/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=f72eb440:a00faf6a:5db799ca:0349c33a name=mirror:1
ARRAY /dev/md/0 metadata=1.2 UUID=43debb14:5374fc55:a8c69b52:c9d71ab8 name=mirror:0


# This file was auto-generated on Mon, 04 Feb 2013 13:09:19 +0000
# by mkconf $Id$








=================== mapper/ubuntu--vg-root/proc/mdstat :
Personalities :
unused devices: <none>






Unhide GRUB boot menu in mapper/ubuntu--vg-root/etc/default/grub


=================== mapper/ubuntu--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root 4096 Feb 11 12:48 grub.d
drwxr-xr-x 2 root root 4096 Feb 11 12:47 grub.d.bak
total 56
-rwxr-xr-x 1 root root 7806 Sep 17 15:30 00_header
-rwxr-xr-x 1 root root 5522 Sep 17 15:15 05_debian_theme
-rwxr-xr-x 1 root root 7877 Sep 17 15:30 10_linux
-rwxr-xr-x 1 root root 6449 Sep 17 15:30 20_linux_xen
-rwxr-xr-x 1 root root 6675 Sep 17 15:30 30_os-prober
-rwxr-xr-x 1 root root 1388 Sep 17 15:30 30_uefi-firmware
-rwxr-xr-x 1 root root 214 Sep 17 15:30 40_custom
-rwxr-xr-x 1 root root 95 Sep 17 15:30 41_custom
-rw-r--r-- 1 root root 483 Sep 17 15:30 README








=================== mapper/ubuntu--vg-root/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=15893ded-64d9-420b-907a-86831f8417f4     (sda1)


=================== mapper/ubuntu--vg-root/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=f72eb440:a00faf6a:5db799ca:0349c33a name=mirror:1
ARRAY /dev/md/0 metadata=1.2 UUID=43debb14:5374fc55:a8c69b52:c9d71ab8 name=mirror:0


# This file was auto-generated on Mon, 04 Feb 2013 13:09:19 +0000
# by mkconf $Id$








=================== mapper/ubuntu--vg-root/proc/mdstat :
Personalities :
unused devices: <none>








*******lspci -nnk | grep -iA3 vga
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]
Subsystem: VMware SVGA II Adapter [15ad:0405]
Kernel driver in use: vmwgfx
00:10.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev 01)
Subsystem: VMware LSI Logic Parallel SCSI Controller [15ad:1976]
*******


grub-install --version
grub-install (GRUB) 1.99-21ubuntu3.17,grub-install (GRUB) 1.


Reinstall the GRUB of mapper/ubuntu--vg-root into the MBR of sda
grub-install /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0


chroot /mnt/boot-sav/mapper/ubuntu--vg-root update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
File descriptor 9 (/proc/2007/mounts) leaked on lvs invocation. Parent PID 18784: /bin/sh
File descriptor 63 (pipe:[25990]) leaked on lvs invocation. Parent PID 18784: /bin/sh


Boot successfully repaired.


You can now reboot your computer.

```

---

### Post by LouisinLondon on 2015-02-11
Trying the Advice from the post starting with
"[COLOR=#333333][FONT=UbuntuRegular]You hit the problem right on the head: the initramfs does not have LVM support. Here's how to fix it:"[/FONT][/COLOR]

[http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd](http://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd)

I get the error when doing:
dpkg -i *.debFATAL: Could not load /lib/modules/3.11.0.26-generic

after reboot still the obnoxious error:
ALERT! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell!

Any advice what's next 

- the server just had reboot required notifications, and VMWare Tools was added, then after reboot this beautiful situation.
Rebuild will be a couple of days job as it's quite a complicated server setup with customised software (so would have that ONLY as the super last resort)

---

### Post by steeldriver on 2015-02-11
Not exactly a solution, but have you tried booting to an older kernel (from the grub menu)?

---

### Post by darkod on 2015-02-11
First, please put the script result from post #1 in CODE tags. It's too long to scroll pasted as it is.

When you activated the lvm with vgchange from live mode, did it look ok? What does vgdisplay and lvdisplay show?

---

### Post by LouisinLondon on 2015-02-11
Hi SteelDriver -> That was the first thing I tried (booting from older Kernels although I didn't try them all...)

all the LVM commands work fine when adding the lvm via apt-get to the Live-Disk
able to mount and all is well...

It just seems that after reboot (even after chrooting and apt-get install lvm on chroot)
 initramfs doesnt have LVM support at the time it's trying to boot.

Any suggestions welcome as to what to try next.
Users have access to the files at the moment as it was a OwnCloud server (amongst many other things) and data is there.. just dont want to rebuild server just for it to happen again

Also Note: 
Don't be confused with the VG-name which is valcri-vg -> I just made it ubuntu-vg in the title to attract/get more generic visits

vgdisplay in Live-CD 
```

root@ubuntu:/home/ubuntu# vgdisplay
  --- Volume group ---
  VG Name               valcri-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               255.76 GiB
  PE Size               4.00 MiB
  Total PE              65474
  Alloc PE / Size       58925 / 230.18 GiB
  Free  PE / Size       6549 / 25.58 GiB
  VG UUID               AOguRy-YkAa-mTyw-oUqW-OvBW-eGMK-VkAFpu

```

lvdisplay in Live-CD
```

root@ubuntu:/home/ubuntu# lvdisplay
  --- Logical volume ---
  LV Name                /dev/valcri-vg/root
  VG Name                valcri-vg
  LV UUID                H0eug0-kYMS-7eXQ-I8n2-JEsH-DPQ3-vpKSkV
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                214.18 GiB
  Current LE             54830
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/valcri-vg/swap_1
  VG Name                valcri-vg
  LV UUID                L5HfSt-9zt5-Vzrx-FlQu-OXK2-eEdQ-SutpgD
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                16.00 GiB
  Current LE             4095
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1



```

We believe the /boot had filled up (common problem with Ubuntu - wish the coders can introduce a checking of space before doing anything there..)

---

### Post by steeldriver on 2015-02-11
So did the chrooted update-initramfs succeed or fail? what is the exact usage level of /mnt/boot (using df)?

---

### Post by LouisinLondon on 2015-02-12
Hi SteelDriver 

Along with an academic I roped in we managed to fix the problem.

To answer your Question:
update-initramfs did give errors but only on some Kernels but since we only wanted to boot on some of the later ones we first thought it's not the issue (which it was).

In a nutshell this Academic writing board sums it up:
[https://www.dropbox.com/s/4x1nqsvlhg01yqs/initramfs-issue-booting.JPG?dl=0](https://www.dropbox.com/s/4x1nqsvlhg01yqs/initramfs-issue-booting.JPG?dl=0)

so after installing lvm on live disk and chrooting,
then had to remove 3.11.10-26,24,10 etc

the in teh chrooted environment 
dpkg -i lvm2*.deb - > the deb file copied from the LiveDisk lvm install caches area previously.

Thanks for the help though.



[COLOR=#000000]



[/COLOR]

---

### Post by steeldriver on 2015-02-12
OK thanks for the update

It might have been helpful to have included the errors in your original post. I must admit I was a bit puzzled why you were doing update-initramfs **-a** instead of the more usual update-initramfs **-u** (since the former would seem possible to leave you without any working image if it goes wrong). But I'm no expert on that kind of thing.

Glad you are up and running again

---

### Post by LouisinLondon on 2015-02-13
Hi SteelDriver - indeed the errors would have been useful

because they were for kernels I weren't interested in I ignored them
this was the error:

FATAL module not found /lib/modules/3.11.0-24 

solution was 
apt-get remove linux-image-3.11.10.-24

apt-get update
apt-get install linux-image-3.11.10.-24

dpkg -i lvm*.deb (as copied previously from Live Disk as mentioned previously)

---

