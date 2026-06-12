---
title: "Ubuntu won't share with Ubuntu"
date: 2010-04-20
forum: Server Platforms
---

### Post by nipsy on 2010-04-20
I hope I'm not breaking any kind of Forum etiquette by posting another question while one is still "unsolved", but I'm stuck again.

Server running Ubuntu 8.04 regular edition- 

2 Vista Premium laptops- see all computers on network

One desktop running Vista Basic- sees laptops and dual boot desktop, but not server

and the most recent one that we are trying to solve: One desktop newly installed with Ubuntu 8.04 that can not get into the Ubuntu server but can get into laptops with vista installed

When we try to get into the server, receive the "unable to mount location" error.

We have samba and ssh running plus nautilus.

We configured the smb to make sure the workgroup was correct and the same. I feel like we are missing one tiny part and just can't figure out what.

We did reinstall the Ubuntu desktop just to make sure it installed correctly. Any ideas?

---

### Post by carl4926 on 2010-04-20
In a terminal

ssh xxxx@serverIP

xxxx= server username

---

### Post by nipsy on 2010-04-20
> **carl4926 said:**
> In a terminal

ssh xxxx@serverIP

xxxx= server username

Thank you, we got in perfectly!!

Just in passing, why do we have to use the IP way when the ubuntu server will just mount, ask for password, and let us in to all the others??

---

### Post by carl4926 on 2010-04-20
I can't really answer anything about winders.

remember 

ssh -X xxxx@serverIP

will let you then say start an app on the server Eg: *firefox*
and have X display
So long as you have that in permissions

---

### Post by Iowan on 2010-04-20
> **nipsy said:**
> I hope I'm not breaking any kind of Forum etiquette by posting another question while one is still "unsolved", but I'm stuck again.Having multiple threads going is certainly not breaking any etiquette - if fact, it's encouraged. Separate threads makes it easier to concentrate on one problem - and close it out when solved. Someone else searching for a solution to the same (or similar) problem is more likely to find it, too.
Marking solved threads as such is also recommended/appreciated!

'Ya done good... =D>

---

