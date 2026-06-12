---
title: "install fails on poweredge 2650"
date: 2006-10-06
forum: Server Platforms
---

### Post by Draaku on 2006-10-06
Hi,
I first tried the ubuntu-server disc, then i tried the pressed ubuntu desktop disc, but they both fail when starting to copy files. I get all through the partitioning then boom.
 
The machine is a Dell PowerEdge 2650, BIOS up to date, RAID SCSI firmware up to date, 4 drives in a RAID 5.
 
Has anyone been successfull in installing on one of these? canyou shed some light on my end?

---

### Post by Draaku on 2006-10-07
The error message after creating the partition is:

"Failed to create file system"

While shutting down I also see this:

"Stopping RAID monitoring service - FAILED"

](*,)](*,)

---

### Post by Draaku on 2006-10-07
well, it turned out to be a none issue. Last night before I left I re-created the RAID. This morning I tried the install again and it took. wierd if i dont say so myself. I'm pretty stoked to have this setup. it is going to be our backups location and file server. I have VNC and SSH installed plus Webmin for configuring. It is also joined to the SBS domain.

---

