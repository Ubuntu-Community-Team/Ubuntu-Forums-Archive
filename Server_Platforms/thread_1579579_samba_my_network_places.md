---
title: "samba my network places"
date: 2010-09-22
forum: Server Platforms
---

### Post by SilverSkull on 2010-09-22
Hey,

Ive been running 2x Samba servers for a while now, but one of them doesn't appear in 'My Network Places' on Windows XP.

Server 1:
(Appears in My Network Places)
Ubuntu 9.10, Samba 3.4.0

Server 2:
(Doesn't appear in My Network Places, but can be accessed by typing \\server02\share )
Ubuntu 10.04, Samba 3.4.7

Ive tried various settings to no avail. Any help would much appreciated.

Cheers,
Dave

---

### Post by robsablah on 2010-09-24
is the second server in the same workgroup?
:P

---

### Post by SilverSkull on 2010-09-27
Yeah, both servers are on the same workgroup.

---

### Post by R.Bucky on 2010-09-27
check your DNS. do you have the proper lookup zones set? are you operating DNS?

---

### Post by Ryan Dwyer on 2010-09-27
I think installing winbind fixes that.

---

