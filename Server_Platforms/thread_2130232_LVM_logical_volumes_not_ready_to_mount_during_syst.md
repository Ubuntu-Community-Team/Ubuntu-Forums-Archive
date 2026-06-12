---
title: "LVM logical volumes not ready to mount during system start on Ubuntu Server 12.04.2"
date: 2013-03-28
forum: Server Platforms
---

### Post by Mito73 on 2013-03-28
[COLOR=#222222][FONT=Times]Hello everybody,

I was using openSuSE for several years now but for our new family-server I decided to switch to Ubuntu. Unfortunately to setup LVM is taking me half a day already[FONT=Verdana]:confused:[FONT=Times]. I have read through goggled article for ours now without success, now I hope that one of you will know how to fix the following issue.[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Times]
**System Configuration:**


[LIST=|INDENT=1]
[*]Intel Core i5-3450, 16G RAM
[*]128 GB SSD as System disk (/dev/sda)
[*]3Ware Raid-Controller, RAID1 with 2 TB capacity (/dev/sdb)
[*]Bootloader and root-partition located on /dev/sda
[*]For /var and /tmp two primary partitions on /dev/sdb are used
[*]The third (extended) partition of /dev/sdb is used as physical volume for the LVM
[*]The LVM only stores user-data, no system related information
[/LIST]

**Steps leading to issue:**


[LIST=|INDENT=1]
[*]Installed Ubuntu Server 12.04.2 64 Bit on /dev/sda without setting up LVM
[*]Partitioned /dev/sdb using [FONT=courier new]fdisk[/FONT] and set partition type to '[FONT=courier new]8e[/FONT]'
[*]Installed lvm: [FONT=courier new]apt-get install lvm2[/FONT]
[*]Set up lvm with four logical volumes
[*]Formatted logical volumes with ext4 using [FONT=courier new]mkfs[/FONT]
[*]Command lvdisplay shows all logical volumes as available
[*]Created mount points for logical volumes
[*]Manual mount of logical volumes works
[*]Edited [FONT=courier new]/etc/fstab[/FONT] to automatically mount logical volumes - example for one logical volume:
[FONT=courier new]UUID=[uuid-like-displayed-by-lvdisplay]  /mnt/images  ext4  default  0  1[/FONT]
[*]Rebooted system
[/LIST]

[B]Problem:
[/B]

[LIST=|INDENT=1]
[*]System displays the following message when booting up and waits for user action to skip mount commands:
[I][FONT=courier new]The disk drive for /mnt/images is not ready yet or present.
Continue to wait, or press S to skip mounting or M for manual recovery[/FONT][/I]
[*]When skipped the same message is shown for the next logical volume mount point
[*]After skipping the last mount point boot up proceeds until login screen
[*]When login in the logical volumes are not mounted
[/LIST]

[B]Things I tried:
[/B]

[LIST=|INDENT=1]
[*]**Created init-script [FONT=courier new]/etc/init.d/lvm[/FONT]** and used [FONT=courier new]update-rc.d[/FONT] lvm default to set it up for all runlevels:
[/LIST]
[INDENT][FONT=courier new]#!/bin/sh
case "$1" in
 start)
    /sbin/vgscan
    /sbin/vgchange -ay
    ;;
  stop)
    /sbin/vgchange -an
    ;;
  restart|force-reload)
    ;;
esac
exit 0[/FONT]
_Result:_ Even though the script is executed with the lowest number in the current runlevel directories, the logical volumes are not available during boot-up, only after login!

[/INDENT]

[LIST=|INDENT=1]
[*]**Added the file [FONT=courier new]/etc/udev/rule.d/85-lvm2.rules[/FONT]** with following content:
[/LIST]
[INDENT][FONT=courier new]SUBSYSTEM=="block", ACTION=="add|change", ENV{ID_FS_TYPE}=="lvm*|LVM*", \[/FONT]
[FONT=courier new] RUN+="watershed sh -c '/sbin/lvm vgscan; /sbin/lvm vgchange -a y'"[/FONT]
Then executed the command [FONT=courier new]update-initramfs -u -v[/FONT]
_Result:_ Logical volumes still not available for mounting during system boot-up


[/INDENT]

[LIST=|INDENT=1]
[*]**Tried to modify Upstart script [FONT=courier new]/etc/init/mountall.conf[/FONT]** - this was more or less blind research since I knwo a lot about System-V startup but nothing about Upstart. I added the following lines:
[/LIST]
[INDENT][FONT=courier new]pre-start script[/FONT]
[FONT=courier new]    /sbin/vgchange -ay[/FONT]
[FONT=courier new]end script[/FONT]
[/INDENT]
[INDENT]_Result:_ The system didn't boot up anyore at all (good look I had a second system installed as rescue system :-)
[/INDENT]

