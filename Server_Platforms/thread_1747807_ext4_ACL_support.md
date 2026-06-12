---
title: "ext4 ACL support"
date: 2011-05-03
forum: Server Platforms
---

### Post by DustWolf on 2011-05-03
Hello,

Does Ubuntu Server 10.10 i386 (2.6.35-28-generic-pae) support EXT4 ACLs?

The ext4 documentation [apparently]("http://ubuntuforums.org/showpost.php?p=6896997&postcount=3") states:
> acl Enables POSIX Access Control Lists support.
Additionally, you need to have ACL support enabled in
the kernel configuration (CONFIG_EXT4_FS_POSIX_ACL).
See the acl(5) manual page and [http://acl.bestbits.at/](http://acl.bestbits.at/)
for more information.

...I have no idea what the Ubuntu Server kernel configuration is.

I would like to insert the "acl" mount flag into my fstab and wouldn't want to make my machine unbootable if there is no support.

Anyone?

LP,
Jure

---

### Post by kgatan on 2011-05-03
I have ACL active on my ubuntu 10.04 backup server.
You just add "acl" to the options part in fstab.

Ex mounting md0 to "/mnt/storage" using ext4 and acl.

```
/dev/md0        /mnt/storage    ext4    acl,errors=remount-ro   0       1
```


Im a noob so i take no responsibility if you break something, but it works for me :)

---

### Post by DustWolf on 2011-05-04
> **kgatan said:**
> I have ACL active on my ubuntu 10.04 backup server.
You just add "acl" to the options part in fstab.

Works! Can now set ACLs from windows workstations over Samba.

LP,
Jure

---

