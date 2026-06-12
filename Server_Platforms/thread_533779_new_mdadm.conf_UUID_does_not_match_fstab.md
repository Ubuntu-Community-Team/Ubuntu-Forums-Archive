---
title: "new mdadm.conf UUID does not match fstab"
date: 2007-08-24
forum: Server Platforms
---

### Post by trtech on 2007-08-24
I maintain a remote server that has 1 small SATA drive mounted as /, and 2 large SATA drives, mirrored w/ RAID 1 mounted as /data.

I just did a 'dist-upgrade' using apt on a remote server and got the following message:

```
Setting up linux-image-2.6.20-16-server (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-server
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
```

The file /usr/share/doc/mdadm/README.upgrading-2.5.3 tells me to:

```
...inspect /etc/mdadm/mdadm.conf or /etc/mdadm.conf (whichever one
is present, the first gets priority if both are present) and ensure that all arrays
are properly identified. Here are a number of recommended checks:

  - Verify that all arrays referenced by /etc/fstab, /etc/crypttab, your LVM
    metadata, and whatever other subsystem uses MD arrays (RAIDs) on your
    machine have a corresponding line in the configuration file.

    Make sure to verify that your bootloader refers to the proper device name,
    in case your root filesystem is on an MD array.

    In particular, verify that the device node name is exactly the same;
    /dev/md6 is *not* identical to /dev/md/6. Partitionable arrays are
    a slight exception: if /dev/md_d0p3 is referenced, you need an entry for
    /dev/md_d0 in the configuration file.

  - Compare your file with the output of /usr/share/mdadm/mkconf . In
    particular, make sure that the UUID matches for each array, whenever
    a UUID is specified. Also compare the values of super-minor, name, and
    devices. Only one match identifier (UUID, super-minor, name, devices) is
    needed for each array, but if multiple identifiers are specified, all must
    match. See mdadm.conf(5).

    Identifying arrays by UUID is the preferred method.
```

The problem is that the UUID in **/etc/mdadm/mdadm.conf** does not match the UUID in **/etc/fstab**.

/etc/mdadm/mdadm.conf (after replacing with the output of sudo /usr/share/mdadm/mkconf):

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 **UUID=ed15494e:b3d101ac:f7fb6803:d8c00764**
```

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2042298a-d58d-406e-bc8f-e0a0170ea1f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md0
**UUID=a6b4a39f-038e-4873-ab00-976f4c4f6f6d** /data           ext3    defaults        0       2
# /dev/sda5
UUID=f78f13f1-f0d7-46f1-a5a5-bce5a10b417f none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Am I going to have a problem when I reboot?

Thanks,
-Chris

---

### Post by ruibernardo on 2007-08-24
if you do have any problem, run

```
blkid
```

and update fstab and/or mdadm.conf.

---

### Post by trtech on 2007-08-24
Thanks for the quick reply epimeteo.

Could you please explain further?

I am accessing the server via SSH so if I reboot and I have problems, then the system won't be able to open the pod bay doors.

Thanks,
Chris

---

### Post by ruibernardo on 2007-08-24
Sorry Chris, can't help you. 

I though it was a simple UUID difference between two configuration files. Maybe someone who uses RAID can help you.

---

### Post by trtech on 2007-09-15
For those who may be searching for this, I realized that the instructions state that the UUID(s) in the configuration file must match those in the output of /usr/share/mdadm/mkconf and the device names must match those in /etc/fstab.

I mistakenly thought that it was telling me to make sure that the UUIDs in mdadm.conf matched the UUIDs in /etc/fstab.

---

