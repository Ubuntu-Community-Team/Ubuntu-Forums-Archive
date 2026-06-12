---
title: "Ubuntu Server drive partitioning recommendations"
date: 2008-05-29
forum: Server Platforms
---

### Post by rcpettit on 2008-05-29
I've been playing around with a basic webserver using ubuntu 7.10.  Wanting to start from scratch with server edition 8.04.  On the old server I had everything in one partition.  The server has a 300 gig hd.  I've searched the web and it seems to be very arbitary on the size of the partitions.  I plan on using the server to run a large MySQL database and photogallery.  So far the only thing I could find that was consistant was:
 
Swab = twice amount of memory
/ = no more than 1 gig.
 
Any help would be appriciated.

---

### Post by NateMan on 2008-05-29
There are several other posts regarding this subject, even just recently. As far as partitioning goes, if you set your / to only have 1gig then you have to make separate partitions for each of the major directories from there. You may want to try a simpler formatting scheme if your not very familiar with how much space you need in each. Why don't you make a /home partition, a /var partition, a / partition, and a swap partion? Where are you planning placing your photos? I'm also not sure about how large you intend on your mysql database should be.

---

### Post by rcpettit on 2008-05-29
Ops sorry about that, I ment /boot not /.  I've looked thoughout this site for partitioning help, only finding how to use parted, etc.  What I'm thinking about doing is using the following scheme:
 
/swap = 4 gb
/boot = 1 gb ext2
/ = 40 gb ext2
/home = 200gb LVM
/var = 10gp ext
 
 
move my mysql data files from /var/lib/mysql to a chowned directory located in /home.

---

### Post by NateMan on 2008-05-29
Yeah that looks good. You can just symlink to the directory in home for that, should work well.

---

### Post by rcpettit on 2008-05-29
I was wanting to move my mysql data files to the /home directory so I only need to back up just one partition.

---

