---
title: "Help setting up backuppc"
date: 2007-08-22
forum: Server Platforms
---

### Post by KawiRider on 2007-08-22
Hello,

I am currently trying to set up a backup server running Ubuntu at work using BackupPC.  My supervisor and I chose this program since its a great freeware alternative to expensive Windows backup programs and it also (hopefully) offers all the functionality we need.  

Primarily, I've been the one working on this project and have only had limited success:  currently I've only been successful at backing up Windows PCs that are part of the local network (which is a simple 4-port router).  However, we will need to be able to do some remote backing up since we have multiple computers and routers that have been assigned ip addresses by the university in which we are employed.

Basically our network works like this:  the university has allotted us a certain number of IP addresses.  Since the number of computers we use is constantly expanding, many of the computers have now been grouped behind routers in order to free up IP addresses for later use.  Therefore we have some computers that have statically defined IP address, gateways, and DNS servers and some routers that are configured in a similar manner.  We will need to be able to back up all computers, whether behind a router or not.

Currently, our computer running BackupPC is behind a router and I'm trying to get it to back-up a "remote" computer (my personal laptop) that is assigned a static IP address by the University (and not behind a router).  

Here is any helpful information I can think of:
The laptop's NETBIOS name is dell700m
Full computer name: dell700m.someschool.edu
Workgroup: WORKGROUP
Assigned IP Host Name:  whale.someschool.edu

I have a user named 'backuppc' on my laptop with Backup Operator privileges and have disabled "Use Simple File Sharing" in order to correctly set backuppc's privileges.

nmblookup fails to find whale.someschool.edu
nmblookup -A fails to find <whale.someschool.edu's IP address>
(Is this because NMBLOOKUP only works for local network?)

The current error I am getting in BackupPC is:
**tree connect failed:  NT_STATUS_DUPLICATE_NAME** 
**tree connect failed:  NT_STATUS_DUPLICATE_NAME**
**Got fatal error during xfer (no files dumped for share bpc-docs)**
**Backup aborted (No files dumped for share bpc-docs)**

If anyone can help, it would be greatly appreciated.  Sorry this is such a long post but I wanted to be as detailed as possible.  I've worked on this project off and on since April (I'm a student worker) and now that we finally have the new server built, we need to get backups going asap.  Thanks again.

Regards,
KawiRider

** THIS IS MY OLD THREAD -- PLEASE RESPOND TO MY NEW THREAD IN THE GENERAL HELP FORUM.  THANKS**

---

### Post by tak1150 on 2007-09-10
[This website]("http://www.taksuyama.com/?p=13") has a good step-by-step instruction on building a backuppc server in an academic lab setting. If you have any more questions after you  read this site, let me know.

---

