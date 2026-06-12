---
title: "After Ubntu 9.10 Server installation, grub says: &quot;no such disk&quot;"
date: 2010-01-20
forum: Server Platforms
---

### Post by Trevski13 on 2010-01-20
So I'm setting up an old computer as a server, the installation of Ubuntu 9.10 Server (32bit) went successfully, but now on boot it says: 
"error: no such disk 
Press any key to continue"

I've successfully set up a number of multi boot systems but this is the first dedicated only to Linux.

computer is an Old Dell (originally came with Win98 )
currently has a 450 MHz Pentium III, 384MB of RAM and a 160GB IDE HDD

ls results in:
"(hd0) (hd0,1) (fd0) (fd1)
error: no such disk"
and I also did ls /boot and I get things prefixed with system.map, vmlinuz, config, abi, vmmcoreinfo, initrd.img, and memtest86.bin plus the grub/ folder
is there supposed to be a linux kernel in there? or am I just completely wrong

thanks in advance

note: I also booted to a live CD and cannot mount the drive (it's not clear to me *why*... but I can't).

---

### Post by meierfra. on 2010-01-21
> is there supposed to be a linux kernel in there? o

You do have a kernel: vmlinuz 


> error: no such disk
Sound like a hardware or bios problem. Or maybe your cables aren't  plugged in right.

But lets check your out your system before we jump to conclusions.

Do you get a "sh: grub>" prompt or a "rescue: grub>" prompt?


 In the first case you can try to boot into Ubuntu via:

```
search -f --set /vmlinuz
probe  --set=U -u $root
linux /vmlinuz root=UUID=$U ro
initrd /initrd.img
boot

```


In the second case  (or if the above did not work) try

```

set root=(hd[COLOR="Red"]0,1[/COLOR])
set prefix=(hd[COLOR="Red"]0,1[/COLOR])/boot/grub
insmod ext2
insmod linux
set root=(hd[COLOR="Red"]0,1[/COLOR] )
linux /vmlinuz root=/dev/[COLOR="Red"]sda1[/COLOR] ro
initrd /initrd.img
boot
```
The values  in red depend on the location of your Ubuntu partition. But from  the "ls" output it seems that  ubuntu is the first partition on the first  hard drive, so this should be correct.


If you are able to boot into Ubuntu, run
```
sudo grub-install /dev/sda
sudo update-grub
```

Reboot and see whether  things improved.

If this did not solve your problem, (and I doubt that it will), report any error messages your got. Also if you have some kind of Linux Live CD,  boot from  it and follow these instruction to run the Boot Info Script and post the RESULTS.txt: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by meierfra. on 2010-01-21
> note: I also booted to a live CD and cannot mount the drive (it's not clear to me why... but I can't).

I just saw your edit.  That changes things a little bit. Try the things from my previous post, but you might also run a file system check:


```
sudo e2fsck -yfv /dev/sda1
```

(of course that assumes that Ubuntu is on /dev/sda1)


On second thoughts:  What kind of LiveCD do you have?  If your Ubuntu partition is ext4, your LiveCD might not be able to read it

---

### Post by Trevski13 on 2010-01-21
> [QUOTE]is there supposed to be a linux kernel in there? o 
You do have a kernel: vmlinuz [/QUOTE]
*facepalm* forgive my momentary stupidity. lol

> Do you get a "sh: grub>" prompt or a "rescue: grub>" prompt?
well, if I remember correctly the VERY first time it happened I got a "rescue:grub>" prompt but currently I have to go to the command-line myself and then I get "sh:grub>"

> In the first case you can try to boot into Ubuntu via:

```
search -f --set /vmlinuz
probe  --set=U -u $root
linux /vmlinuz root=UUID=$U ro
initrd /initrd.img
boot
```

attempted and got: "error: cannot get C/H/S values [PAKtC]"


> ```
set root=(hd0,1)
set prefix=(hd0,1)/boot/grub
insmod ext2
insmod linux
set root=(hd0,1 )
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```
BINGO that worked like a charm... at least once I remove the space from the second "set root=(hd0,1 )" :D

I ran ```
sudo grub-install /dev/sda
sudo update-grub
```
and upon reboot I get 
"error: no such disk
      Failed to boot default entries.
[PAKtC]"
and upon another reboot I'm back exactly where I was... *sigh*

