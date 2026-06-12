---
title: "HEEELP!!! How to fix broken qcow2 image? HAVE NO BACKUP!"
date: 2012-10-16
forum: Server Platforms
---

### Post by toshko3 on 2012-10-16
I've done a snapshot during machine running and it gave no error. After that the image is corrupted and no partitions at all at the Ubuntu server 12.04 guest.
I am DEAD if I don't fix it!!!
Please help me! I didn't find any tool for fixing qcow2 images...
](*,)

---

### Post by wirelessmonkey on 2012-10-16
I'm sorry to tell you, but I don't think the image can be recovered, once corrupted. Perhaps if it's a local file system error, the image may not be bad once the FS is repaired...

---

### Post by toshko3 on 2012-10-23
Thanks.
I did a convert to the same type (qcow2) and it removed all of the snapshots, but the image wasn't repaired. Well I started the guest, created the partition the same way it was before with cfdisk, forced a repair of the file system, claiming it is ext4 (yes it was) and it repaired it with many errors, but I hope with no missing or corrupted files.
People, I must say something from my experience of using snapshots of qcow2 image.
DON'T USE THEM! They break images and corrupt everything. The snapshotting feature is waaaaay too at child phase to use in production environment. Again, DON'T USE THEM! And for the mission impossible of recovering qcow2 image... it speaks for itself. USE AT YOUR OWN RISK!
I will share some info about the system I've created and scripts to do snapshots, if anyone interested. I've spent many weeks to test and create a script for auto snapshotting, but the snapshotting process and result is not reliable, obviously!
AGAIN - DON'T use snapshotting and qcow2 images in combination for production environments!!!

---

