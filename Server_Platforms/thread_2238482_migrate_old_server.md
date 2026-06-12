---
title: "migrate old server"
date: 2014-08-08
forum: Server Platforms
---

### Post by paolol on 2014-08-08
Hi , I have an old Fujitso server with SATA raid controller ( the MB have 2 xeon processor ) as time change I no longer need this server but still need the data and the program that are installed on it ( the company how create the program is no longer in business :( so I can't reinstall it ).
I build a new server ( just a PC ) for it , I did a dd of the disk and loaded on the new one but ( and her I need help ) the disks that hold the program and the data are not mounted ( those are the one that was using the raid controller ).
Hope any one can give me some suggestion on how to solve this.
Thanks to all

---

### Post by TheFu on 2014-08-08
Update - re-read the OP.

If you exactly mirror all the data without using the RAID cards bit-for-bit, the RAID encoding will be a huge problem. I don't think there is a solution unless you have the EXACT SAME RAID CARD (probably even the exact model and version) to access that data. 

OTOH, if you can backup the files/data, then put them back on new storage all will be fine.

Hardware RAID has that limitation and is best used only in business environments with on-site spares.
In a home environment, using software RAID is much more convenient and flexible, mainly because the data isn't tied to specific hardware to gain access.  Neither of these methods removes the requirement for good backups - perhaps the backups could be used to restore on the new system?

---

### Post by paolol on 2014-08-08
Thanks for the reply, I have the backup but is on tape and the tape recorder broke ( one of the reason I won't to drop this server ) and a new one is very expensive. I no longer need this data as my business changed but I need to keep it for old customer . but I think I can follow your idea of backup all the data on my external HD and then restore it. Did you think that will be a correct way to move the program to the new hardware ?
Thanks again

---

### Post by volkswagner on 2014-08-08
If you are planning on keeping the config as a legacy system, you may consider setting up a hypervisor such as KVM or Xen.
Use the appropriate P2V (Physical to Virtual) live migration.

Pick your hypervisor of choice and do a live migration.

---

### Post by TheFu on 2014-08-08
Whatever gets the files from the old storage to the new storage so they appear in exactly the same place in the file system is what you want.  That isn't a bit-for-bit copy, but a file-for-file copy.

So, if every file on the old system that matters to the programs is moved to the same place on the new system, that should be it. There isn't any "registry" and very few programs have license keys (though some do and will not work).  I've implemented license management in UNIX and Windows, but we used network license managers, so that licenses weren't tied to any specific machine, but were provided on the network (subnet limited, upto the purchased concurrent number).

If the data on the backup tape can no longer be read, then that is NOT a backup.

"Correct way?"  I don't know - but if it works, that should be good enough. ;)

---

### Post by paolol on 2014-08-09
Thanks I will try .
No the program was made by a small softerhouse and is in foxpro, so all file are on the server and I can easily try a backup-restore with an external HD, let see if this work :)

---

