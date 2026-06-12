---
title: "Problems installing Areca raid controller in 8.10"
date: 2009-02-24
forum: Server Platforms
---

### Post by MountainX on 2009-02-24
The Ubuntu installer sees the drives on my Areca 1220 sata raid card and I can partition/format them. I put my boot partition on one of the drives on the Areca. When I remove the installation CD, Ubuntu won't boot because it can't find the boot partition. The grub command line "find" finds nothing.

After googling this for a while, I see the same issue - but with Dapper, not the current version. For example: [https://launchpad.net/ubuntu/+source/hw-detect/+bug/40075](https://launchpad.net/ubuntu/+source/hw-detect/+bug/40075)

I can't figure out why I am having a problem that has been reported to have been solved a long time ago. Maybe my problem is a little different...

Anyone want to help me figure it out? I'm not sure what to do next.

I don't want to use the Live CD because I've been sitting here waiting for it to boot up for about half an hour. I have no idea what is wrong with it. I usually use the alternate CD and I prefer it.

So how can I trouble shoot this with the alternate CD? THanks.

**_[COLOR="Red"]UPDATE:[/COLOR]_**
See [this thread]("http://ubuntuforums.org/showthread.php?t=1080832") for more information. This problem is probably NOT due to the Areca controller.

---

### Post by fjgaude on 2009-02-24
First thing: can you show us your **/boot/grub/menu.lst** file?

As you say **grub** is not getting put on the boot drive. Did you put a partition table on that drive? Using **cfdisk**, **parted**, etc.?

You are not using the raid card to create an array, eh?

---

### Post by MountainX on 2009-02-24
I partitioned the drive with the alternate installer. I made a /boot partition and formatted it. I completed the install and then I rebooted. The computer fails to boot - it doesn't find an operating system.

The problem is that Ubuntu is not seeing the partition on the disk attached to the Areca controller after the install finishes.

It doesn't matter whether I make a RAID array or use JBOD, as I am doing now, Ubuntu will not boot from a disk attached to this controller.

I cannot find the /boot/grub/menu.lst file.

questions:
1. how do I start grub from the alternate CD?
2. once I am in grub, what do I do when the find command returns doesn't find anything? (I think it doesn't find anything because Ubuntu isn't seeing the /boot partition.)

Thank you.

---

### Post by MountainX on 2009-02-24
more info:
when I use the alternate installer CD and enter rescue mode, I am presented with a list of all hard drives.

My root and /boot partitions are on sdc. Here's some info:
SCSI2	(0,5,0)	WDC WD740GD-00FLC0	Areca 1220	passthru
sdc1	/boot	296.1M	
sdc2	/root	74.1G

when the rescue app asks me to select a device for the root file system, I select sdc2.

It fails with this message:
rescue-mode: selected root device '/dev/sdc2'
rescue: umount: cannot umount /target: invalid argument
rescue: mount: mounting /dev/sdc2 on /target failed: Device or resource busy

I imagine solving that issue will get me one step closer...

---

### Post by fjgaude on 2009-02-24
Where is your / partition?

Why are you using the alt CD and not the liveCD? Okay, I guess you wish to make custom partitions, eh?

I think you don't have the MSDOS or GPT partition tables installed. You can do that with **fdisk**. I use **cfdisk** as it is much easier to use, not much to remember in terms of command line parameters.

What you are doing I've not done before... it could be something to do with the raid card but you would think you could get results in JBOD as simply a controller.

While you are in the alt CD you likely can install **grub** if it is not there already with apt-get:

```
apt-get install grub
```

Then do:

```
grub-install /dev/hdc
```

```
grub
grub>root (hd2,0)
grub>setup (hd2)
quit
```
```

grub-install /dev/hdc
```

Now, consider the hd0, is it the first drive... I can't say. If it is the third drive then leave the hd2. You might want to read the **man** pages for grub.

---

### Post by MountainX on 2009-02-24
> **fjgaude said:**
> Where is your / partition?

Why are you using the alt CD and not the liveCD? Okay, I guess you wish to make custom partitions, eh?


The first time I tried to install Ubuntu (a year ago), the Live CD wouldn't work and I had to use the alt CD. Since that time I have found the alternate CD to be faster and easier.

On this server I have to encrypt several different partitions, so yes, the alternate CD is the best. I did try to boot up with a Live CD and it hung (black screen with blinking cursor), so I don't think I have a choice.

I have the alternate CD and the Super Grub disk available.

> **fjgaude said:**
> 
While you are in the alt CD you likely can install **grub** if it is not there already with apt-get:

Unfortunately, apt-get and aptitude are not available at the command line from the alt CD, so I guess I can't install anything.

Not sure what to do next...

---

### Post by MountainX on 2009-02-24
> **fjgaude said:**
> Where is your / partition?


I listed it above (but I called it /root, just to make it easier to read, or so I thought).

/ is on sdc2

---

### Post by fjgaude on 2009-02-24
Okay, / is base of filesystem with /root a directory off the base. <smile>

You seem to be in a box... the liveCD would permit you to do what needs to be done... I don't use the alternate enough to remember how to get you going.

Seems you may not have an MBR else grub would have been installed and you could boot...

I'll sleep on it overnight and see if anything comes up.

---

### Post by MountainX on 2009-02-24
> **fjgaude said:**
> Okay, / is base of filesystem with /root a directory off the base. <smile>



I appreciate your feedback and help.

When I was typing the prior post, I started to just type "/" and I changed my mind and intended to type "root", but the result was "/root" (a typo).

I do have an option that I know will solve this -- reinstall. The problem I have is that there are 10 hard drives and more than a dozen partitions. Most of these partitions are LVM + encrypted. It takes a long time to redo all that (custom mount points, non-default options, etc.). I have already redone it several times and I just don't want to do that again. It gets old after spending more than 150 hours installing Ubuntu on one computer...

And other potential solutions are difficult because of the encrypted volumes. So installing again might be the only reasonable choice.

I'm not sure if it will interest anyone, but here is the back story.

I was forced to do the most recent reinstall after the Samsung HD103UJ drives proved incompatible with the Areca 1220 controller. I thought setting them up as JBOD would eliminate that problem but it didn't. (Previously I had installed Ubuntu with these drives in various RAID configurations, each time running into problems.)

After the most recent drive/controller problem, I moved all the Samsung drives to another controller, but that caused me to move the Ubuntu OS drives to the Areca controller and hence, this new issue came up. This issue is surely a bug. This must be an incompatibility between this hardware and Ubuntu. I have tried so many different combinations with this hardware and installed Ubuntu so many times on it that I know something unusual is happening as a result of booting from this controller.

I can resolve this just by moving the partitions around and making sure that the boot partition is not on a drive attached to the Areca controller. It is a couple more hours of work, but it will definitely solve the issue.

I wanted to just move the boot partition to another drive and avoid reinstalling, but I actually could have reinstalled everything by now if I had just gone ahead and done it.

---

### Post by fjgaude on 2009-02-25
You have a MBR on /sdc, the boot drive. Grub is there, or it should be. There should be a /boot/grub/menu.lst file... I think I don't have any recommendations other than a complete re-install.

With ten drives and so many partitions things have gone adrift.

Good luck in whatever you do, try.

---

### Post by MountainX on 2009-02-25
Thank you again. I should probably file a bug report... 

Having installed Ubuntu so many times on this hardware, I can say that the issue isn't having a lot of drives or partitions. The issue is putting the boot partition on the Areca controller. That's the only time the problem happens (and it is reproducible). 

So I know the cause of the problem, and (originally) I was just hoping to be able to move the boot partition without doing a complete reinstall. But no big deal. I've learned some good things, including the tips you shared with me in this thread.

---

### Post by fjgaude on 2009-02-25
Sometimes things don't go as we plan... but we can always find a way toward success.

---

### Post by MountainX on 2009-02-25
I'm humbled and I have to admit that I have no idea why my system will not boot now. I have reinstalled Ubuntu a bunch of times today and what seemed clear about this problem is no longer clear.

So starting from the beginning, here is menu.lst. 

```
grub> find /grub/stage1
find /grub/stage1
 (hd4,0)
grub> cat (hd4,0)/grub/menu.lst
cat (hd4,0)/grub/menu.lst
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
default                0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout                3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[Hit return to continue]
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
# title                Windows 95/98/NT/2000
# root                (hd0,0)
# makeactive
# chainloader        +1
#
# title                Linux
[Hit return to continue]
                        # root                (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/vgHD103UJ999M-lvRoot_crypt ro
[Hit return to continue]
                        
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
[Hit return to continue]
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

[Hit return to continue]
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

title                Ubuntu 8.10, kernel 2.6.27-7-generic
root                (hd0,0)
kernel                /vmlinuz-2.6.27-7-generic root=/dev/mapper/vgHD103UJ999M-lvRoot_crypt ro quiet splash 
initrd                /initrd.img-2.6.27-7-generic

title                Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root                (hd0,0)
[Hit return to continue]
                        kernel                /vmlinuz-2.6.27-7-generic root=/dev/mapper/vgHD103UJ999M-lvRoot_crypt ro  single
initrd                /initrd.img-2.6.27-7-generic

title                Ubuntu 8.10, memtest86+
root                (hd0,0)
kernel                /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
grub> 


```

Now this computer has:
2 sata drives on motherboard (as 3m and 4m) which are listed in Ubuntu as sdd and sde.

sde has 2 partitions: 350MB for /boot and the rest for LVM.

in the LVM partition of sde, there are the following logical volumes:
swap, var, tmp, root and data (custom mount).
(each LV ultimately has an Ext3 file system in it...)

all other drives, sda to sdd are physical volumes for LVM. (They just show up in gparted as filesystem = unknown.)

Given that info, menu.lst looks wrong at this line:
root                (hd0,0)
...but I'm not sure

Any ideas?

---

### Post by MountainX on 2009-02-26
I made a grub floppy disk.
I edited the menu.lst line to read: ```
root     (hd4,0)

```
booting from the floppy brought up the grub menu.
Howeverr, I could not start Ubuntu from that point.
I dropped into the grub shell and found stage1 on (hd1,0).
So I edited the first line in grub to read (hd1,0) and I booted.
Success!

So what is going on? Why does the Ubuntu installer think my drive is hd0, the live CD shows it as hd4 (sde) and it is actually hd1??????

Anyone want to clue me in (and tell me how to resolve this correctly)? Thanks

---

### Post by MountainX on 2009-02-26
maybe this is my problem?
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/119233](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/119233)

