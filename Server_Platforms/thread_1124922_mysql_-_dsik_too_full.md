---
title: "mysql - dsik too full"
date: 2009-04-13
forum: Server Platforms
---

### Post by heitjer on 2009-04-13
I need some help!

My server will not start again. It stops at

```

starting MTA: exim4
/etc/init.d/mysql [3793] ERROR: The partition with /var/lib/mysql is too full
starting samba daemons
```

And it hangs right there. 

It started when I copied new photos to my server. This particular drive is probably too full.

---

### Post by jms1989 on 2009-04-13
Run df -h to see if your root partition is full. Your root partition is /.

---

### Post by BkkBonanza on 2009-04-14
You're probably right - your drive is too full. So either a. remove files or b. add more space. If you have been using this server for a while and have not configured suitable log rotation then you may also have a situation where your logs have grown huge and consume a lot of space. Check /var/log and see what's there. If so then it's good to read up on log rotation and how to set that up so you don't keep them forever.

---

### Post by hyper_ch on 2009-04-14
or move the mysql dbs to a different location where you have more space.

---

### Post by heitjer on 2009-05-03
I want to close this out. The disk was actually to full. My server contains 4 old PATA drives and one of them that I use a temp directory to move files between machines was completely full. The systems still showed 40% free (webmin) but this one temp directy was one old 4GB HD and when it was full it caused this error.

Solution:
Found an old Knopppix CD, started root terminal and deleted the files on the temp directory. After that the server started again.

---

