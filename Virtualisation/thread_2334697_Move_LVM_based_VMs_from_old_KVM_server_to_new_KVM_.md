---
title: "Move LVM based VMs from old KVM server to new KVM server"
date: 2016-08-21
forum: Virtualisation
---

### Post by chrisjx on 2016-08-21
I want to move my LVM based VMs from my old KVM server to my new KVM server.  What is "the way"?

I have:
KVM running on Ubuntu 12.04 - old system
  with 5 VMs on LVM partition at /dev/sd3/vgroup/
  all references to VMs in /dev/sd3/vgroup/ are actually symlinks to ../dm-1-5

KVM running on Ubuntu 16.04 - new system
  with 1 vm, deb8, as a test
  it also has the same structure /dev/sd4/vgroup/deb8
  deb8 is a link to ../dm-0

a backup script that weekly stops each vm on old system and dd to a gzipped copy


If I unzip a copy of my backed-up vm on the new KVM box, and dd it to /dev/vgroup/testdata it copies the vm file and does not create the magic link to /dev/vgroup/testdata (which, I assume, should link to ../dm-1).  The copied testdata VM in /dev/vgroup does not appear in my list of storage volumes in virt-manager.

I've read a lot of articles about using snapshots, dd, gzip, and dd back to the LVM directory.  I also have the vm.xml config files backed up, but none of the articles I found seem to describe how this is to be used to bring up on a new server.

Can someone please explain all this magic (or definitive references) and maybe just a straight-ahead approach to moving LVM based VMs from one KVM server to another KVM server.

Thanks in advance,
Chris.


Old KVM
[FONT=courier new]# lvs
  LV         VG     Attr   LSize  Origin Snap%  Move Log Copy%  Convert
testCinga  vgroup -wi-ao 58.59g
  UbuDesktop vgroup -wi-a- 39.06g
  devbox     vgroup -wi-ao 39.06g
  testdata   vgroup -wi-ao 39.06g
  testlogs   vgroup -wi-ao 19.53g
  testlogs2  vgroup -wi-ao 54.69g
  webserver1 vgroup -wi-ao 40.00g
  win2008-1  vgroup -wi-a- 29.30g

lsblk /dev/sda3
NAME                         MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda3                           8:3    0 422.9G  0 part
&#9492;&#9472;md2                          9:2    0 422.8G  0 raid1
  &#9500;&#9472;vgroup-webserver1 (dm-0) 252:0    0    40G  0 lvm
  &#9500;&#9472;vgroup-UbuDesktop (dm-1) 252:1    0  39.1G  0 lvm
  &#9500;&#9472;vgroup-testCinga (dm-2)  252:2    0  58.6G  0 lvm
  &#9500;&#9472;vgroup-testdata (dm-3)   252:3    0  39.1G  0 lvm
  &#9500;&#9472;vgroup-testlogs (dm-4)   252:4    0  19.5G  0 lvm
  &#9500;&#9472;vgroup-testlogs2 (dm-5)  252:5    0  54.7G  0 lvm
  &#9500;&#9472;vgroup-devbox (dm-6)     252:6    0  39.1G  0 lvm
  &#9492;&#9472;vgroup-win2008--1 (dm-7) 252:7    0  29.3G  0 lvm

# ls -la /dev/vgroup
total 0
drwxr-xr-x  2 root root  200 Aug 20 13:08 .
drwxr-xr-x 17 root root 4700 Aug 20 13:08 ..
lrwxrwxrwx  1 root root    7 Aug 20 13:08 devbox -> ../dm-6
lrwxrwxrwx  1 root root    7 Aug 19 22:15 testCinga -> ../dm-2
lrwxrwxrwx  1 root root    7 Aug 19 21:51 testdata -> ../dm-3
lrwxrwxrwx  1 root root    7 Aug 19 08:37 testlogs -> ../dm-4
lrwxrwxrwx  1 root root    7 Aug 19 20:39 testlogs2 -> ../dm-5
lrwxrwxrwx  1 root root    7 Aug 14 20:21 UbuDesktop -> ../dm-1
lrwxrwxrwx  1 root root    7 Aug 19 01:45 webserver1 -> ../dm-0
lrwxrwxrwx  1 root root    7 Aug 19 22:41 win2008-1 -> ../dm-7[/FONT]



New KVM 
[FONT=courier new]# lvs
  LV      VG     Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  deb8    vgroup -wi-ao---- 80.00g



# lsblk /dev/sda4
NAME             MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda4               8:4    0  2.2T  0 part
&#9492;&#9472;vgroup-deb8    252:0    0   80G  0 lvm


# ls -la /dev/vgroup
total 16446376
drwxr-xr-x  2 root root          80 Aug 21 12:57 .
drwxr-xr-x 19 root root        4260 Aug 21 12:57 ..
lrwxrwxrwx  1 root root           7 Aug 18 02:24 deb8   -> ../dm-0
-rw-r--r--  1 root root 16841089024 Aug 21 12:20 testdata[/FONT]

---

### Post by TheFu on 2016-08-22
The short answer is that storage is storage.  As long as the OS sees the storage where it is expected "inside" the running OS, then how it gets there doesn't matter.
[http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html) might be helpful.

I move VMs around occassionally. See that process as a way to test our backup and restore methods, so I use that. No need to do something different.  Storage has to be created outside the backup/restore process for our situation.  Backup/restore only deals with the files inside the VM.  We don't do LV pass-through from the hostOS to the VM. Sounds like you do.

That doesn't mean there isn't some fancy, LVM-based way to do this. It just means that beyond **vgimport**, I don't think there is anything special about it.

Welcome to the forums.  Whatever works is what I'd use.

---

### Post by chrisjx on 2016-08-23
Seems the missing part from all the documentation I read was to create a new logical volume (LV) on the target machine, THEN, dd the backed up VM INTO the new LV.

I thought I was backing up an LV and I was looking for an lvcreate with an existing backed up LV file.

Maybe someday there will be a process to move a VM/LV from one KVM server to another using virt-manager.

I'm OK for now...

Thanks,
Chris.

---

### Post by MAFoElffen on 2016-08-23
To me, what you are saying is missing is just another extension to what he suggested. If you have a storage framework , you need to adjust and adapt to your own framework-- whether the existing framework that lies on is an LVM, ZFS... SMB, NFS, SAN, etc. 

You recreate or adapt going from one to another, whether that is the same or different. After that is done, then do the actual migration. Right?

Virt-Manager is set up for basic management on a static system. It does not have advanced features offering provisioning in LVM or ZFS... nor any features offering migrations. (It would be great it it did, but alas...) To do those when using Virt-Manager, you still have to do those via manually, or via a user scripts.

---

### Post by TheFu on 2016-08-23
If you have shared storage, live-migrations should be possible. [http://www.linux-kvm.org/page/Migration](http://www.linux-kvm.org/page/Migration) and [https://libvirt.org/migration.html](https://libvirt.org/migration.html)

Appears that RHEL has supported live-migrations through virt-manager [https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Virtualization/sect-Virtualization-KVM_live_migration-Migrating_with_virt_manager.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Virtualization/sect-Virtualization-KVM_live_migration-Migrating_with_virt_manager.html)

IME, this is where enterprises differ from home users - shared, networked, storage.  However, even that line is blurring for savvy home users who are willing to deal with the added hassles of shared storage.

---

