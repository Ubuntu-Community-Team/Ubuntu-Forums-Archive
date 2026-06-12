---
title: "Adding new SSD's to a database server  - Postgres"
date: 2012-07-05
forum: Server Platforms
---

### Post by Transition on 2012-07-05
I have a postgres database server i'm running 12.04 on.  I originally setup the box to use a  single sata disk for the primary storage.  I've since added an SSD to the box that i want the postgres portion to be served from.  

What would be the best approach to making sure the database read/writes are served from the SSD's and not the SATA disks?  Should i create a new mount point then move the postgres files to that new mount or just use something simple like a symlink and move the files to the ssd?

---

### Post by SeijiSensei on 2012-07-05
Either would work, but I recommend mounting the SSD to /var/lib/pgsql.

First, create a filesystem on the SSD with mkfs.  Then shutdown PostgreSQL with "sudo postgresql stop".  

Now we'll mount the SSD to a temporary mount point and transfer the files.  Let's suppose that the SSD has an ext4 filesystem in /dev/sdb1.

```

sudo mkdir /mnt/temp
sudo mount /dev/sdb1 /mnt/temp
cd /var/lib/pgsql
sudo rsync -a . /mnt/temp

```

You should now see the entire /var/lib/pgsql directory structure replicated on /mnt/temp. 

Next add an entry to /etc/fstab like this:

```
/dev/sdb1  /var/lib/pgsql    ext4     defaults  0  0
```

Now we'll move the current /var/lib/pgsql to a safe place and mount the SSD:

```

sudo mv /var/lib/pgsql /var/lib/pgsql.old
sudo mkdir /var/lib/pgsql
sudo chown postgres:postgres /var/lib/pgsql
sudo mount -a
mount

```

The last mount command should show the SSD mounted to /var/lib/pgsql.  Now try starting the server with "sudo postgresql start".  Everything should now be working fine and using the SSD for PostgreSQL.

---

