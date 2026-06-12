---
title: "Can't cd to nfs mount"
date: 2011-02-09
forum: Server Platforms
---

### Post by peridian on 2011-02-09
I have a file share server hosted by a CentOS 5.5 install.  All the other Linux CentOS 5.5 boxes can mount the share no problem.

A Ubuntu Server 10.10 box however seems to be able to mount the drive, but then says cannot cd to the folder in question.  I have installed the nfs-common package.

The CentOS share has the following in its exports file:

/media 192.168.1.0/24(ro,sync,no_root_squash)

This allows use of mount server:/media /myfolder

The ubuntu box has the following in its fstab file:

server:/media /myfolder/media  nfs  defaults  0  0

I've tried setting up the users on both boxes to match, but this seems to have no effect.  The exact message is:

cd: <random number each time>: can't cd to media

Any ideas?

Regards,
Rob.

---

### Post by Kooothor on 2011-02-09
Hello,
Have you checked the permissions on the nfs share ?

---

### Post by volkswagner on 2011-02-09
Silly question, does /myfolder/media exist?

If you list the contents what do you get.

```
ls -alt /myfolder/media
```

---

### Post by peridian on 2011-02-10
It does appear to be a permissions issue, but I can't get the two to sync...

I'm setting up an LDAP server anyway so I'll get that setup and set permissions using that so that the two machines are in sync.

Thanks anyway,

Rob.

---

### Post by volkswagner on 2011-02-10
I seem to recall NFS users need to be the same UID number, not only the name and password need to match.

---