> On second thoughts: What kind of LiveCD do you have? If your Ubuntu partition is ext4, your LiveCD might not be able to read it
I think that's right on target, for a Live CD I'm just running the Ubuntu/Xubuntu 9.10 (32bit) CD... and I have a strong feeling it can't read ext4...

I'm currently loading the Live CD and will post the Boot Info Script once that's done.

(on a slightly side note... now, of course I want to legitimately solve the problem... but I just have to ask... would replacing the default boot entry in GRUB to:```
set root=(hd0,1)
set prefix=(hd0,1)/boot/grub
insmod ext2
insmod linux
set root=(hd0,1 )
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
``` make it work...? kind of an unorthodox method but I don't see why it wouldn't...)

---

### Post by Trevski13 on 2010-01-21
And here it is:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5196600

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   310,343,669   310,343,607  83 Linux
/dev/sda2         310,343,670   312,576,704     2,233,035   5 Extended
/dev/sda5         310,343,733   312,576,704     2,232,972  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="Ubuntu-Server" UUID="8010a4f9-bf58-4c92-b5bb-448f92d31cc7" TYPE="ext4" 
/dev/sda5: UUID="07ab29bb-abf2-48bd-bc2c-fab8ea661233" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8010a4f9-bf58-4c92-b5bb-448f92d31cc7
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8010a4f9-bf58-4c92-b5bb-448f92d31cc7
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=8010a4f9-bf58-4c92-b5bb-448f92d31cc7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8010a4f9-bf58-4c92-b5bb-448f92d31cc7
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=8010a4f9-bf58-4c92-b5bb-448f92d31cc7 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8010a4f9-bf58-4c92-b5bb-448f92d31cc7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=07ab29bb-abf2-48bd-bc2c-fab8ea661233 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic-pae
    .0GB: boot/vmlinuz-2.6.31-14-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz

```

---

### Post by meierfra. on 2010-01-21
> . but I just have to ask... would replacing the default boot entry in GRUB to: ...  make it work...? 

Yes, it would. But it would get overwritten during the next kernel update.

 There are a couple of lines in "grub.cfg" which are not really necessary, and could be causing the problem. You could just remove them both, but I would like to know   which one is  blame.

So try this at the ">sh grub" prompt:


 ```
 search --no-floppy --fs-uuid --set  8010a4f9-bf58-4c92-b5bb-448f92d31cc7
```

also

   ```
 search  --fs-uuid --set 8010a4f9-bf58-4c92-b5bb-448f92d31cc7  
```


and 

```

      load_env
      recordfail=1
      save_env recordfail
```

Let me know of any error messages you got.


If the "save_env" command produces an error messsage, do this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

If the search command produces an error message, do this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Just for my understanding:
> error: cannot get C/H/S values [PAKtC]"
Did you got this after the "search" or after the "probe" command?

---

### Post by Trevski13 on 2010-01-21
```
search --no-floppy --fs-uuid --set  8010a4f9-bf58-4c92-b5bb-448f92d31cc7
```results in "error: no such disk"

```
search  --fs-uuid --set 8010a4f9-bf58-4c92-b5bb-448f92d31cc7
```results in "error: cannot get C/H/S values"


```
      load_env
      recordfail=1
      save_env recordfail
```results in nothing happening at all

> Did you got this after the "search" or after the "probe" command?I got it after the "search"

Ah! Now *here* we go, I edited the GRUB file and Success!! It boots perfectly. Thank you very much for you help!

So... it seems this "search" command is quite buggy... so why is it included by default?

---

### Post by meierfra. on 2010-01-21
> It boots perfectly. 
Great.


> it seems this "search" command is quite buggy... so why is it included by default? 
The "search" commands  determines the Ubuntu partition by uuid rather than "root=(hd0,1)". If you create an extra partition in front  of your Ubuntu partition, or add a new hard drive to you computer, you still will be able to boot.  So it is a really nice feature.  

But with Grub 2 being so new, and all the different bios, it's no surprise that it's still a little buggy.

---

### Post by buckyinsfo on 2010-01-22
What specifically did you edit?

I'm having the exact same issue on a new install on older hardware.

Are you saying the device cannot be found using the uuid?

---

### Post by meierfra. on 2010-01-22
> What specifically did you edit?

I think  he/she followed these instruction:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by buckyinsfo on 2010-01-24
Thank you for your help.

During my initial install I allowed the partitioner to do a 'Guided with LVM".  I couldn't ever get the grub menu to come up.  I reinstalled and just used /dev/sda as root and the instructions in your link solved my problem.  Thanks again!

---

