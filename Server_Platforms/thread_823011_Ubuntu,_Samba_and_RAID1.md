---
title: "Ubuntu, Samba and RAID1"
date: 2008-06-08
forum: Server Platforms
---

### Post by pred02 on 2008-06-08
Hi,
I already have an existing Win XP configuration with a boot drive and two file server drives in RAID1 on a separate interface. If I was to install Ubuntu, then Samba on the boot drive, will the integrity of two file storage drives (RAID1) be retained? I think the RAID integrity is maintained by the controller as it would ask me to rebuild at the boot if the RAID is broken.

In short, would this work:
1) Install Ubuntu on the boot drive
2) Ubutnu and Samba would recognize the RAID and all the files
3) Share the drive in RAID to the network via Samba?

I have a generic Rosewill controller, probably the hard part would be to find RAID drivers for Ubuntu.

Thanks!

---

### Post by samosamo on 2008-06-09
Same controller?  Yes, its that easy.  You should still back up all data before attempting this.

If you're worried about the controller being compatible find out what chipset is on it (lshw or lspci on a live cd) and then google it.

---

### Post by windependence on 2008-06-09
Unlike Windoze, you don't generally have to go frogging around looking for drivers to "load" in Linux, most of them are either compiled into the kernel or loaded as modules at boot after the hardware is detected. you should be fine with the controller, but a backup is a must. Even with RAID, it is not substitute for good backups so you should be doing this anyway.

-Tim

---

### Post by pred02 on 2008-06-09
> you should be fine with the controller, but a backup is a must.

A backup before I attempt to reform/Ubuntu installation or keep a backup in general?

My file server (the two drives in RAID1) store the following for a number of PCs in the household:
[LIST]
[*]Shared multimedia (pictures, music, videos)
[*]Acronis Image backups (workstation nightly backs are stored on the drive)
[/LIST]
In case of the workstations fails, there is an image of the backup on the file server. In case a drive on the file server fails, there is the second drive (RAID1).

What is not fault-proof reading this? (besides both drives failing at once but what are the chances of that?)

> If you're worried about the controller being compatible find out what chipset is on it (lshw or lspci on a live cd) and then google it.

Rosewill RC-201 and there are drivers for it so I am ok. 

Two more questions:

1. I currently use Acronis to back up images of workstation drives to the shared file server. All my workstation machines are Windows. What would be a recommended back storage where I can manage the backups from the Ubuntu File Server and install clients to all Windows machines on the network (all are Win XP Pro)?

2. I read "out of box" there is a problem between Linux and NTSB partitions. The current file system on the RAID1 file server drives is NTSB. Do I need to install NTFS-3g? The read/write from the Client computers are going to be for the most part XP machines.

I appreciated the info.

Thanks!

---

