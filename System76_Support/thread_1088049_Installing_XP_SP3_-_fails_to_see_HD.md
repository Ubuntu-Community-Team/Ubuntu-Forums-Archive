---
title: "Installing XP SP3 - fails to see HD"
date: 2009-03-05
forum: System76 Support
---

### Post by Trevor Bramble on 2009-03-05
I finally got around to buying a new drive and installing 64-bit 8.10.  Everything's running well enough (except Jdeveloper, which is typical) but now I'm trying to add Windows so I can use some games that are just too sluggish under Wine and I'm blocked solidly before the install even starts.

I actually tried installing Windows first, to make everything easier, but didn't have time to waste on this problem and wasn't getting anywhere with it.

What happens is, I start up with the Windows install disc (slipstreamed SP3, actually) and when it gets to the point where it should ask me how to handle putting Windows on the hard disk, it says it couldn't find one.

I theorized maybe it just lacked drivers, but when hitting F6 to indicate I might have some tasty new drivers for it to use, it said there was no hard disk available for it to apply them.

Wot?

(Edit: I suppose I should mention this is a Serval Pro 3...)

---

### Post by thomasaaron on 2009-03-05
Hi, Trevor.

Try disabling AHCI in your BIOS.

If that doesn't work, you can slipstream SATA drivers into the install disk. There are a number of tutorials out there on this. Let me know if disabling AHCI doesn't work, and I'll help you find a good one.

---

### Post by Trevor Bramble on 2009-03-05
Disabling AHCI did the trick!

