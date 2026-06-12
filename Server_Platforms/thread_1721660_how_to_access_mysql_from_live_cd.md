---
title: "how to access mysql from live cd ?"
date: 2011-04-04
forum: Server Platforms
---

### Post by Tosho on 2011-04-04
ubuntu 10.04.2 LTS (64-bit)

Hi there,
I pretty much crashed my Ubuntu 10.04 and now it's not able to boot but I can access the partition with the LiveCD. I need to export my old mysql database from, how to do it using the Live CD? so I can make fresh install.
Can I copy the /var/lib/mysql files and dirs to NTFS partition and use them after the install??

---

### Post by SeijiSensei on 2011-04-04
There's a good chance of that, but I'd tar the entire directory first since NTFS knows nothing about Unix permissions:

```

cd /var/lib
sudo tar czvpf mysql.tgz mysql

```

Use "tar xzvf mysql.tgz" to unpack the compressed tarball.

In the future you should consider running daily backups with mysqldump. There are some threads about how to do this on the forums.

---

### Post by Tosho on 2011-04-05
thanks for the tip :) I'll try it later and see what will happen.:popcorn:

---

