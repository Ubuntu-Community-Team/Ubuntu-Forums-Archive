---
title: "hd0, msdos1 not found error"
date: 2015-10-21
forum: Server Platforms
---

### Post by Mayte on 2015-10-21
Hello,

I am not an Ubuntu expert, lets start from there. I have an IBM x3550 server with Ubuntu 14, Gnome running Nagios Core since January this year.

Monday somehow heater started and office temperature was high ( nobody was there)causing the server to roar like an animal. When I came back, turned on AC and decided to turn off the server by software, means logged in select power/shut-down. Next morning the server is not booting up. After booting Kernel it prompts the GRUB menu. After some research I typed ls and ls -l and this is what I'm getting.

grub> ls
(hd0) (hd0,msdos5) (hd0,msdos1)
grub> ls (hd0, msdos5)/
error: disk 'hd0,msdos1' not found.
grub> ls (hd0, msdos1)/
error: disk 'hd0,msdos1' not found.
grub> ls -l
Device hd0: No known filesystem - Sector size 512B - Total size 97....kib
	Partition hd0, msdos5: No known filesystem detected - partition start at 250...kib -total size 97....kib
	Partition hd0, msdos1: Filesystem type ext* - Last modification time 2015-10-19 .....

Can I recover my installation somehow? What else can I do?
Please help:icon_frown:#-o

Thanks

---

### Post by oldfred on 2015-10-21
Are you using RAID or LVM, or just standard partitioning.

You may need live installer, so you can boot it and run repairs. Run fsck on all ext* partitions.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If RAID or LVM instructions are a lot different and I do not know details.

---

### Post by darkod on 2015-10-21
Was there any specific message why it doesn't want to boot normally?

At that grub> prompt, try this:
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot
```

Does that boot the machine?

---

### Post by Mayte on 2015-10-21
Yes I am using RAID

---

### Post by Mayte on 2015-10-21
Hi Darko,

There wasn't any specific message.
I tried the code you are suggesting but after typing the second line it returns:
error: file '/vmlinuz' not found.

?

---

### Post by darkod on 2015-10-21
Hardware raid from the machine or software raid with linux mdadm package?

---

### Post by Mayte on 2015-10-21
hardware raid from the machine

---

### Post by darkod on 2015-10-21
Did you check in the raid BIOS if the array is still good? Maybe it got messed up with the heat issue?

When it's HW raid the ubuntu OS sees it as single disk, so the commands should also work. Maybe the /vmlinuz symlink is not working in your system. At the grub prompt try also listing what it has on partition #1:
```
ls (hd0,1)/
ls (hd0,1)/boot
```

Lets try to see which kernels you have in the /boot folder.

---

### Post by Mayte on 2015-10-21
Hi Darko,
Can we continue tomorrow? I have to finish something else and leave for the day.
I will check the RAID tomorrow morning as far as I remembered when the server starts it recognizes the RAID, but I will check again.
The last code you suggested didn't succeed.
   thanks 

Myt

---

### Post by Mayte on 2015-10-28
Hi Darko,
We have been very busy this week sorry for the delay.
 
Going back to your question  "[COLOR=#000000]There wasn't any specific message." [/COLOR]when server gets to the GRUB menu if I select Ubuntu*, it returns several lines but in the first line says ....Kernel panic.... , then reading about this I ran the bootinfoscript from a liveCD and results are as follow:


============================= Boot Info Summary: ===============================
 
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    in partition 112 for.
 
sda1: __________________________________________________________________________
 
    File system:       ext2
    Boot sector type:  -
    Boot sector info:
    Operating System: 
    Boot files:        /grub/grub.cfg
 
sda2: __________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  FAT16
    Boot sector info:
 
sda5: __________________________________________________________________________
 
    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:
 
JVFubuntu-vg-root': ____________________________________________________________
 
    File system:      
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
 
JVFubuntu-vg-swap_1': __________________________________________________________
 
    File system:      
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 1000.0 GB, 1000026931200 bytes
255 heads, 63 sectors/track, 121579 cylinders, total 1953177600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 1,953,175,551 1,952,673,794   5 Extended
/dev/sda5             501,760 1,953,175,551 1,952,673,792  8e Linux LVM
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              squashfs  
/dev/mapper/JVFubuntu--vg-root 7ae16d66-5fbf-4be7-a216-f019fb13aa4d   ext4      
/dev/mapper/JVFubuntu--vg-swap_1 d0da144e-f338-4c2a-b670-f4c2343c19e2   swap      
/dev/sda1        107f701c-6476-419a-90a0-dd983a57edb7   ext2      
/dev/sda5        CsdiCy-yRPh-LAYf-MVy4-tDv9-1AlP-l1LDme LVM2_member
/dev/sr0                                                iso9660    Ubuntu 14.04.3 LTS amd64
 
========================= "ls -R /dev/mapper/" output: =========================
 
/dev/mapper:
control
JVFubuntu--vg-root
JVFubuntu--vg-swap_1
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/107f701c-6476-419a-90a0-dd983a57edb7 ext2       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
 
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

There is more info, in case needed. What can I do now??

Thanks in advance

Myt

---

### Post by darkod on 2015-10-28
Look at my previous post #8 and try to post the output of those ls commands. Lets see if it shows any kernels and where...

---

### Post by Mayte on 2015-11-05
Hello team,

Thanks everyone for your time, my problem was very simple to fix, but lack of knowledge is terrible in this cases. 

when I boot the server, it was going to the GNU Grub menu which has 4 options. Second option is Advance options for ubuntu, select that and voila I got all the previous versions of kernel that ubuntu keeps just in case. I selected the generic one previous to my latest in this case 54 and guru magic My server is back to live!:p

Of course the boot partition is full I have to correct that now.

Thanks everyone for your time and I hope this may help others like me.

have a great dayyyyyyyyyyyyy

---

