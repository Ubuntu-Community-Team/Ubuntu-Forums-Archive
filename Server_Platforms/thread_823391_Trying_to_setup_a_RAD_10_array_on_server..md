---
title: "Trying to setup a RAD 10 array on server."
date: 2008-06-09
forum: Server Platforms
---

### Post by Joe Driller on 2008-06-09
Need help to setup a RAID 10 on ubuntu 8.04 i386 server installation. My machine is a dual PIII 500 Mhz 1Gb RAm PC133 with a SuperMicro P6DBE Mobo with two SCSI cards, an ADAPTEC AHA2940 with 2 20 Gb SCSI disks attached and a ADVANSYS ABP3940U2W with another pair of 20 Gb.SCSI2 disks, the system is installed on a SCSI disk of 4,3 Gb hanging on ADAPTEC card. Also have a pair of 6,3 Gb IDE disks, a SCSI CD-ROM and A SCSI CD-RW on the ADAPTEC.

My first problem is the ADVANSYS, system don't recognize it, help are needed to load the driver.

The second problem are to setup a RAID 10 with this four SCSI disks. If I starts with a 7.10 live Cd I can see the two cards and four disks but is no way to set up a raid 10, only raid 0,1,5. Maybe MDADM can help??

The final plan is to set up a file server with system on a RAID 0 on the IDE drives and all data on a RAID 10 with SCSI disks.


All help will be welcomed.

Best Regards.

---

### Post by TheGameAh on 2008-06-09
I do believe that at the moment, only the Fedora installer gives the option of setting up RAID10 at install time.

For all other distros, you're right, you have to use MDADM.  Been spending a lot of time lately myself with this.

I always install the root partition and /var, etc., on a RAID1 (just cause it's easier to setup at install time).  Then post-install, I use MDADM to setup the RAID10.

---

### Post by Joe Driller on 2008-06-09
O.k. I have system running in the 4,3 Gb SCSI disk and have acces to the other 4 SCSI disks. Can you tell me how to setup the RAID 10 with mdadm, I've tried it, but don't understand how does it works.
In fact I actually have 4 MD devices (I see them in Gparted),MD0 that seems doesn't work, MD1 is a RAID1 with sd(ab)1, MD2 is a RAID1 with sd(ef)1 and MD3 that is RAID 10 with MD1 and MD2. I can mount MD3 and appears in my home directory as mount1 folder; I can write in it.
After rebooting I only see MD0 of 512Mb but still doesn't work and I have no idea what disks or partitions is using.


Really I need help to understand RAIDs

---

