---
title: "I can only access my first NFS share."
date: 2010-06-13
forum: Server Platforms
---

### Post by u-slayer on 2010-06-13
Every time I try to mount a folder from my server, it ignores whatever folder I specify and just mounts the first folder in the exports file.

Here is my exports file:

```

/dir1  192.168.1.0/24(rw,no_root_squash,async,fsid=1234)
/dir2  192.168.1.0/24(rw,no_root_squash,async,fsid=1234)

```


When I try to mount dir 2:

```

mount -v 192.168.1.127:/dir2 /mnt/server
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Sun Jun 13 23:41:57 2010
mount.nfs: text-based options: 'addr=192.168.1.127'
192.168.1.127:/dir2 on /mnt/server type nfs (rw)

```

It gives me the first dir in the exports file. No matter what I type, I can't mount the second directory.

I'm pretty sure that I used to be able to mount more than one nfs folder, so I don't understand what is going on. Google isn't helpful.

---

### Post by Ryan Dwyer on 2010-06-13
Try using different fsids in your exports file. According to this page ([http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)) they should be unique.

---

### Post by u-slayer on 2010-06-14
> **Ryan Dwyer said:**
> Try using different fsids in your exports file. According to this page ([http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)) they should be unique.

THanks! That fixed it.

---

