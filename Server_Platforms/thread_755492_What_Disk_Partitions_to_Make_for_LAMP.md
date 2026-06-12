---
title: "What Disk Partitions to Make for LAMP?"
date: 2008-04-14
forum: Server Platforms
---

### Post by wagb278 on 2008-04-14
Starting with new computer that I intend to use as desktop and home (house) web/file server I would like suggestions for how to partition the hard drives.  I will have 80GB and 250GB SATA drives.  The server traffic will be low.  When I ordered the computer my plan was only to put the root stuff and /home (plus swap) on the 80gb drive and server-related files on the 250GB drive.  I figured a partition for a file server (Samba) for access by other computers to store/share and copy backups to.  

I'm new to Ubuntu and I am not sure where the LAMP data is placed - is it /var or /srv?   Suse ver 9.1 puts MySQL databases below /var and Apache's Document Root is in /srv/www/htdocs.  So the PHP files and some flat data directories are under htdocs.  I this the same as Ubuntu?

I think I would like all the server stuff in one partition but that is not necessary.  I just want to do what is smart and able to grow.  My new computer shoudl arrive late this week and I want to have a partition scheme when it arrives. 

So, how do all you experienced LAMP home users partition drives for your Ubuntu systems?

Thanks

---

