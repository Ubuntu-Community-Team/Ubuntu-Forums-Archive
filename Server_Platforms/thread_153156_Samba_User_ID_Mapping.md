---
title: "Samba User ID Mapping?"
date: 2006-03-31
forum: Server Platforms
---

### Post by Absolute on 2006-03-31
I have a problem right now, with mounting a samba drive between two Linux boxes.  Actually, it's mounting from two separate boxes, to my Ubuntu 5.10 box.

My user name is jeff on all three machines, but on the two I'm mounting from my user ID is 500, while on my Ubuntu desktop it's 1000.  When I mount the Samba drives between my two machines, as cifs, it maps them with an owership of user  ID 500.

Both machines require me to authenticate as jeff before mounting, making me assume that they're being mounted with my user ID on those two machines.  I can't seem to find a way to mount them with my Ubuntu user ID, though.

In /etc/fstab I've specific uid=jeff and uid=1000, but they still map with user ID 500.

Any ideas?

Thanks!

---

### Post by Iowan on 2006-03-31
Manually edit the UID in the passwd file(s)?

---

### Post by LordHunter317 on 2006-03-31
The short story is you can either sync your passwd and group files across all the machines (and fix permissions) or turn off 'unix extensions' on the Samba server.

---

### Post by Absolute on 2006-03-31
[QUOTE=LordHunter317]The short story is you can either sync your passwd and group files across all the machines (and fix permissions) or turn off 'unix extensions' on the Samba server.[/QUOTE]

Excellent, thanks for the help!  I turned off the unix extensions, and I can now write properly to the share which mounts under my Ubuntu UID.

---

