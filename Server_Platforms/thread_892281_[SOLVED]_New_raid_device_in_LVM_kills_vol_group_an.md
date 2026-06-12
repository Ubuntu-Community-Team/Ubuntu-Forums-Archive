---
title: "[SOLVED] New raid device in LVM kills vol group and root partition - will not boot"
date: 2008-08-17
forum: Server Platforms
---

### Post by thefekete on 2008-08-17
[COLOR="Red"]**Solution:**[/COLOR]
initramfs needs to know about the raid devices during boot, it gets the info from /etc/mdadm/mdadm.conf INSIDE the initrd image. In order to update it you need to add the new array to your normal mdadm.conf and run
```

sudo update-initramfs -u

```

This needs to be done right after you add the array and BEFORE you reboot. After my experience, I'd recommend doing the following when adding raid devices to an existing LVM volume group:
[LIST=1]
[*]Build your array
[*]Add array to /etc/mdadm/mdadm.conf
[*]Run sudo update-initramfs -u
[*]Reboot to verify raid device started at boot (mdadm --detail /dev/mdX)
[*]Add raid device to volume group
[*]Reboot to verify
[*]If all goes well, expand your logical volumes and filesystems
[/LIST]
NOTE: Be extra careful when expanding filesystems like xfs, this cannot be undone!

If you get stuck at the initramfs shell because a raid device did not start, don't worry... You can start your array(s) from the busybox shell with:
```

mdadm --assemble /dev/mdX /dev/sdXX /dev/sdXX ... 

```
just like from bash. Once you get your devices started, do a logical volume scan with
```

lvm lvscan

```
to verify your volume group started and your logical volumes are available. If all is well, just type
```

exit

```
and the boot process will resume with your root partition available to the kernel.

Hope this helps...
[COLOR="Red"]**/Solution**[/COLOR]



**Quick Description:**
I ran out of room on my home file server, so I added four 320gb sata drives, created a raid 5 device via mdadm (/dev/md1) and added it to my only Logical Volume Group. When I rebooted, I was dropped to a busybox shell with the error that my root partition didn't exist.

cat /proc/mdstat shows that that the new device (/dev/md1) is not started at boot, just the original /dev/md0. I'm assuming since md1 is part of the vol grp that contains my root partition, and LVM is failing to create that group, it is prohibiting the kernel to see my root partition.

Basically, I need help getting mdadm to start the new raid device at boot in order let LVM build the vol group and boot my system. Or, if my assumptions are wrong, please point me in the right direction

**Background info:**
Installed gutsy server with raid5+LVM from start. Raid consisted of six 500gb drives in level 5 array (/dev/md0). LVM setup was one physical volume (/dev/md0) placed in volume group (6r5-2500gb). This group was split into /(root), /home, /tmp and /var logical volumes. The boot and swap partitions are not part of the RAID or LVM setup.

**Details:**
Once I ran out of room, I partitioned the new 320gb drives with linux raid autodetect and created a new array (/dev/md1) with mdadm --create.

I then added /dev/md1 to the same volume group as the original raid 5 device (/dev/md0), extended the /home logical volume to fill free space and extended the xfs file system to fill logical volume.

I checked df -h and saw that the space had been properly allocated. I felt like there was some step involved to make the changes permanent, but google didn't bring up much evidence. It seemed that LVM would remember my settings and mdadm.conf wasn't really necessary since mdadm scanned the partitions at boot. So I rebooted to confirm, and was greeted with this:

```
Starting up ...
Loading, please wait...
	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/{my root vol} does not exist. Dropping to a shell!
(initramfs) _
```

I rebooted and entered recovery mode and realized that the system seemed to pause for about a minute after loading md0 and then dropped to the shell. Here's the last few lines:

```
raid level 5 set md0 active with 6 out of 6 devices, algorithm 2
RAID5 conf printout:
 --- rd:6 wd:6
 disk 0, o:1, dev:sdb3
 disk 1, o:1, dev:sda2
 disk 2, o:1, dev:sdc2
 disk 3, o:1, dev:sdd2
 disk 4, o:1, dev:sdf2
 disk 5, o:1, dev:sde2
Done.
	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/{my root vol} does not exist. Dropping to a shell!
```

