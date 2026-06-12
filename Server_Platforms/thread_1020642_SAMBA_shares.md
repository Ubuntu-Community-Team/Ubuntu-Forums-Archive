---
title: "SAMBA shares"
date: 2008-12-24
forum: Server Platforms
---

### Post by neomaximus2k on 2008-12-24
I have a question about SAMBA shares, I have multiple folders being shared across the network, most are public with one being private to a set username.  My question is this, I have one folder that I would like everyone to have read access to, however one user should be able to have write access (say admin user for instance)

Does anyone have any ideas on how this can be done?

---

### Post by namdung on 2008-12-24
Share the folder twice, once with read only access to everyone and then read write access to the special user.

---

### Post by neomaximus2k on 2008-12-24
> **namdung said:**
> Share the folder twice, once with read only access to everyone and then read write access to the special user.

LoL I was thinking of doing that but figured it would mess up permissions, will give it a try later on

---

### Post by Iowan on 2008-12-26
I can't remember the exact option, but you should be able to set up a "write list" allowing only the user "admin" the rights.

---

### Post by neomaximus2k on 2008-12-26
> **namdung said:**
> Share the folder twice, once with read only access to everyone and then read write access to the special user.
This didn't work, instead the last entry took over the first and meant no one could write to the folder.

> **Iowan said:**
> I can't remember the exact option, but you should be able to set up a "write list" allowing only the user "admin" the rights.

I have since setup webmin to handle samba shares rather than keep editing the conf file.  There is a read/write users list but thats about it, is this what you are refering to? That also means for each windows user I would have to create a user for samba.  This is why I thought directory service would be easier lol

btw my webmin specs say
```

Operating system 	Ubuntu Linux 8.10
Webmin version 	1.441
Time on system 	Fri Dec 26 21:36:58 2008
Kernel and CPU 	Linux 2.6.27-9-server on x86_64
System uptime 	10 hours, 2 minutes
CPU load averages 	0.13 (1 min) 0.03 (5 mins) 0.01 (15 mins)
Real memory 	3.87 GB total, 378.20 MB used
	
Virtual memory 	9.48 GB total, 0 bytes used
	
Local disk space 	358.58 GB total, 13.62 GB used

```

---

### Post by jonabyte on 2008-12-26
use:

```

security=user

```

in the conf file and setup users/groups and rights.

---

### Post by Iowan on 2008-12-27
> **neomaximus2k said:**
>   There is a read/write users list but thats about it, is this what you are refering to?
No, but I'm a couple of hundred miles from my Samba book... There's a "WRITE LIST =" option for shares (or something similar).

---

### Post by neomaximus2k on 2008-12-29
> **jonabyte said:**
> use:

```

security=user

```

in the conf file and setup users/groups and rights.

When I tried this it wouldn't allow any one else to access the folder, I need people to access the folder but only a few users to have write permissions

> **Iowan said:**
> No, but I'm a couple of hundred miles from my Samba book... There's a "WRITE LIST =" option for shares (or something similar).

I couldn't find anything to that extent

---

### Post by Iowan on 2008-12-29
Back home... my "Unleashed" book mentions that **write list=username** is to grant write permissions on a per-user basis to an otherwise read-only share (and in fact, overrides the **read list=** parameter, and the **read only=yes** option.

---

### Post by neomaximus2k on 2008-12-30
> **Iowan said:**
> Back home... my "Unleashed" book mentions that **write list=username** is to grant write permissions on a per-user basis to an otherwise read-only share (and in fact, overrides the **read list=** parameter, and the **read only=yes** option.

Thanks for the advice, it would appear the read/write list under webmin adds that line into the config file, still not working but not to worry i'll get there

---