Well, I have a temporary workaround now by just doing the mount commands in my **[FONT=courier new]/etc/init.d/lvm [/FONT]**script. But I don't think thats a clean solution. It should either work by the udev rules or the upstart scripts - or am I wrong?

Would be great if somebody could give me some hints how I can solve this issue in the way it is intended to work!

Thanks in advance! Greetings from Stuttgart,
Michael
[/FONT][/COLOR]

---

### Post by darkod on 2013-03-28
I'm not sure whether you only needed to update the initramfs after you configured the LVM. Not sure if your scripts can interfere now.

Boot the system, activate the LVM manually without any scripts (disable the scripts if necessary), and try updating the initramfs:
```
sudo vgchange -ay
sudo update-initramfs -u
```

If the LVM is initialized correctly on boot I assume the fstab entries will work just fine.

---

### Post by steeldriver on 2013-03-28
I have a feeling the UUIDs from lvdisplay are not the 'right' ones - I don't know why - but if you look at blkid you will likely see different IDs corresponding to the device mapper, e.g. on my box I see

```
$ sudo lvdisplay | grep UUID
  LV UUID                vjtdoP-6uiA-YxuW-ejtc-fPTO-yRUh-iW4NmG
  LV UUID                Jtj3p8-XEST-nzU3-bUZg-mIiV-RCJo-XmR7j9
  LV UUID                uRhE8w-iCfb-8TK5-Ss0f-VHXp-uJc3-W8IweS
  LV UUID                QXJszf-oFh0-HGXi-COta-00Y6-5Aw2-anA6CK
$
$ sudo blkid -c /dev/null | grep mapper
/dev/mapper/vg1-lv0: UUID="5a7a6816-a43a-414e-ac6f-d31f9a30a76f" TYPE="swap"
/dev/mapper/vg1-lv1: UUID="bb5c5da2-4c75-4212-ad1d-1f4b691c7d76" TYPE="ext4"
/dev/mapper/vg1-lv2: UUID="181da924-a8a3-4934-a417-9b264a98fec7" TYPE="ext4"
/dev/mapper/vg0-lv0: UUID="897da7b7-edb1-4a6c-94e0-0a6175c89273" TYPE="xfs"
```

Try using the blkid UUIDs - or use the /dev/mapper/vgname-lvname labels, which is what I have done, e.g.

```
$ cat /etc/fstab | grep mapper
/dev/mapper/vg1-lv1     /tmp            ext4    defaults        0       2
/dev/mapper/vg1-lv2     /var            ext4    defaults        0       2
/dev/mapper/vg1-lv0     none            swap    sw              0       0
/dev/mapper/vg0-lv0     /storage/mythtv xfs defaults,noatime,allocsize=512m,logbufs=8 0 2
```

---

### Post by Mito73 on 2013-03-29
Thanks for the quick response and the hints. I think the different UUID's are one part of the issue - when mounting a volume group with the name [FONT=courier new]LV Name[/FONT] given by [FONT=courier new]lvdisplay[/FONT], the name of the mounted device is different:

```

[FONT=courier new]root@ikarus:~# /bin/mount /dev/vgikarus/lvimages /mnt/images [/FONT]
[FONT=courier new]root@ikarus:~# df -h | grep /mnt/images[/FONT]
[FONT=courier new]/dev/mapper/vgikarus-lvimages  1.5T  197M  1.5T   1% /mnt/images[/FONT]

```

Should have made me suspicious before! But unfortunately **it still does not work** after changing [FONT=courier new]/etc/fstab[/FONT] accordingly :icon_frown:

**Steps performed:**


[LIST]
[*]Deleted (moved away) my own, mentioned above, init-script [FONT=courier new]/etc/init.d/lvm[/FONT]
[*]Executed [FONT=courier new]update-rc.d lvm remove[/FONT]
[*]Deleted (moved away) my own, mentioned above, udev rules-scrip /etc/udev/rules.d85-lvm2.rules
[*]Commented out lines for logical volumes in /etc/fstab
[*]Rebooted the system
[*]Performed commands:
```

[FONT=courier new]root@ikarus:/etc/udev/rules.d# vgchange -ay[/FONT]
[FONT=courier new]  4 logical volume(s) in volume group "vgikarus" now active[/FONT]
[FONT=courier new]root@ikarus:/etc/udev/rules.d# update-initramfs -u[/FONT]
[FONT=courier new]update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic[/FONT]

```
[*]Created the following lines in /etc/fstab:
```

[FONT=courier new]root@ikarus:~# cat /etc/fstab | grep vgikarus[/FONT]
[FONT=courier new]/dev/mapper/vgikarus-lvvmware     /mnt/vmware  ext4 default    0    1[/FONT]
[FONT=courier new]/dev/mapper/vgikarus-lvhome       /home        ext4 default    0    1[/FONT]
[FONT=courier new]/dev/mapper/vgikarus-lvvmusic     /mnt/music   ext4 default    0    1[/FONT]
[FONT=courier new]/dev/mapper/vgikarus-lvimages     /mnt/images  ext4 default    0    1[/FONT]

```
[*]Rebooted the system
[/LIST]