Thanks in advance for any help!

---

### Post by windependence on 2008-08-17
The new drive needs to have the LVM signature written on it.

This is done by doing:

```
vgextent <volume_name> /dev/hdX
```

Is that the way you added it?

-Tim

---

### Post by thefekete on 2008-08-17
Thanks for the quick response...

Yes, here's the sequence of commands I used:

```

# Vol Group contained physical volume md0 only
mdadm --create --verbose /dev/md1 --level=5 --raid-devices=4 \
	/dev/sdg1 /dev/sdh1 /dev/sdj1 /dev/sdi1
pvcreate /dev/md1
vgextend 6r5-2500gb /dev/md1
# Vol Group now had md0 and md1 as physical volumes
lvextend -L+890G /dev/6r5-2500gb/home
# lvm lvs now showed addition to /home
xfs_growfs /home
# df -h now showed addition to xfs filesystem

```

After reboot, only md0 is started, but md1 is not. I think LVM is failing to start the volume group because md1 is not present at that time.

If I start md1 via busy box and scan with LVM, The vol goup is built and I can mount the individual logical volumes just fine...

---

### Post by thefekete on 2008-08-17
UPDATE:
I looked into shrinking the the vol group and removing the offending md1, however I shot myself in the foot by extending the xfs filesystem, since it seems that cannot be shrunk. Thus I'm stuck with a 3.15TB volume group.

Since getting the storage to back all this up is prohibitively expensive, I need to fix this in place.

Anyways, here's a little more info on the LVM setup:
```
Volume Groups
	VG		#PV	#LV	VSize	
	6r5-2500gb	2	5	3.15TB
Physical Volumes
	PV		VG		Fmt	PSize
	/dev/md0	6r5-2500gb	lvm2	  2.27TB  <-- Starts at boot
	/dev/md1	6r5-2500gb	lvm2	894.27GB  <-- Doesn't start automatically
Logical Volumes
	LV	VG		LSize	Fmt
	home	6r5-2500gb	3.12TB	xfs
	root	6r5-2500gb	5.00GB	ext3
	tmp	6r5-2500gb	4.88GB	ext3
	usr	6r5-2500gb	5.00GB	ext3
	var	6r5-2500gb	4.88GB	ext3
```

---

### Post by thefekete on 2008-08-18
UPDATE:
I just figured out that if you type 'exit' at the ash prompt, the OS tries to continue booting...

So here's my work around:
(this is all done from the ash prompt)

First I create the second raid device:
```

mdadm --assemble /dev/md1 {hard drives in second array}

```
Then I get LVM to see the volume group and all logical volumes:
```

lvm pvscan
lvm vgscan
lvm lvscan

```

Finaly, I resume the boot sequence with both arrays and the vol group running:
```

exit

```

This is far from a solution, but it gets my server working. I'm not sure if I should file a bug report for the LVM/RAID implementations, or if I'm just missing some config file somewhere.

So I still have the same problem:
My second raid device is not started at boot, and therefore LVM fails to start the volume group with my root partition.

Any help is greatly appreciated.


-dan

---

### Post by bigredradio on 2008-08-19
I skimmed, but it appears from what you listed that you need to update the initrd. I doubt that Ubuntu creates an initrd that can handle LVM on RAID. If it can (which is what you had originally?) then run the command to recreate the initrd. Then all devices will be available to gain access to the root filesystem.

---

### Post by thefekete on 2008-08-19
@bigredradio
Thanks for your reply. Apparently ubuntu can and does set up initrd for LVM2 over raid... This was my original installation setup. However, my problems started when I added a second raid device to LVM. This new device is not started at boot.

Ran the following:
```

# update-initramfs -u

```
Unfortunately, the problem persists. Is there another command I need to execute? Or do I need to enable or move the new initramfs?

---

### Post by thefekete on 2008-08-19
bigredradio, thanks for the reminder on the linux boot sequence... 

Finally figured it out:

I added the second array to /etc/mdadm/mdadm.conf, ran update-initramfs -u and rebooted...

Worked like a charm, no more building arrays in busybox!

Thanks again for the pointers.


-dan

---

