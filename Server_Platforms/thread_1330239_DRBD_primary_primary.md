---
title: "DRBD primary primary"
date: 2009-11-18
forum: Server Platforms
---

### Post by bm.mol on 2009-11-18
I am running two Ubuntu 9.04 servers with DRBD in primary primary mode. Both servers mount /dev/drbd1 as /var/vm. On both servers vmware is running.
I see there will be a difference (inconsistancy) between the two /var/vm.
 
When removing/adding files on one host in the /var/vm this is not replicated on the other host /var/vm.
 
why is this happening?

---

### Post by wyldfury on 2009-11-18
Does DRBD believe it is in sync?
What FS are you using?
Have you checked the logs?

---

### Post by bm.mol on 2009-11-18
DRBD is in sync
" cs:connected ro:Primary/Primary ds:UpToDate/UpToDate C r---"
fs is ext3
 
logfiles : Don't know where to look. /var/log has no drbd.log

---

### Post by wyldfury on 2009-11-19
Ext3 is not a clustered file system and so cannot be used in a primary/primary setup.
If you're going to use primary/primary then you need to look at OCFS2 or GFS2. I'd recommend OCFS2 on Ubuntu since I don't think GFS2 is considered production stable yet. OCFS2 also has some bugs in the versions included with Ubuntu prior to Karmic.

The [DRBD documentation]("http://www.drbd.org/docs/about/") includes instructions for setting up DRBD with OCFS2 or GFS2.
The ocfs2 kernel module is already included in the Ubuntu kernel so you should only need to install ocfs2-tools and do the conf files for it.

Logging for DRBD can be enabled in your drbd.conf.

---

