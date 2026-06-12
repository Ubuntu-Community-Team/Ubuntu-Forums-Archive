---
title: "Partioning &amp; Installing"
date: 2008-04-08
forum: Server Platforms
---

### Post by amai on 2008-04-08
Have 500 gig SATA drive. I am going to partion as follows

/=15GB
Swap=3GB
/user=150GB
/home=150GB
/var=90GB
/tmp=90GB
/boot=2GB

What I want to do , is run a server for.
Hosting 6 websites
podcast
store data(document, torrents e.t.c)

MY Question is when to partion the drive.Partion using the CD(during installation ) or better using CLI and how do I name the partions.

Thanks

---

### Post by Oldsoldier2003 on 2008-04-10
> **amai said:**
> Have 500 gig SATA drive. I am going to partion as follows

/=15GB
Swap=3GB
/user=150GB
/home=150GB
/var=90GB
/tmp=90GB
/boot=2GB

What I want to do , is run a server for.
Hosting 6 websites
podcast
store data(document, torrents e.t.c)

MY Question is when to partion the drive.Partion using the CD(during installation ) or better using CLI and how do I name the partions.

Thanks

easier to partition it out during the install. you can tell Ubuntu where each directory resides when you install.

---

### Post by Rocket2DMn on 2008-04-10
You don't need a separate partition for each of those directories unless you actually know that you do.  Having a separate /home partition can be nice, but otherwise the rest of that stuff can just be under your root partition.  However, that's your own deal.

You can partition either way you'd like, both methods are equally effective.  Just remember that some of the partitions will have to be logical instead of primary (since you can only do 4 primaries, one of which will have to encompass the logical ones).

It may be easier to do it during the install if for no other reason than this is when you have to declare the mount points anyway.

---

### Post by amai on 2008-04-11
Thanks guys will partion during install.
Reason for partion is for security.

---

### Post by songshu on 2008-04-11
depending on what you would like to do and host the partition sizes seem  slightly odd to me.

p.s.

/user=150GB

i guess you mean /usr which stands for "Unix System Resources"

i call it user as well tough when i'm mumbling silently to myself during partitioning ;)

---

