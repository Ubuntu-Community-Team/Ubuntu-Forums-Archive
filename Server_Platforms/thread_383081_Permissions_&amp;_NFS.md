---
title: "Permissions &amp; NFS"
date: 2007-03-12
forum: Server Platforms
---

### Post by thornomad on 2007-03-12
Hi

I have a partition on my server's hard drive I want to export via NFS and have available for everyone to use on my network.  I am able to export the drive and copy files from it no problem, but I can't get the permission to add files or modify them ... seems to be read only.  I have tried chmod-ing the directory but that didn't seem to work.

1. How do I set permissions so that anyone on the local network can add/delete/change the files from that mount point ?

2. How do usernames carry over ? (For example, if my username on my Mac and on the server are the same, will I have the same access to my files?)

3. I have my /etc/exports as:```
/share *(rw,synx,no_root_squash)
``` because that is what the ubuntu docs recommend ... I don't know what any of it means though.  Should I have it different?  Where can I find those options ?

Thanks,
Damon

---

### Post by Mr. C. on 2007-03-12
A good tutorial on NFS might be recommended.  For a start, have a look at week 4 "NFS / Automounter" coursework and the lab work at:

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

That should give you a better framework.  If you have questions after that, we'll go from there.

MrC

---

### Post by gostek_1 on 2007-03-12
Try mount -t nfs -o rw your_serv_ip:/share /mnt/share

---

### Post by thornomad on 2007-03-13
Hey, thanks for those links.  It looks like what I need is to have UIDs that match on both systems.  Interesting.  Okay, I am going to check out how to get those to match on all my machines.  I had never heard of the UID (numerical).  Will look into it more.

---

