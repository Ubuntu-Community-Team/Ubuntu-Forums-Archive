---
title: "How to save data to my slave hard drive on ubuntu server 12.04"
date: 2012-10-19
forum: Server Platforms
---

### Post by lazarojhr16 on 2012-10-19
i have a slave hard drive on my server. i mount it by doing sudo mount /dev/sdb1 /mnt 
it mounts but when i connect to it with my other ubuntu machine through ssh and drag something to /mnt. it says permission denied. ho0w do i transfer my data to the mounted volume. what i'm i doing wrong. i'm new to linux please explain. thank you.

---

### Post by darkod on 2012-10-19
I suggest you create a mount point for it instead of using the generic /mnt. For example:
sudo mkdir /media/hdd2

You can create which ever mount point you want. Then mount it automatically at boot by adding a line in /etc/fstab:
```
/dev/sdb1 /media/hdd2 ext4 defaults 0 2
```

If the filesystem is not ext4, change it accordingly.

As for permissions, you will need to allow writing to /media/hdd2 for the user you are using to connect. Or simply configure read/write for all if you don't need any limitations. You can do that with:
sudo chmod a+rw /media/hdd2

That should allow writing to it.

---

### Post by lazarojhr16 on 2012-10-19
Perfect that worked. thank you.

---

