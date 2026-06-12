---
title: "MDADM Booting Issues"
date: 2012-05-03
forum: Server Platforms
---

### Post by AvidElite on 2012-05-03
My system has 4 sata ports on the motherboard, and I added a PCIe card with 2 more sata ports.

My system boots off /dev/sda1, no problem.

I had a linear raid (just two disks glued together) on /dev/sdb1 and /dev/sdc1.  I since added two more drives on /dev/sdd1 and /dev/sde1.  Now, the /dev/sde drive is on that add-in card that gives me more sata ports.

When I boot, it complains that there's a drive missing, always /dev/sde1.  However, if I get past the shell and exit into Ubuntu itself, /dev/sde1 is there, and I can just start the raid from the console.

Is there a way I can make the sata card initialize it's drives BEFORE mdadm tries to assemble?  Or, is there a way to stop mdadm checking at boot and I can just have the rc.local script assamble and mount it?

I tried bootdegraded=true but with one drive "missing" from a linear array, it's not degraded, it's broken, and still halts the boot process.

Please help!

Many thanks in advance.

---

### Post by rubylaser on 2012-05-03
If you run
```
dpkg-reconfigure mdadm
```
You can tell mdadm to not start any arrays.  Finally, you'd just need to run the mdadm assemble command in rc.local as you suggested.

The only other thing that could be goofing you up is if you explicitly listed your disks in your /etc/mdadm/mdadm.conf file, and they're no longer in the same positions.  What's the output of.
```
cat /etc/mdadm/mdadm.conf
```
and
```
cat /proc/mdstat
```

---

### Post by AvidElite on 2012-05-03
The command "dpkg-reconfigure mdadm" asks me three questions:
(1) Should mdadm run monthly redundancy checks on the MD arrays? [I answer no, since it's a linear there is no redundancy]
(2) Do you want to start the MD monitoring daemon? [I answer yes]
(3) Do you want to boot your system if your RAID becomes degraded? [I answer yes]

However the system still drops to the Initramfs/BusyBox interface when the linear fails to assemble.

----------
/etc/mdadm/mdadm.conf


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE partitions containers
#DEVICE /dev/null

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]avidelite@yahoo.ca[/email]

# definitions of existing MD arrays
ARRAY /dev/md/charlotte:stratos metadata=1.2 name=charlotte:stratos UUID=07def056:b1d95953:d24d14e3:650a1519

----------
/proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sde1[3](S) sdc1[1](S) sdb1[0](S) sdd1[2](S)
      9767553024 blocks super 1.2

unused devices: <none>

----------

I don't know what I managed to break in all my mucking about, but I can't even get the raid to assemble now even after it boots.

I run "mdadm --assemble --scan" and I get no error, or anything, and /proc/mdstat stays looking like above.

I run "mdadm --assemble /dev/md127" and it gives me this: "mdadm: /dev/md127 not identified in config file."

Which, unless there's another config file I don't know about, it IS there (see my above text).

I'm really super frustrated.  I've been googling for hours and trying everything I can find and nothing is working.

I really appreciate any help here.

---

### Post by rubylaser on 2012-05-04
> **AvidElite said:**
> 
# definitions of existing MD arrays
ARRAY /dev/md/charlotte:stratos metadata=1.2 name=charlotte:stratos UUID=07def056:b1d95953:d24d14e3:650a1519

I run "mdadm --assemble --scan" and I get no error, or anything, and /proc/mdstat stays looking like above.

I run "mdadm --assemble /dev/md127" and it gives me this: "mdadm: /dev/md127 not identified in config file."

Which, unless there's another config file I don't know about, it IS there (see my above text).

I'm really super frustrated.  I've been googling for hours and trying everything I can find and nothing is working.

I really appreciate any help here.

The reason mdadm is throwing that error is that your config file doesn't mention a /dev/md127 device, it mentions /dev/md/charlotte:stratos.  Here's what you need to do to get it working again.

```
sudo -i
mdadm --stop /dev/md127
```