**Problem stays the same like described in initial post **

[B]Things I tried now:
[/B]

[LIST]
[*]I commented out all lines referring to logical volumes in [FONT=courier new]/etc/fstab [/FONT]and restarted the machine again. No it came up cleanly, but after login in I realized that the logical volumes are in state [FONT=courier new]NOT available[/FONT] according to [FONT=courier new]lvdisplay[/FONT]. 
-> So I think the problem is not the mounting itself but that LVM (device-mapper) is not loaded at boot time.
[*]As soon I do as simple [FONT=courier new]vgchange -ay[/FONT] command as root the volume groups are available and can be mounted. Another try with [FONT=courier new]update-initramfs -u[/FONT] didn't bring any changes after reboot.
[/LIST]

Well, something must go wrong during boot-up - maybe some configuration issue either with [FONT=courier new]device-mapper[/FONT] or [FONT=courier new]udev[/FONT] - both topics where i have not much clue of. Trouble is that I didn't do much configuration changes on the system yet - apart from the changes I mentioned above it is quite out of the box. Well, I have Grub installed, which can also start a second Ubuntu installation on /dev/sda3 (for emergencies). But I can't omagine how this would cause the problem.

So, now I am pretty lost - spend lots of time in Google already. Will invest today for further investigation and post this in the hope of some more hints. Then I have to decide if I want to live with my workaround as mentioned above or better switch back to SuSE which I just know better. :confused:

---

### Post by steeldriver on 2013-03-29
Hmm just re-reading your original post and the LVM pv is a logical volume on your hardware RAID, is that correct? if so I wonder whether it's something to do with the timing of the RAID startup i.e. the pv itself not being 'ready' in some sense when the system tries to vgchange -ay? is there anything to that effect in dmesg / syslog / kern.log?

---

### Post by darkod on 2013-03-29
I don't have much experience adding LVM once the system was installed, but I think after you installed the lvm2 package that should be it.

Another thing you could try, but I don't think it should make a difference, is using /dev instead of /dev/mapper for the LVs. If you don't know, there is another way to address a LV and that's /dev/VGname/LVname instead of the /dev/mapper/VGname-LVname.

They do the same job. But if the LVs are not even active on boot as you say, I don't think using /dev/VGname/LVname in fstab will help much.

---

### Post by Mito73 on 2013-03-29
Thanks for the quick reply again. I think *steeldriver's* idea sound reasonable somehow. On th other hand the log files don't give any hint about a problem. I tried to search them for keywords like [FONT=courier new]udev[/FONT], [FONT=courier new]lvm[/FONT] or [FONT=courier new]device-mapper[/FONT] using the [FONT=courier new]grep[/FONT] command. Then I even read trough them: Nothing suspicious. Or maybe yes - in all logfiles I could find only two entries regarding the device-manager:

```

[FONT=courier new]root@ikarus:/var/log# grep -e 'device-mapper' *.log[/FONT]
[FONT=courier new]kern.log:Mar 29 15:02:01 ikarus kernel: [    0.470265] device-mapper: uevent: version 1.0.3[/FONT]
[FONT=courier new]kern.log:Mar 29 15:02:01 ikarus kernel: [    0.470297] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com[/FONT]

```

Apart from this, I can only find entries for the RAID-Controller which look more or less the same in all logfiles:

```

**[FONT=courier new]/var/log/syslog[/FONT]**
[FONT=courier new]
[/FONT]
[FONT=courier new]...[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    0.470265] device-mapper: uevent: version 1.0.3[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    0.470297] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com[/FONT]
[FONT=courier new]...[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    0.782506] 3ware 9000 Storage Controller device driver for Linux v2.26.02.014.[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    0.782937] 3w-9xxx: scsi6: ERROR: (0x06:0x000D): PCI Abort: clearing.[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    0.812967] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)[/FONT]
[FONT=courier new]...[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.117465] scsi6 : 3ware 9000 Storage Controller[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.117551] 3w-9xxx: scsi6: Found a 3ware 9000 Storage Controller at 0xf7e20000, IRQ: 16[/FONT]
[FONT=courier new]...[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.452724] 3w-9xxx: scsi6: Firmware FE9X 4.08.00.006, BIOS BE9X 4.08.00.001, Ports: 4.[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.453288] scsi 6:0:0:0: Direct-Access     AMCC     9650SE-4LP DISK  4.08 PQ: 0 ANSI: 5[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.460906] sd 6:0:0:0: Attached scsi generic sg1 type 0[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.460994] sd 6:0:0:0: [sdb] 3906228224 512-byte logical blocks: (1.99 TB/1.81 TiB)[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.461425] sd 6:0:0:0: [sdb] Write Protect is off[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.461428] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.461704] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.497355]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.498634] sd 6:0:0:0: [sdb] Attached SCSI disk[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.538228] Adding 7811068k swap on /dev/sda1.  Priority:-1 extents:1 across:7811068k SS[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.559072] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.559076] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready[/FONT]
[FONT=courier new]:[/FONT]
[FONT=courier new]...[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.933464] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.965087] 3w-9xxx: scsi6: ERROR: (0x03:0x0101): Invalid command opcode:opcode=0x85.[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.965406] 3w-9xxx: scsi6: ERROR: (0x03:0x0101): Invalid command opcode:opcode=0x85.[/FONT]
[FONT=courier new]Mar 29 15:02:01 ikarus kernel: [    1.965666] 3w-9xxx: scsi6: ERROR: (0x03:0x0101): Invalid command opcode:opcode=0x85.[/FONT]

```

[B]So this leaves me with two possible conclusions:
[/B]

[LIST=1]
[*]Either the system does not even try to initialize the LVM logical volumes
[*]or - since device-mapper is initialized before the 3Ware-Controller - *steeldriver* is right and the load order is wrong
[/LIST]

To verify this, I will try to delete my LVM configuration and create a new one using a physical volume on /dev/sda which is the system hard disk. But no matter if 1) or 2) is the cause - how would i fix it?

---

### Post by darkod on 2013-03-29
If you suspect number 2, you might google for something like "how to delay loading lvm modules in ubuntu server" or simply "how to delay loading lvm in ubuntu server".

---

### Post by steeldriver on 2013-03-29
the only thing I can offer is that one of my LVs is on top of a mdadm sofware RAID PV and that has always mounted fine - so I don't think there's anything intrinsically wrong with what you are trying to do

---

### Post by Mito73 on 2013-03-29
I just set up a new LVM configuration with its a physical volume located on the system drive [FONT=courier new]/dev/sda [/FONT]and not on the hardware RAID1 [FONT=courier new]/dev/sdb[/FONT]. The created logical volume was inserted into [FONT=courier new]/etc/fstab [/FONT]to mount it at boot-time.

After reboot the system came up without any problems, after login the logical volume was correctly mounted.

So it is like suspected: The hardware RAID1 is initialized too late, after device-mapper is already set up - due to the LVM logical volumes are never activated and unable to be mounted during startup.

I did some research in Google: the few hints I found having the same problem used a linux distribution with system-V init. At least there is no init.rd on my system, so it does not help. 


[LIST]
[*]Is it possible that the boot-loader **[FONT=courier new]GRUB[/FONT]** controls the initialization order?
[*]Does [FONT=courier new]**initramfs**[/FONT] handle this in Ubuntu? - I found an [article about it regarding start order of a software raid]("http://ubuntuforums.org/showthread.php?t=1365365") - but for hardware raid there does not seem to exist a hook in [FONT=courier new]/usr/share/initramfs-tools/hooks[/FONT]
[/LIST]

Any hint how to change the initialization order would be appreciated! I don't know any further.

---

### Post by Mito73 on 2013-04-30
A month ago I have raised [Bug #1163406]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1163406") (Device-mapper initialized before hardware-raid during system boot) for the Ubuntu package [Upstart]("http://upstart.ubuntu.com/index.html"). Since there was no reaction at all on this Bug and I was running out of time with my installation, I switched back to OpenSuSE finally. With version 12.3 the installation including my LVM setup worked on the first try.

Ubuntu really seems to boot much faster - this may be due to the more modern [init process using Upstart]("http://wiki.ubuntuusers.de/Upstart"). But on the other hand this init process is much more complicated and less mature the the classical and commonly used Unix System V init system. At the same time I had the feeling that the Upstart developers didn't take too much care for bugs which are assigned to their upstart-package.
Even though Ubuntu offers long term support for their Server distribution, I would only use it again for a very simple and straight forward system due to this. To get the OpenSuSE box running took around one day - all in all I spend nearly five complete days to get this Ubuntu issue solved. So even if I have to reinstall OpenSuSE after 2 years since my current version will run out of support, I still will have much less effort maintaining the system. And the Upstart advantage of faster boot times does not count too much on a server system!

---

