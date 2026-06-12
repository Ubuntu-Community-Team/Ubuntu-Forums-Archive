---
title: "Backup to removeable disk"
date: 2006-11-20
forum: Server Platforms
---

### Post by alanandhispc on 2006-11-20
Hi,

I would like to set up a edgy box that copies windows shares/files to a removeable disk, how does edgy cope with removeable media?

I would like to cron job the backup operation daily, allowing me to remove the removeable hard disk without any operation on the server itself. I have 5 disks for monday through to friday, so the script will have to know that it will back up to any of these disks.


I would prefer to do a fsync or alternative operation on the vast majority of the shares to save on backup time, is fsync the best as i know it's a bit more itensive on the cpu (servers is a pentium 3 700mhz with 768mb ram)

any thoughts on the best way to acheive this?

Many Thanks

Alan

---

### Post by Macchi on 2006-11-20
Hello Alan,
You probably mean rsync and cron for taking efficient snapshots of your system as a backup? There are dozens of guides on how to customize backup solutions with these great tools.

On Ubuntu (Debian), there is also an application called simple-backup that is immediately available on the (universe?) repositories. It is very easy to use and can be good for a very fast start. Later you may need something more professional customized for your needs. 

How do you change disks? Do you have hotswap disks or is it ATA over Ethernet? I am not yet sure on how is the kernel support for these cases.
Otherwise, if they are using ordinary IDE or SATA harddisks on trays you will have to manually stop, swap disks, and restart the system.
Such manual switching process is prone to many risks for corrupting information and destroying hardware (for instance, ESD may destroy disks, all background processes have to terminate nicely.)  

Personally I am using USB disks that have a low cost and can be hotswapped quite easily without shutting down the server. The drawback is a slower interface but it can be acceptable for backup purposes. Of course it is still necessary to unmount and remove the disks manually. An alternative is to keep only two or three disks connected at a time and rotate them less often to avoid the physical risks of handling hardware.

Ideally the backup disks should be on separate machines and even on different physical buildings and networks, and connected to independent powerlines. Obviously on shock-absorbing boxes inside a fire-resistant safe on a earthquake-safe building ... 

Good luck and keep in touch!

---

### Post by alanandhispc on 2006-11-21
Yeah i did mean rsync, i use a tool called fsync in windows which has similar functionality and keep getting them the wrong way round.

The back-up script/tool will have to pull data from multiple windows shares, so not sure if simple-backup will cut it.

Was concerned about the removeable disk, it's a hotplug bay with sata disks. The bay has a key lock on it that when you unlock it the disk wan be pulled out.

i guess that no matter what disk is in that bay it will always have the same device name (ie sda1 etc.), so do you think a script to unplug and re-initilize that device will be on the cards, this is with edgy afterall.

any thoughts on this anyone?


Many Thanks

Alan

---

### Post by Macchi on 2006-11-21
Hello again,

To backup information pulled out of windows shares you will have to make them available (smb mount) them anyway in your system, thus it will not be a problem as long as you resolve such things as access permissions and locked files. The idea with simple backup was only to have a very quick start but definitely not as a permanet solution. It is not bad but there must be something better for production machines.

The devices will have the same name but volumes may be different if you wish. That could be used to affect the mount point and to steer something in your backup solution. 

Yes, I know that these bays have mechanical locks to prevent accidental removal of drives. I was more concerned with the solution for hotswap of disks on Linux and with the physical handling of the disks.

Does anyone knows a good solution for hotswaping disks? I am also curious to find something but will not have time to google for that information right now.

---

