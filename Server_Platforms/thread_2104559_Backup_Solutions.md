---
title: "Backup Solutions"
date: 2013-01-13
forum: Server Platforms
---

### Post by DanHorniblow on 2013-01-13
Hi,

I have a VPS running Ubuntu 10.04 which I use for hosting web sites and email mailboxes.

I currently have a script that backups up certain directories to a tar and the ftp's them to another server. I would like to be able to take an image / snapshot of my VPS, so I could restore it if the worst happened.

Does anyone have any ideas?

Thanks Dan

---

### Post by rootyourbrain on 2013-01-13
> **DanHorniblow said:**
> Hi,

I have a VPS running Ubuntu 10.04 which I use for hosting web sites and email mailboxes.

I currently have a script that backups up certain directories to a tar and the ftp's them to another server. I would like to be able to take an image / snapshot of my VPS, so I could restore it if the worst happened.

Does anyone have any ideas?

Thanks Dan
bump

---

### Post by TippingPoint on 2013-01-13
[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)

---

### Post by markbl on 2013-01-13
I've used rsnapshot for many many years and although I occassionally look around to see if any else better has come along I still think it the best backup solution for linux systems.

---

### Post by LHammonds on 2013-01-14
I configure my servers to use LVM.  It is all LVM except the /boot and I have extra unused space in the LVM to do LV snapshots.  I use LV snapshots with fsarchiver to create 100% online and full backups of the partitions so they can easily be restored to a new server in case it goes dark for whatever reason.

I also use rsync to backup data files, 7-zip to compress them and store them offsite in addition to the less frequent partition backups.

Check my sig for more details.

LHammonds

---

### Post by SeijiSensei on 2013-01-14
> **DanHorniblow said:**
> I have a VPS running Ubuntu 10.04 which I use for hosting web sites and email mailboxes.

I pay my VM provider Linode a few bucks a month to create snapshot backups of my machine each night.  I also use rsync to keep an updated copy of some of the server's directories on a machine in my home as well.

---

### Post by collisionystm on 2013-01-16
> **markbl said:**
> I've used rsnapshot for many many years and although I occassionally look around to see if any else better has come along I still think it the best backup solution for linux systems.


This. ++++++

---