> Yes, this bug still exists on 8.04. I had to switch to using UUID
because the drive letters kept changing again at reboots.


and 

> 

This issue is still a problem in Intrepid as well. UUIDs can be useful in some cases but this is a major problem when using mdadm which seems to handle them based on the mount points rather than UUID.

In my case this is a problem almost every time I boot. (sometimes I get lucky)


I [read]("http://www.linux.com/?module=comments&func=display&cid=1198639") separately that using UUID's is not a good idea...

still don't know what to do or exactly what my problem is, except my drive mount letters are changing somehow...

---

### Post by MountainX on 2009-02-26
Good article here:
[http://www.linux.com/feature/146951](http://www.linux.com/feature/146951)
What UUIDs can do for [edit: TO] you

One [comment]("http://www.linux.com/?module=comments&func=display&cid=1198449") mentions mounting disks by label. That sounds interesting...

related links I'm studying:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1007492.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1007492.html)

I think I'll try mounting by labels tomorrow unless someone offers a better suggestion.

---

### Post by IntuitiveNipple on 2009-02-26
I've just seen your comment to [bug #119233]("https://bugs.launchpad.net/bugs/119233"). I suspect it is related to slight differences between the installer and installed kernel. The order of device detection can be different in some circumstances - especially with a mixture of on-board and slot-mounted controllers - because some drivers are built-in to the kernel and others are loaded dynamically later.

Can you attach two reports, one generated from the alternate CD root prompt and the other from the booted installed system?
```

REPORT=/tmp/disk-report.txt
uname -a >$REPORT
lsb_release -a >>$REPORT
sudo lspci -vvnn >>$REPORT
ls -l /dev/disk/by-path/ >>$REPORT
sudo blkid >>$REPORT

```
Collect the reports on a USB stick or some other permanent location and rename them to reflect where they were collected:
```

# from the installer:
cp /tmp/disk-report.txt /media/disk/disk-report-installer.txt
# from the installed:
cp /tmp/disk-report.txt /media/disk/disk-report-installed.txt
# when collected together, make into a compressed archive file:
cd /media/disk
tar -czf disk-reports.tar.gz disk-report-*.txt

```
And attach the resulting disk-reports.tar.gz

---

### Post by MountainX on 2009-02-26
> **IntuitiveNipple said:**
> Can you attach two reports, one generated from the alternate CD root prompt and the other from the booted installed system?

Yes, gladly. Thank you for the instructions. I will do as you described and attach the results to the bug report.

---

### Post by MountainX on 2009-02-26
> **IntuitiveNipple said:**
> 
sudo blkid >>$REPORT


In the installer environment:
```
/bin/sh: blkid: not found
apt-get install blkid
/bin/sh: apt-get: not found
```

what is my next step? Thank you.

UPDATE: i found that I have apt-install and apt-setup commands available. I also found that blkid is part of the package e2fsprogs. However, so far I have not been able to get it installed... appreciate any tips

---

### Post by MountainX on 2009-02-26
> **IntuitiveNipple said:**
> 
And attach the resulting disk-reports.tar.gz

The file is attached. Due to the fact that blkid and vol_id are not available from the command shell of the alternate installer, I used "ls -la /dev/disk/by-*" to generate as much info as I could.

I have looked over the reports, but it isn't clear to me what the problem is. I look forward to your feedback. Thanks.

---

### Post by MountainX on 2009-02-28
I now believe this problem may not be due to the Areca raid controller hardware. I haven't verified this yet, but I wanted to update future readers of this thread to the fact that my earlier assumptions appear to be at least partially incorrect.

See the following [thread]("http://ubuntuforums.org/showthread.php?t=1080832") for better info:
[http://ubuntuforums.org/showthread.php?t=1080832](http://ubuntuforums.org/showthread.php?t=1080832)

---