Still having trouble, though.  Window is fully installed and I juggled he MBR as per the wiki [[https://help.ubuntu.com/community/WindowsDualBoot]](https://help.ubuntu.com/community/WindowsDualBoot]) but when I attempt to select XP from grub, I get a message about autocheck and a BSoD. 

Google has provided some clues but none of them have panned out.

---

### Post by Trevor Bramble on 2009-03-05
Further, more terrifying troubles have arisen.

Grub is now spitting out error 17 at boot.  I can't boot Windows OR Linux.

I'm not sure what changed.  But I believe some of the grub commands I came across in my efforts to solve the above problem are the cause.

[This thread]("http://ubuntuforums.org/showthread.php?t=1069546") linked to a neat script for spitting out a bunch of (hopefully) helpful information.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub0.97 in the file /mbr.bin looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on the same 
                       partition for /boot/grub/stage2.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000905d6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    97,659,134    97,659,072  83 Linux
/dev/sda2          97,659,135   976,768,064   879,108,930   5 Extended
/dev/sda5          97,659,198    97,916,174       256,977  92 Unknown
/dev/sda6          97,916,238   488,536,649   390,620,412  93 Amoeba/Accidently Hidden Linux
/dev/sda7         488,536,713   976,768,064   488,231,352  93 Amoeba/Accidently Hidden Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="526893C66893A6EF" TYPE="ntfs" 
/dev/sda5: UUID="b5c638e7-f121-4e44-b9a8-cacbbde5f57b" TYPE="swap" 
/dev/sda6: UUID="391c4804-852e-4040-8cdd-6cb65b2e3c7e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="6be36281-6d3f-4108-ba77-295e132cae5b" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6be36281-6d3f-4108-ba77-295e132cae5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6be36281-6d3f-4108-ba77-295e132cae5b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6be36281-6d3f-4108-ba77-295e132cae5b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6be36281-6d3f-4108-ba77-295e132cae5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6be36281-6d3f-4108-ba77-295e132cae5b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6be36281-6d3f-4108-ba77-295e132cae5b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6be36281-6d3f-4108-ba77-295e132cae5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6be36281-6d3f-4108-ba77-295e132cae5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6be36281-6d3f-4108-ba77-295e132cae5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6be36281-6d3f-4108-ba77-295e132cae5b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6be36281-6d3f-4108-ba77-295e132cae5b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=6be36281-6d3f-4108-ba77-295e132cae5b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=391c4804-852e-4040-8cdd-6cb65b2e3c7e /home           ext3    relatime        0       2
# /dev/sda5
UUID=b5c638e7-f121-4e44-b9a8-cacbbde5f57b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 446.6GB: boot/grub/menu.lst
 446.5GB: boot/grub/stage2
 446.5GB: boot/initrd.img-2.6.27-11-generic
 446.5GB: boot/initrd.img-2.6.27-7-generic
 446.5GB: boot/vmlinuz-2.6.27-11-generic
 446.5GB: boot/vmlinuz-2.6.27-7-generic
 446.5GB: initrd.img
 446.5GB: initrd.img.old
 446.5GB: vmlinuz
 446.5GB: vmlinuz.old
```

If it's not "fdisk /mbr", I'm just not sure what to do at this point.

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> Further, more terrifying troubles have arisen.

Grub is now spitting out error 17 at boot.  I can't boot Windows OR Linux.
...
If it's not "fdisk /mbr", I'm just not sure what to do at this point.

If I remember correctly then Error 17 has to do with the BIOS drive layout being different, it's possible that switching the AHCI option caused that - you could try switching it back.

---

### Post by Lee_Machine on 2009-03-06
In dont know about the BIOS in your laptop, but for the Pangolin in BIOS there is an option that asks what OS you us. Windows XP has to be selected in order to boot properly.

---

### Post by Lee_Machine on 2009-03-06
Also the instructions you found are different from the ones from the S76 web site.
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

The S76 ones worked just fine for me with WindowsXP SP3

---

### Post by Trevor Bramble on 2009-03-06
Thanks for your help guys.

I actually did try switching AHCI back, but it didn't change anything (I've since turned it off again).

There isn't any option in the SerP3 BIOS for OS, so unfortunately that's not the answer either.

The trouble with any of the grub recovery attempts I see is that none of them appear to know how I should handle what happens here:
```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

**Error 17: Cannot mount selected partition**
grub> quit
quit
```

Now what? =^(

---

### Post by Trevor Bramble on 2009-03-06
Here's what really confuses me.  Everything I did should be reversible.

I followed the Ubuntu wiki instructions as mentioned above, where dd is used to create the backup of the mbr.  Likewise I copied menu.lst to menu.lst.working before modification.

Replacing mbr.bin and menu.lst does NOTHING.  No change!  Why not??

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> Here's what really confuses me.  Everything I did should be reversible.

I followed the Ubuntu wiki instructions as mentioned above, where dd is used to create the backup of the mbr.  Likewise I copied menu.lst to menu.lst.working before modification.

Replacing mbr.bin and menu.lst does NOTHING.  No change!  Why not??

1) Are you sure that's the correct partition?
2) Is the partition no-longer marked bootable?

---

### Post by Trevor Bramble on 2009-03-06
> 1) Are you sure that's the correct partition?
Partition table was modified during Windows install (first partition was destroyed and recreated and formatted) but Ubuntu was booting fine after that.  Otherwise there have been no partition table changes.

> 2) Is the partition no-longer marked bootable?
Good question.  It's been years since I've looked at that.  How should I check?

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> Partition table was modified during Windows install (first partition was destroyed and recreated and formatted) but Ubuntu was booting fine after that.  Otherwise there have been no partition table changes.


Good question.  It's been years since I've looked at that.  How should I check?

If your first partition was destroyed to make room for windows then (hd0,0) is NOT the location of GRUB, you need to tell GRUB exactly which partition has the GRUB configuration files.  If you know which linux partition that is then you can use the pattern:
/dev/sda1 => (hd0,0)
/dev/sdc6 => (hd2,5)

You can check whether the partition is bootable by using the Partition Editor on the Live CD, it's in the System | Administration menu.

---

### Post by Trevor Bramble on 2009-03-06
> If your first partition was destroyed to make room for windows then (hd0,0) is NOT the location of GRUB
I hope I wasn't misunderstood.  Before Windows, I had the following:

Primary:
50 GB NTFS (awaiting windows)
Extended:
128 MB Swap
200 GB Ext3
250 GB Ext3

Give or take a little on those sizes.

Windows complained that the 50 GB partition was unusable during install so I deleted it at that time and created it again, following through with a quick format and the rest of the install.

So, the partition table should not have changed, right?

Swapping hard disks to check bootable flag now...

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> I hope I wasn't misunderstood.  Before Windows, I had the following:

Primary:
50 GB NTFS (awaiting windows)
Extended:
128 MB Swap
200 GB Ext3
250 GB Ext3

Give or take a little on those sizes.

Windows complained that the 50 GB partition was unusable during install so I deleted it at that time and created it again, following through with a quick format and the rest of the install.

So, the partition table should not have changed, right?

Swapping hard disks to check bootable flag now...

Your partition layout has not changed but if you're trying to instruct GRUB to use (hd0,0) as the location for the configuration files then it will fail.  NTFS and Swap partitions cannot contain the GRUB configuration files, GRUB cannot mount these partition types.  So, to fix this you need to tell GRUB to use either of your Ext3 partitions (whichever one has the /boot/grub/ folder).

---

### Post by Trevor Bramble on 2009-03-06
You were right that sda7 was missing the boot flag, which was applied to the NTFS partition (sda1).  That was corrected and on reboot I encountered the same error.

> Your partition layout has not changed but if you're trying to instruct GRUB to use (hd0,0) as the location for the configuration files then it will fail. NTFS and Swap partitions cannot contain the GRUB configuration files, GRUB cannot mount these partition types. So, to fix this you need to tell GRUB to use either of your Ext3 partitions (whichever one has the /boot/grub/ folder).

/ (including /boot) is mounted on sda7 (250GB Ext3)

From the live CD:
```
grub> root (hd0,6)
root (hd0,6)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub>
```

---

### Post by Trevor Bramble on 2009-03-06
Should I just re-install Ubuntu?  I've got work to do.

I can tell the installer not to overwrite my partition where /home is mounted, right?  And Windows is already installed so the installer will sort out all the boot configuration needs and but everything where it needs to be, right?

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> Should I just re-install Ubuntu?  I've got work to do.

I can tell the installer not to overwrite my partition where /home is mounted, right?  And Windows is already installed so the installer will sort out all the boot configuration needs and but everything where it needs to be, right?

GRUB problems are fixable, personally I recommend using google until you get the commands correct and get it going.

Things I've remembered doing in the past:
1) Using "find /boot/grub/stage1" to have GRUB search for the correct partition.
2) Using the GRUB repair option on the Live CD startup menu (I don't remember what it's called exactly though)
3) Using "sudo fdisk -l /dev/sda" to double check that the partition type is correct (ext3 is partition Id 83), for some reason I've had to re-set the partition type before - I thought it was really odd as I did not remember changing it.

Edit: Important Note -> LVM uses a different Id, if you have that enabled.

---

### Post by Trevor Bramble on 2009-03-06
> GRUB problems are fixable, personally I recommend using google until you get the commands correct and get it going.

Of course.  I've been all over Google and these forums.  Everyone says the same couple of things and I haven't been able to get any of it to work for me.

> 1) Using "find /boot/grub/stage1" to have GRUB search for the correct partition.
```
grub> find /media/disk/boot/grub/stage1
find /media/disk/boot/grub/stage1

Error 15: File not found
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub>
```

> 2) Using the GRUB repair option on the Live CD startup menu (I don't remember what it's called exactly though)
I thought I remembered something like that too, but I can't find anything on my 8.10 amd64 CD here.

> 3) Using "sudo fdisk -l /dev/sda" to double check that the partition type is correct (ext3 is partition Id 83), for some reason I've had to re-set the partition type before - I thought it was really odd as I did not remember changing it.

UHM.  Well I'm confused:
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000905d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2            6080       60801   439554465    5  Extended
/dev/sda5            6080        6095      128488+  92  Unknown
/dev/sda6            6096       30410   195310206   93  Amoeba
/dev/sda7   *       30411       60801   244115676   93  Amoeba
```
Amoeba?! And the first partition is "Linux"??

This is all wrong.  Why do they all look OK in GParted but not here??

In GParted they're:
/dev/sda1     ntfs
/dev/sda2     extended
  /dev/sda5   linux-swap
  /dev/sda6   ext3
  /dev/sda7   ext3

---

### Post by compholio on 2009-03-06
> **Trevor Bramble said:**
> ...
UHM.  Well I'm confused:
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000905d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2            6080       60801   439554465    5  Extended
/dev/sda5            6080        6095      128488+  92  Unknown
/dev/sda6            6096       30410   195310206   93  Amoeba
/dev/sda7   *       30411       60801   244115676   93  Amoeba
```
Amoeba?!

HA-HA! That's it, please run "sudo fdisk /dev/sda" and type "p" (enter) to list partitions (it should show the same list).  Now repeat the following for each parition:
1) Type "t" (command to "change partition type") and hit enter
2) Type the number of the partition to edit and then hit enter
3) Type the hex code of the CORRECT partition type and then hit enter
when done type "p" (enter) again to confirm the new partition types, if they are correct then type "w" (enter) to write the new information (there is no turning back after you do this, but your partition table is obviously borked).

hex codes for the partition types you care about:
7 NTFS
82 Linux Swap
83 Linux (Ext3)

Edit: Reason: GParted using the filesystem information (higher priority) in addition to the partition table information.
Edit: for you the exact sequence SHOULD be:
t
1
7
t
5
82
t
6
83
t
7
83
p
-> make sure everything is OK
w

---

### Post by Trevor Bramble on 2009-03-06
Sorry, should've mentioned before rebooting that I'd found a post (keyword was "amoeba"!) that [described exactly what you just posted]("http://www.3till7.net/2007/10/25/grub-error-17/").

So now I'm in my shiny new Ubuntu.  Windows, however, still won't boot.  Sat at "Starting Up..." message or whatever it was for about half an hour while the CEO chatted with me from the other side of the display. ;^)

Thanks for all your help, compholio.  I'm very relieved to have my workspace available again without having to redo the hours of work I'd already put into it this week.

(Edit: Windows now boots after putting in the correct partition info in menu.lst--forgot to re-apply my edits earlier.)

---

### Post by Trevor Bramble on 2009-03-06
OK I think this is all wrapped up.  Let's see if I can summarize it all for any who follow.

**AHCI is disabled.** - This is probably what started the whole thing.

**Don't use hide() unhide() in grub/menu.lst** - This is what got me in trouble with the partition type ids.

**Windows partion has BOOT flag** - I'm not sure this is meaningful, as Ubuntu booted without this scenario.

I followed the wiki instructions where they suggest using dd to archive and replace the master boot record.  This is probably spot-on, and I only ran into trouble when I didn't understand why Windows wasn't booting (AHCI was enabled) and started trying the grub commands posted in another section of that same wiki page, and many other places 'round the web, which included use of hide() and unhide() and that's where the partition ids were changed as a side-effect.

---

