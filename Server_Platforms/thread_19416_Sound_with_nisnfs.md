---
title: "Sound with nis/nfs"
date: 2005-03-11
forum: Server Platforms
---

### Post by joepotter on 2005-03-11
I have a small lab with 20 Debian boxes. I set up Hoary Hedgehog on one of them and it went just fine. User "lab" had sound and all that.

Then, I went with nis and nfs to allow all the 120 users access to the box. I had to give root a password (or so I think so) and all went just fine. 

The problem? Sound went away. Do I need to add all the users to some group? Change permissions somewhere?


Thanks, Joe

---

### Post by alastair on 2005-03-11
Probably permissions somewhere.

Log in as the (non-NIS) user (i.e. where sound works) and check what groups you belong to e.g.

id

There might be an "audio" group there perhaps. Perhaps add NIS users (who need sound access) to this group (on the NIS server).

---

### Post by joepotter on 2005-03-14
[QUOTE=alastair]Probably permissions somewhere.

Log in as the (non-NIS) user (i.e. where sound works) and check what groups you belong to e.g.

id

There might be an "audio" group there perhaps. Perhaps add NIS users (who need sound access) to this group (on the NIS server).[/QUOTE]


Thanks, I will try that today. It seems that the "audio" group is what I must add.

Regards, Joe

---

