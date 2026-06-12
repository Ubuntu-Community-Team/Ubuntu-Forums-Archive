---
title: "Boot error on Primergy L200"
date: 2006-06-04
forum: Server Platforms
---

### Post by henrikwidth on 2006-06-04
Hi

When I install dapper-server on my Fujitsu-Siemens Primergy L200 PN2
I get this boot-error:

[I]    Booting ´Ubuntu, kernel 2.6.15-23-386´
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/i2o/hda1 ro quiet splash
{snip}
Uncompressing Linux... Ok, booting the kernel.
[4294696.712000] iop0: device already claimed
[4294696.713000] iop0: DMA /IO allocation for i2o controller failed
[/I]

This happens on: 
dapper-server-cd: regular install and LAMP install
dapper-alternative: Install server

If I install dapper desktop, everything works fine...

there are three scsi-disks on the i2o-controller running in raid5

output from lspci -vv

0000:01:0a.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1010 66MHz  Ultra3 SCSI Adapter (rev 01)

anyone else experiensing the same? what can I do to get a bare server-install?

Best regards

Henrik

---

### Post by henrikwidth on 2006-06-04
bug filed ages ago..

[https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/22220](https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/22220)

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=henrikwidth]bug filed ages ago..
[https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/22220](https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/22220)[/QUOTE]

unfortunately I must agree to some comments on this specified thread: this bug is not fixed.

Yesterday I tried to install Ubuntu 5.10 Server and also 6.06 (final) on a machine which contains an Adaptec 2400A Raid controller. Both fails.
Booting from 5.10 install CD a kernel crash does happen when loadiong dpt_i2o. Same crash happens when installing without Raid controller, install all avaliable updates and then add the controller.
Booting from 6.06 install CD another mysterious error happens: boot process does stop with a warn message about a soft bug in CPU0. :confused:

The specified thread doesn't help to solve the problem.

To be honest: this dpt_i2o problem seems to be more generic and NOT Ubuntu related. I tried to boot from different Linux CD, even Knoppix does not but (no error message appears, it's just frozen), neither other distro's.

Thomas

---

### Post by henrikwidth on 2006-06-05
Hi Thomas

what puzzles me is that the dapper-desktop works flawlessly.. are there different ways of loading the dpt_i2o? I really need to get this working, I´m not to sure about having a dapper-desktop install on a production server..

Henrik

---

### Post by linuxone on 2006-06-05
Hi Henrik,

[QUOTE=henrikwidth]what puzzles me is that the dapper-desktop works flawlessly.. are there different ways of loading the dpt_i2o? I really need to get this working, I´m not to sure about having a dapper-desktop install on a production server..[/QUOTE]

I tried many things to get this Raid controller working. I installed 5.10 Server without the controller card build in; the Raid-5 array should be used for a Samba file server into a small local network at a home workplace. My guess was to test the updated kernel environment because this may solve the problem .... no matter what happened using the original boot CD.
Because I didn't get 5.10 working I tried the newer software release by doing apt-get upgrade and apt-get dist-upgrade. Thanks to a fast DSL connection this could be done within a short time. Althought the lastest kernel version from Dapper Drake won't work in combination with the Adaptec controller.

Finally the local users deceided to work without the raid array. Instead I installed a specific backup solution, so all files could be restored in a short IF this worst case will ever happen. And I re-installed a fresh breezy system to have the same system on all my servers.

Thomas

---

### Post by warriorx99 on 2006-06-10
I've been running into the same issue where it boots past grub, then I get:

Booting 'Ubuntu, kernel 2.6.15-23-server'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/i2o/hda1 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x16b75f]
initrd /boot/initrd.img-2.6.15-23-server
[LInux-initrd @ 0x1f950000, 0x69f602 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel
[42949377.l970000] PCI: Failed to allocate mem resource #9: 100000@fe000000 for 0000:01:1d.0
[42949377.970000] PCI: Failed to allocate mem resource #6: 8000@fe000000 for 0000:03:01.0
[42949391.280000] iop0: device already claimed
[42949391.280000] iop0: DMA/IO allocation for I2O controller failed
ALERT! /dev/i2o/hda1 does not exist.  Dropping to a shell!


I'm not sure at all what to do with this and I'm really eager to get Ubuntu server working on this machine.  This is my first ubuntu install and it's not going so well :(

-Shane

---

### Post by henrikwidth on 2006-06-11
Hi All

I´m not too sure what to do either.. I have tried to reply to the bug-list but I didn´t get any response. The bug is assigned to Colin Watson, it says Fix committed and fix released, but only confirmed for the kernel team. does this mean that we´ll be good to go when the server iso is "re-pressed"? some time soon?

---

### Post by zitch on 2006-07-26
I'm trying to install Ubuntu Server 6.06 on a system at work, and I'm hitting this problem.  It either tells me "device already claimed" or "could not Init".  Seems to switch randomly.  After this, it gives me a "ALERT! /dev/i2o/hda1 does not exist. Dropping to a shell!" error and drops me into a shell telling me to fix it.  Simply exiting or pressing Control-D will continue the boot process normally and successfully.

Pretty much, I'm hitting the same issues as warriorx99 on an Adaptec 3210S.

EDIT: Had the wrong model #!

---

### Post by zitch on 2006-07-27
I believed I have found a fix!

It's not actually a problem with the dpt_i2o module as I had assumed.  It actually tries to detect and correctly backs out when it finds out the RAID Card is "already claimed" by the newer i2o drivers.  The problem in my case is in the /etc/fstab file!

When the system boots, the fstab tells the kernel to mount /dev/i2o/hda1 as /boot, but this doesn't actually exist!  So the system will boot to a command line asking you to fix the filesystem, but pressing Control-D will allow the filesystem to boot normally with the exception of the /boot partition (The rest of the file system is under a LVM setup, so it's automatically detected correctly).

The fix?  Open up the /etc/fstab file as root and modify the line containing the following when the system boots after bypassing the filesystem check:

```

/dev/i2o/hda1       /boot           ext3    defaults                        0 2

```

to

```

/dev/sda1       /boot           ext3    defaults                        0 2

```

If you have other filesystems trying to mount from /dev/i20/xxxx in fstab, then you may have to fix those entries too. (Note, if you *can't* boot because the root filesystem is referred in that manner, then you might have to use a live cd, mount the root filesystem, and edit the /etc/fstab file that way).

Then reboot.  The boot directory should now correctly mount and the boot process will not be interrupted when attempting to mount the filesystem.

This seems to be a bug in the installer/partitioner, since that is what referred to the filesystem as /dev/i2o/xxx when setting it all up.  The developers may have to be made aware of this.

---

