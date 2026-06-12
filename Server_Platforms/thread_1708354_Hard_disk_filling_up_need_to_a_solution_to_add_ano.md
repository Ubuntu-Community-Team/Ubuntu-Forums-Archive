---
title: "Hard disk filling up need to a solution to add another disk"
date: 2011-03-16
forum: Server Platforms
---

### Post by aliahsan81 on 2011-03-16
Hi All


I have a directory /var/log/data its about 80 GB,It filling up quit rapidly.I don't have much space left in the system them So i will attaching another External HDD.My question is that i need to mount /var/log/data to new HDD.So i have old data and pulse new coming up.I don't want to copy data from /var/log/data then  mount new HDD to /var/log/data you know what i am taking about is there a simple way like linking or any other.

---

### Post by cariboo on 2011-03-16
You could use a symlink eg:

```
sudo ln -s /var/log/data /media/disk/var/log/data
```

---

### Post by BkkBonanza on 2011-03-16
I think you may want that ln reversed, and also rename the current data first, eg.

assuming your new disk is at /media/disk 

mkdir /media/disk/data
mv /var/log/data /var/log/olddata
ln -s /media/disk/data /var/log/data

Your data from before the change will be at /var/log/olddata and the new data will get routed on to the new disk in the /data directory.

---

### Post by nosebreaker on 2011-03-16
Did you set the drive up in a LVM ?  You can expand a LVM across multiple drives if you did.  I did it and it wasn't too complicated (search for "howto expand lvm ubuntu" or similar).

---

### Post by Vegan on 2011-03-16
Another idea is to limit the size of the log files by aging.

---

