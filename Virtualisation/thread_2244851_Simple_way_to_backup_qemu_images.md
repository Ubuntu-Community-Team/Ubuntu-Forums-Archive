---
title: "Simple way to backup qemu images?"
date: 2014-09-19
forum: Virtualisation
---

### Post by sgofferj on 2014-09-19
Hi,

I have started to consolidate all the services of my home infrastructure, which were spread over several physical machines but not very logically, into VMs which run on my new core server. The core server is a Xeon with 32GB RAM, 6x3TB running ZFS/RaidZ2 and a 128GB SSD. The VM disk images are located on the SSD for performance but, of course, I would like to have also safety, so I would like to create a copy of every VM's disk image at least once a day and store a history of those on the array. I have been googling quite a bit and found a ton of whitepapers but no simple tutorial on how to do that. Frankly, I'm not interested in learning to fully understand the inner workings and coding concepts of e.g. qemu-livebackup. That's not my topic. I simply want to do backups of my VMs.
Can anybody point me to a simple tutorial on how to get a clean copy of a VM's disk image without shutting the VM down for that?

-Stefan

---

### Post by TheFu on 2014-09-21
Use zfs snapshots.  I'm afraid it isn't "simple", but if you figured out zfs, you should be able to figure this out too. I don't know if this will ensure a consistent state for running DBs.  Then use zsend to replicate the snapshots to a different machine.

I don't use anything VM and LVM related for backups. Each VM is treated like a normal machine and standard backup methods are used. I would dump any running DBs, then use [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) to backup system data, settings and lists of installed packages. The easy solution for this method is also, very inefficient in time and storage requirements. With a little intelligence, it is relatively easy to have 2 months of daily incremental backups (most recent backup is a mirror) easily available.  Restores begin by installing a fresh basic install - then the backups are applied to reconfigure the system to be identical to before any issue - total time 20-40 minutes.  For an email gateway server there 120 days of backups are less than 50MB - yes, MB, not GB.  BTW the installed OS/apps/data on that box are just over 4G.

---

### Post by sgofferj on 2014-09-22
But my VMs are not running ZFS because of the memory requirement. They are running from regular images from the SSD and the SSD is formatted with EXT4. The VM images are also fairly small with 8G each, so keeping a little history of those on my array wouldn't really be that bad and it would also make restoring fairly simple... Just copy the desired backed up image to the SSD and restart the VM.

I anyways keep the majority of the important data on the array and let the VMs access it via 9p. I mainly would like to backup the VM images so I don't have to set them up all new in case the SSD dies.

---

### Post by TheFu on 2014-09-22
If the hostOS runs ZFS, you can use snapshots while all the VMs are running, then zsend.

Otherwise, I don't think there is an answer that allows the machines to stay running. Sorry.  Well - my method does, but it isn't "simple."

---

