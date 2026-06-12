---
title: "partitioning two 300gig hd for server"
date: 2005-12-26
forum: Server Platforms
---

### Post by rcpettit on 2005-12-26
I have two 300 gig drives in a server box and was wondering what would be the best partitioning scheme for a system that will be running a large database that will be accessed from the web.  I'll be running apache2, php5, mysql.

was thinking about
 / 30 meg
 /usr 60 gig
 /home 100 gig
 /var for the rest.

---

### Post by LordHunter317 on 2005-12-26
That sounds totally wrong to me (for starters, you won't even install with a / that small).  How important is this server?

If all you have is two 300GB drives, then you should setup RAID-1, and have a single /.  Your performance will be poor, but you dont have enough muscle.

If you don't care about your data, then dedicate a whole drive to the database.   You'll get better I/O that way.  For the rest of the system, I'd have a /home (if needed) that's as big as it needs to be, and make / encompass the rest of the other drive.

---

### Post by rcpettit on 2005-12-26
Oops.  Too much turkey.  / is support to be 30 GB :???:

---

