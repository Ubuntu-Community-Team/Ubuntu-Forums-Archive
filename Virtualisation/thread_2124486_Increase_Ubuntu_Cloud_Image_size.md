---
title: "Increase Ubuntu Cloud Image size"
date: 2013-03-11
forum: Virtualisation
---

### Post by tpradeep on 2013-03-11
I am using Ubuntu 10.04 cloud image to boot virtual instance in OpenStack (using devstack). However, if I choose a flavor with 20G hard disk and 20G ephemerel disk, I still get only 1.35G(/dev/vda1) virtual instance. If i use resize2fs from inside the instance, the size increases to 2G only. How do I increase the size to 20G ? I tried searching on google but couldn't get any proper step. Can someone please guide me to accomplish this task.

[FONT=monospace]root@test:~# df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/vda1             1.4G  632M  685M  48% /
none                  244M  156K  244M   1% /dev
none                  247M     0  247M   0% /dev/shm
none                  247M   48K  247M   1% /var/run
none                  247M     0  247M   0% /var/lock
none                  247M     0  247M   0% /lib/init/rw
/dev/vdb               20G  173M   19G   1% /mnt

pvdisplay and lvdisplay do not show any output.
[/FONT]

---

### Post by tracer888 on 2013-05-12
I'm having this issue as well, the base master controller has enough space...

```
[FONT=courier new]root@dexterstackcontrol:~/.ssh# vgdisplay cinder-volumes[/FONT]
[FONT=courier new]  --- Volume group ---[/FONT]
[FONT=courier new]  VG Name               cinder-volumes[/FONT]
[FONT=courier new]  System ID[/FONT]
[FONT=courier new]  Format                lvm2[/FONT]
[FONT=courier new]  Metadata Areas        2[/FONT]
[FONT=courier new]  Metadata Sequence No  12[/FONT]
[FONT=courier new]  VG Access             read/write[/FONT]
[FONT=courier new]  VG Status             resizable[/FONT]
[FONT=courier new]  MAX LV                0[/FONT]
[FONT=courier new]  Cur LV                2[/FONT]
[FONT=courier new]  Open LV               0[/FONT]
[FONT=courier new]  Max PV                0[/FONT]
[FONT=courier new]  Cur PV                2[/FONT]
[FONT=courier new]  Act PV                2[/FONT]
[FONT=courier new]  VG Size               101.99 GiB[/FONT]
[FONT=courier new]  PE Size               4.00 MiB[/FONT]
[FONT=courier new]  Total PE              26110[/FONT]
[FONT=courier new]  Alloc PE / Size       2304 / 9.00 GiB[/FONT]
[FONT=courier new]  Free  PE / Size       23806 / 92.99 GiB[/FONT]
[FONT=courier new]  VG UUID               pezIDN-FmoC-r12d-0O7j-HD16-a3k4-KGjj1L[/FONT]

```
This is a fairly new install but I followed these instructions to construct the testbed: [http://openstack-folsom-install-guide.readthedocs.org/en/latest/](http://openstack-folsom-install-guide.readthedocs.org/en/latest/)

The interesting thing is the disk itself is 40 gigs, it appears, according to fdisk...
```
ubuntu@t4:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/vda1             1.4G  630M  686M  48% /
none                  2.0G  152K  2.0G   1% /dev
none                  2.0G     0  2.0G   0% /dev/shm
none                  2.0G   48K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
```

```
ubuntu@t4:~$ sudo fdisk /dev/vda
sudo: unable to resolve host t4


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').


Command (m for help): p


Disk /dev/vda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *           2         261     2088450   83  Linux


Command (m for help): q

```

I tried a 12.04 image and that does resize properly
```
glance image-create --location http://uec-images.ubuntu.com/releases/12.04/release/ubuntu-12.04-server-cloudimg-amd64-disk1.img --is-public true --disk-format qcow2 --container-format bare --name "Ubuntu 12.04 amd64"

```
[COLOR=#333333][FONT=Helvetica]vs
[/FONT][/COLOR]```
[COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]glance image-create --location http://uec-images.ubuntu.com/releases/10.04/release-20130124/ubuntu-10.04-server-cloudimg-amd64-disk1.img  --is-public true --disk-format qcow2 --container-format bare --name "Ubuntu 10.04 amd64"

```
[COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by Ryan G on 2013-06-01
+1 hitting the exact same issue.

Any ideas how to work around it? Wondering if its something Openstack needs to fix or Ubuntu?

---

### Post by mo4 on 2013-08-01
I am having the same problems here. I tried the daily and release versions of lucid, but neither works.

My goal is to set up appscale, which only runs under ubuntu 10.04, so its not possible for me to switch to 12.04 (which also runs fine).

Has anyone found a solution yet?

---

