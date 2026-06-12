---
title: "rescue vm from unbootable host"
date: 2010-06-22
forum: Virtualisation
---

### Post by aidanewen on 2010-06-22
Hi,

I've a Hardy / Zimbra mailserver running on a 10.04 host. The host was unplugged last night and won't reboot. I've booted in from CD in rescue mode and I'm save a backup of my vm (I know - I should have had one already!).

I want to be sure that I'm not missing anything I've got


[LIST=1]
[*]/etc/libvirt
[*]the source file listed in my qemu xml file (mine is /virtualMachines/mail.qcow2)
[/LIST]
Is there anything else I need in order to recreate my vm should I fail to rescue my host?

Thanks in advance,

Aidan

---

### Post by wilee-nilee on 2010-06-22
> **aidanewen said:**
> Hi,

I've a Hardy / Zimbra mailserver running on a 10.04 host. The host was unplugged last night and won't reboot. I've booted in from CD in rescue mode and I'm save a backup of my vm (I know - I should have had one already!).

I want to be sure that I'm not missing anything I've got


[LIST=1]
[*]/etc/libvirt
[*]the source file listed in my qemu xml file (mine is /virtualMachines/mail.qcow2)
[/LIST]
Is there anything else I need in order to recreate my vm should I fail to rescue my host?

Thanks in advance,

Aidan

First from a Live cd you can get into the host. Post the boot script in my signature, posted in code tags, unless your quite sure it's not salvageable.

The vdi file in the Vm if it's Vbox probably has all your info on it copy it out, and see if it will run in another virtual. Don't remove it from the host just copy it and the rest of the files in the folder.

---

### Post by aidanewen on 2010-06-22
I've used kvm rather than vbox (and I don't actually have another host to try my vm on).

Here's the bootscript results: 


```

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

md2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  fd Linux raid autodetect
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   468,520,959   468,518,912  fd Linux raid autodetect
/dev/sdb2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdb5         468,523,008   488,396,799    19,873,792  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32     3,915,775     3,915,744   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         6369978a-f1a1-4b0d-93a2-9140c0ea3164   ext4                                     
/dev/md1         2ec9fcc1-fbfc-4c36-b925-bc5dba8986f9   swap                                     
/dev/md2         7aa6ee0b-0623-4966-8f19-fe4312184b2c   ext4                                     
/dev/sda1        50078b28-2aa9-71aa-c276-026de5455028   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cc5c5487-1894-70c1-b2a1-47ece0433c2d   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        50078b28-2aa9-71aa-c276-026de5455028   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cc5c5487-1894-70c1-b2a1-47ece0433c2d   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2a65507e-9820-43dc-5cfd-fe3c9fdbdff5   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2a65507e-9820-43dc-5cfd-fe3c9fdbdff5   linux_raid_member                               
/dev/sdd: PTTYPE="dos" 
/dev/sde1        EC88-0B7F                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/external          vfat       (rw)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.32-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    linux    /boot/vmlinuz-2.6.32-22-server root=UUID=6369978a-f1a1-4b0d-93a2-9140c0ea3164 ro   quiet
    initrd    /boot/initrd.img-2.6.32-22-server
}
menuentry 'Ubuntu, with Linux 2.6.32-22-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    echo    'Loading Linux 2.6.32-22-server ...'
    linux    /boot/vmlinuz-2.6.32-22-server root=UUID=6369978a-f1a1-4b0d-93a2-9140c0ea3164 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=6369978a-f1a1-4b0d-93a2-9140c0ea3164 ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    echo    'Loading Linux 2.6.32-21-server ...'
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=6369978a-f1a1-4b0d-93a2-9140c0ea3164 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 6369978a-f1a1-4b0d-93a2-9140c0ea3164
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=6369978a-f1a1-4b0d-93a2-9140c0ea3164 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=2ec9fcc1-fbfc-4c36-b925-bc5dba8986f9 none            swap    sw              0       0

UUID=b4b916cf-b6e8-4275-99c3-7c9d813ccb5e    /media/office    auto    defaults    0    2

==================== md0: Location of files loaded by Grub: ====================


  68.9GB: boot/grub/core.img
  73.4GB: boot/grub/grub.cfg
  69.0GB: boot/initrd.img-2.6.32-21-server
  70.9GB: boot/initrd.img-2.6.32-22-server
  94.7GB: boot/vmlinuz-2.6.32-21-server
  86.3GB: boot/vmlinuz-2.6.32-22-server
  70.9GB: initrd.img
  69.0GB: initrd.img.old
  86.3GB: vmlinuz
  94.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 02 00  |.<.MSWIN4.1..@..|
00000010  02 00 02 00 00 f8 ef 00  20 00 80 00 20 00 00 00  |........ ... ...|
00000020  e0 bf 3b 00 00 00 29 7f  0b 88 ec 4e 4f 20 4e 41  |..;...)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200




```

---

### Post by aidanewen on 2010-06-22
I'm really keen to ensure that, assuming it's not corrupt, I saved my vm when I backed up my mail.qcow2 file. Will that contain all I need to run my virtual machine on a new host?

I'm not confident of my ability to restore my host, so I want to be certain everything I need is backed up before I mess around with my host.

---

### Post by aidanewen on 2010-06-22
This is the output I get when I try to boot from my hard drive:

```
    fsck from util-linux-ng 2.17.2
  /dev/md0: Superblock last mount time (Tue Jun 22 13:50:36 2010,
                  Now = Mon Jul 6 03:46:05 2009) is in the future.
   
  /dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
  mountall: fsck / [466] terminated with status 4
  mountall: Filesystem has errors: /
  
```

I'm not sure what this means...

---

### Post by aidanewen on 2010-06-23
I've decided I really need to get everything back online. I've backed up everything I can find thats not corrupted. I'm going to rebuild the host and hope the vm is still intact. Thanks for your help.

---

