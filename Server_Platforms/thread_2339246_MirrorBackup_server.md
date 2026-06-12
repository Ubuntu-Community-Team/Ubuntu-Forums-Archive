---
title: "Mirror/Backup server"
date: 2016-10-06
forum: Server Platforms
---

### Post by shadowyangweb on 2016-10-06
Hi, I am planning to run odoo on ubuntu server. Therefore I'd like to have a mirror server as backup. When the production server goes down, the backup one can be online without any setup. 

I search and get a lot of result talking about rsync. But in my case will it the best solution? I am not just need to backup all my data. Also I need a server to be back online not real time but at least not spend me a whole day to reconfig everything. I am running odoo, apache/nagix and postresql on my server. That relates to ip and domain. So when I bring the backup server online. At least I need to reset all configs relate to that. 

I consulted my college. And he suggests me to use VM and snapshot. All applications run in prod vm on prod host server. then takes snapshot as backup. When prod host server down, I just need to restore the snapshot to backup host server. 

Do you guys think this is good idea? If that's the case, which VM software you guys suggest? Or rsync is simpler? maybe there is any other better/simpler solution? I will be very grateful if you can help me on this.

---

### Post by TheFu on 2016-10-07
You need 2 servers. Virtual or not, doesn't matter.

You need a way to mirror the systems to some point, but that can be accomplished in 50 different ways. You'll need to try a few after doing specific research on the available methods.

You need a way to keep the data synchronized between the active system and the backup.  There are lots of different ways to accomplish this and the best answer depends on how much data there is, how much data there will be in a year and how old the data can be from the time of failure.  

To discuss the best options, you'll need to determine the RTO and RPO requirements.  Just know that shorter times will impact cost, networking, and difficulty. 24 hrs for both is relatively easy. Normal daily backups will handle that.  Shorter periods require different answers.  If you want fully synchronized data written to both systems consurrently, then performance will take a hit.  

The "best" methods will be dependent on the network architecture and storage architecture deployed too.

You need daily, versioned, backups anyway, so I'd suggest starting there. Plus testing the restore is a good way to validate that the backups are working in a way that fits your needs.  Then if you need shorter periods of data replication, take a look at a master-slave DB server setup.  Also, for maintaining the OS and settings on multiple servers, using a DevOps tool like ansible could make sense and scales as the number of servers required increases.

Simple isn't always the best answer.  rsync has some great uses and may be the best answer for the static content replication.  For backups there are better answers and for DB replication, you will need to do more than just rsync.

---

