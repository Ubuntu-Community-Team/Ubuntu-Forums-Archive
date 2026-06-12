---
title: "Set-up RAID-1"
date: 2006-08-01
forum: Server Platforms
---

### Post by jacrider on 2006-08-01
I have managed to set-up a SAMBA server in our house for documents, images, etc. ... not too bad actually.  No LDAP or anything, but a very simple file/printer server.

Next on my list is to safely store all the data on the server.

I am running Ubuntu on a 40GB drive.

I have two new 160GB IDE drives that I want to set up as mirrored storage without a dedicated hardware RAID controller.  My loads will be very low, so I think a software solution is fine.

How do I do that?  I have searched and found many different ways ... fake RAID, mdadm, etc.

Is there a simple HOWTO or a good web resource I haven't found?

Many thanks!

---

### Post by jacrider on 2006-08-01
Tried a search on Yahoo! and found this reasonable HOWTO:

[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html?page=1)

I will try this tonight if I have time.  I haven't even installed the drives yet.

---

### Post by jacrider on 2006-08-03
Well this worked.

Getting my machine to recognize the drives was harder.  This server uses scsi drives and IDE.  I have Dapper installed on a scsi, but wanted the network storage on the IDE drives.  Setting all the boot priorities and so forth was more work than the RAID.

Once the drives were formatted, setting up the RAID 1 array was really easy.  Followed the how-to in the link above.

Mounted it with a line in fstab.

Took a while to get all the permissions straight so everyone can create both files and directories.

Everyone in the house can get to it and use it.  I have moved "My Documents" for all my kids to this array.  Worked like a charm.

---

### Post by Macchi on 2006-08-22
Welcome to the club!
I have also a server for my small office/home office configured with two RAID 1 partitions respectively for the system root (/) and home directories (/home). Additionaly I have bulk storage on a third harddisk for information that already has backup copies somewhere else.

There are advantages and disadvantages with software RAID. Primarily believe that I get a higher level of reliability since the server will not be dependent on single harddisks. The cost is low and the setup is quite simple, using only standard hardware.

Observe that a RAID solution does not eliminate the need for backup copies!  
Be careful to check the logs and activate system email notifications, to get information on what is going on. Once I discovered that one of the disks actually had a soft failure and thus I happened to be running the server for a few weeks without knowledge of the problem. Afterwards I could easily restore one of the copies through a few commands.
The server worked without any noticeable disruptions all the time.

The magazine Linux Journal had recently an article on recovering information from LVM on RAID, a procedure that is quite complicated and risky. I hope that recovering ordinary ext3 partitions on RAID is easier but I try to avoid that at all, thus keeping updated copies of my valuable data somewhere else. The separate partitions for / and /home facilitate to restore only the data and/or the system.

Previously I used to run SuSE 9.3 and 10.0 but now I moved definitively to Ubuntu Dapper server due to the advantages of the Debian base and the nice atmosphere at the Ubuntu comunity.  

Sincerely,

---

