---
title: "Data VHD is showing up/doesn't show up after each reboot"
date: 2022-07-12
forum: Server Platforms
---

### Post by joris-th on 2022-07-12
Hi,

Because I am 'new' to Linux I might do something stupid & also this might be in the wrong thread

Setup
Ubuntu 20 04 Server is running on a Hyper-V Windows Server 2022.
The System (sdb) & Data (sda) VHDs (XFS File System) are on a NAS.
In Hyper V they are both connected via IDE
Except glances nothing is running on the Ubuntu


What I did
sudo nano /etc/fstab
/dev/sda                   /data  xfs     defaults         0       0


The data VHD shows up, but after a reboot it won't show up.
If I reboot again it shows up, reboot again, doesn't show up...

---

### Post by TheFu on 2022-07-12
Use ext4 as the file system inside Ubuntu and SCSI or SATA or virtio with virtio preferred for all storage and network controllers.
xfs is used on other distros much more than with Ubuntu. There are lots of reasons to choose either, but I cannot tell if the XFS is the NAS file system or the file system you picked inside the VM for the Ubuntu install.

Also, it is extremely odd to use an entire virtual disk (or a real disk) for a file system. Nobody does that and it breaks all sorts of things.  Always place file systems onto either partitions or logical volumes (if LVM is used).  Even Windows uses partitions for NTFS. Sadly, you seem to have confused "drive" and "partition" somewhere - probably because MSFT has lied and told you that C: was a "drive" and that "D:" was a drive - - they are not.  They are partitions with a file system inside a drive.  MSFT has been lying about this since the first HDD was connected in the 1980s.  It is a hold over from floppy discs when we used A: and B: as drive letters that mapped directly to, you know, a drive.

---