Then, you need to get your mdadm.conf file in the proper format.  I'd change it as follows.
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE partitions containers

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR avidelite@yahoo.ca

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=07def056:b1d95953:d24d14e3:650a1519
```

All of the other stuff is uneeded and will more often than not mess up assembly rather than aid it.    This will present the array at /dev/md0.

Next, you'll need to edit your /etc/fstab to change your mdadm array mount line to mount /dev/md0, something like this (depends on your mountpoint and filesystem on the array, but this gives you an idea).

```
/dev/md0        /storage            ext4        defaults        0        0
```

Next, we can correctly assemble your array.
```
mdadm --assemble --force /dev/md0 /dev/sd[bcde]1
```

Finally, you should update your initramfs to have this work after a reboot.
```
update-initramfs -u
```

That should get your array working again.  If you're still having problems with the mdadm mountpoint after a boot, you  could just remove the mountpoint from /etc/fstab, and mount the array in rc.local so that it happens later in the boot sequence. Hope that helps :)

---

### Post by AvidElite on 2012-05-04
I had a minor issue in that all the drives were marked as spare by the superblock, so I was being told "mounted array with 0 drives and 4 spares, not enough to start the array."

```
mdadm --create /dev/md0 --assume-clean --level=linear --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

However, I made all the changes you said, then recreated the array with the line above (which only rewrote the superblocks and left my data intact), made sure my mdadm.conf had the UUID of the NEW superblocks, then ran your update-initramfs.

It works.  It boots, assembles the array, and mounts the filesystem all before the login prompt.  It works like it's supposed to work.

You, Rubylaser, are my personal hero.  If you ever find yourself in the Ottawa, Ontario, Canada area message me and I'll buy you *all* of the beers.

Thank you so much for ending hours of torment and panic.

---

### Post by rubylaser on 2012-05-04
No problem.  I'm glad you got it all sorted out.  I'd love all of the beers I could drink, but the 10+ hours from Michigan to Ottawa with gas prices the way they are may be counterproductive :)

---

### Post by mons00n on 2012-05-08
> **rubylaser said:**
> 
Finally, you should update your initramfs to have this work after a reboot.
```
update-initramfs -u
```


this just fixed all of my problems, thanks!  could you tell me a bit more about what it does?

---

### Post by rubylaser on 2012-05-08
> **mons00n said:**
> this just fixed all of my problems, thanks!  could you tell me a bit more about what it does?

Great, glad that worked for you.  update-initramfs takes care of any post GRUB boot issues. It's a good idea whenever you make a change that might affect booting, run this before rebooting.

---

### Post by darkod on 2012-05-08
> **rubylaser said:**
> Great, glad that worked for you.  update-initramfs takes care of any post GRUB boot issues. It's a good idea whenever you make a change that might affect booting, run this before rebooting.

If I may jump in too. :)

Is this something that could help after you clone a partition? Is there a particular set of rules what to do after cloning a partition with regards if the new partition has new UUID and your system has the old UUIDs inside it.
Also, what about if you only copy the files to a new partition, not literary clone the partition? In that case the new partition will definitely have a different UUID.

I know it's far from the topic but it looks sort of related to me. :)

---

### Post by rubylaser on 2012-05-08
In cases of cloning, you should just need to make sure grub is installed on the new partition and files like /etc/fstab are updated to reflect the new UUID's (I assuming you're just talking about booting a cloned hard drive).

---

### Post by AvidElite on 2012-05-13
update-initramfs compiles a series of script files (among other things) into the binary that runs during boot.

I had to set up two identical machines and while RubyLaser's suggestions worked on one, they did not work on the other.  I found out why and wanted to share.

I had to cripple 1 of initramfs' scripts, and once that change was compiled into the binary, it got mdadm to behave.

FILE: **/usr/share/initramfs-tools/scripts/local-premount/mdadm**
I commented out these two lines
```
#degraded_arrays || exit 0
#mountroot_fail || panic "Dropping to a shell."
```

---

### Post by rubylaser on 2012-05-13
This is a good find, but you should never need to do this.  This is a hack to workaround the problem rather than fix it.

---

