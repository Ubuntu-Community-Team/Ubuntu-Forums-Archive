---
title: "Large storage system"
date: 2013-11-11
forum: Server Platforms
---

### Post by a.hk on 2013-11-11
Hi!

I'm new to the forum but have been using ubuntu for some years now, my problem is that i'm a noob at large server systems. so my question is :

How can i set up a system, that makes 2 or more (multiple) physical servers look like one big storage server, with capability to expand. Lets say i have 2 servers with 4 TB storage each, what i want is to combine the 2 servers storage capacity so it look's like one HDD with 8 TB storage. And then i want a third server sharing that "virtual storage" as a CIFS share. And if at a later point I need more storage capacity i can just add another server. is this possible, and if so, how?

Thanks in advance!

( Sorry for bad english!! )

---

### Post by nebileix on 2013-11-11
You are looking for distributed filesystem like glusterfs, andrewfs etc. Try looking in that direction.

---

### Post by a.hk on 2013-11-11
> **nebileix said:**
> You are looking for distributed filesystem like glusterfs, andrewfs etc. Try looking in that direction.



Thanks for quick reply! 

I have already looked at GlusterFS, wasn't sure if it was what i was looking for, but i will give it a try and post later when i have tested it. ;)

---

### Post by nerdtron on 2013-11-12
Looks like a description of CEPH to me.
I have a cluster of 3 server for a total of  9TB storage. If I need more storage or need to add another server it is just a few commands and I have more.

---

### Post by nebileix on 2013-11-12
> **nerdtron said:**
> Looks like a description of CEPH to me.
I have a cluster of 3 server for a total of  9TB storage. If I need more storage or need to add another server it is just a few commands and I have more.

Yep, CEPH is nice and look promising.

Oh, and that remind me of lustre as well.

---

### Post by a.hk on 2013-11-12
Hi, i have tested GlusterFS and everything works great, was exactly what i wanted. Thanks for all help!

---

### Post by nebileix on 2013-11-13
Good that it is working for you. :D

---

