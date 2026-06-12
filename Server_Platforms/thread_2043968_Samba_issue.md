---
title: "Samba issue"
date: 2012-08-17
forum: Server Platforms
---

### Post by MikeyPooh on 2012-08-17
So i have my Server setup and i made a share in smb.conf, but yet when i browse the Server it is showing every folder in /

How Can i Fix This so it only shows folders i share?


Thanks

Mike

---

### Post by LHammonds on 2012-08-17
You have to set the path correctly.

[Look at how I setup my share]("http://www.hammondslegacy.com/forum/viewtopic.php?p=267&sid=26bc981e6c87515798fa19c7bf764929#p267")

LHammonds

---

### Post by MikeyPooh on 2012-08-17
this is what mine looks like, I Always set Security like this, So i dunno what the issue is


Thanks


Mike

---

### Post by LHammonds on 2012-08-17
You need to set it like I did.  **security = user**

The **guest ok = yes** allows them to access the share without a user ID.

It is also good for security and stability of your server if you share a partition that is separated from your root.  That way you can have a certain amount of space set aside for those files and filling it up will not bring the server to its knees (filling the root partition is bad).

LHammonds

---

