---
title: "[SOLVED] bad disk - pvmove"
date: 2008-03-19
forum: Server Platforms
---

### Post by jleiss on 2008-03-19
So I have a disk going bad in my LVM. I went out and got a replcement disk to move the data to until the drive can be replaced by warranty. I setup the partition, and created a PV on the drive, and made it part of the same LVM.

I then booted up with a livecd and did the following:

vgscan --mknodes
vgchange -ay
modprobe dm-mirror
pvmove -v -i 10 /dev/sdb1

but my move hangs at about 78.3% and sits there. I beleive its hitting a spot it cannot read, how can i get it to ignore this and move on?

---

### Post by bigredradio on 2008-03-19
You are using the -i flag which should deal with this. It could be that the i/o errors are causing the modules to fail. You might want to try the LVM irc channel on freenode or post to an LVM specific forum.

Hate to say it, but you might want to try to get a good backup of the data and consider rebuilding the VG. If this is the rootvg, then you can download the trial of Storix and use that. Not open source, but will work so that you do bare-metal recovery to save the system. If you do not have tape, you can backup to a USB drive. Just make sure to read the users guide.

---

### Post by jleiss on 2008-03-19
im using a livecd from 6.06, would it be worthwhile to download 8 and try it from there.. or what about copying the data from one drive to another using dd, and if so how would I do it?

---

### Post by jleiss on 2008-03-19
on a suggestion from the lvm channel i tried a new livecd.. in this case im using 5.1 from knoppix and it seems to be working, i'm beyond 78.3% at least.

---

### Post by jleiss on 2008-03-19
ok, back to needing help. got the partition data moved, but now i need to move lilo or reconfig lilo to boot off the new drive.. any tips or URL's for help on this.

---

### Post by bigredradio on 2008-03-20
Might want to use grub instead. Just because you can make changes to the config file on the fly. Lilo requires the bootloader to be reloaded to the MBR after each change to lilo.conf.

Bootloaders (lilo or grub) cannot access data inside LVM. So an initrd is necessary to run vgscan and activate the VGs so that the root filesystem can be accessed. You must have a separate /boot fileystem that contains the kernel and initrd. Hopefully you can salvage the kernel initrd and menu.lst file from the previous disk.

As far as grub, there is a lot of documentation around. Basically you cat or dd the grub executable to the MBR of the disk. I think you can do this from the knoppix cd using grub-install. Then create a /boot/grub/menu.lst. This is the config file.

---

### Post by jleiss on 2008-03-20
I dont think that will work in this case, because the drives are all LVM, and I don't think Grub can boot from LVM.

---

### Post by bigredradio on 2008-03-21
No bootloader for linux can get access to data inside a logical volume. This is why you need a /boot filesystem on a regular partition that contains the kernel and an initrd. Also, the initrd needs to be able to start LVM. If you are unsure about any of this, you might want to save some hassle and put / in a partition and /usr /var /home /opt etc in LVM.

---

### Post by jleiss on 2008-03-23
Lilo has had no issues accessing the root partition inside the lvm.. The only thing outside is the mbr.. all other partions are inside the lvm.. Since no one seemed to have any good suggestions I just ended up making a copy of my root partition, reinstalling and copying my config files back over.. I just finished getting the system back up.

---

### Post by bigredradio on 2008-03-23
This seems impossible to me. I would be curious to see that. You do not have a /boot filesystem and your rootfs is inside a logical volume?

---

### Post by jleiss on 2008-03-24
here's my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/media-root /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/media-home /home           reiserfs defaults        0       2
/dev/mapper/media-storage /media/storage  reiserfs defaults        0       2
/dev/mapper/media-vmware /media/vmware   reiserfs defaults        0       2
/dev/mapper/media-swap none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

and part of my lilo.conf relating to this.

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/mapper/media-root

---

### Post by jleiss on 2008-03-24
and a pvscan of my drives.


jleiss@brandywine:/etc$ sudo pvscan
  PV /dev/sda1   VG media   lvm2 [465.76 GB / 0    free]
  PV /dev/sdb1   VG media   lvm2 [465.76 GB / 0    free]
  PV /dev/sdc1   VG media   lvm2 [465.76 GB / 0    free]
  Total: 3 [1.36 TB] / in use: 3 [1.36 TB] / in no VG: 0 [0   ]

---

### Post by bigredradio on 2008-03-25
Can I see your entire lilo.conf file? I want to see if there is an initrd line and what the appends are.

---

### Post by jleiss on 2008-03-26
here you are...

# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/mapper/media-root

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#       prompt
#       delay=100
#       timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
        label=Linux
        read-only
#       restricted
#       alias=1

        initrd=/initrd.img

image=/vmlinuz.old
        label=LinuxOLD
        read-only
        optional
#       restricted
#       alias=2

        initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#       label=HURD
#       restricted
#       alias=3

---

