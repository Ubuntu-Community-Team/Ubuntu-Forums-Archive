---
title: "Building a raid array, do I need to use LVM?"
date: 2014-03-02
forum: Server Platforms
---

### Post by jason63 on 2014-03-02
Hey guys. Virgin linux user here.

I'm doing testing on my new Ubuntu Server (Im 3 days into it) and I've got a question about the LVM.

I was shown when creating an array to;

1. create the array
2. add it as a volume group
3. add a logical volume from that group
4. create file system of type (ext4)
5. mount the LV.
6. set permissions on mount to 777
7. share the mount in samba server with 777 permissions



What I have done is;

1. Created an array
2. create file system of type (ext4)
3. mount the array as /mnt/ARRAY
4. set permissions on mount to 777
5. share the mount in samba server with 777 permissions

The way I just described works great, no LVM to deal with, and speeds over the network smb share are perfect.


Am I doing any harm, just mounting the formatted array and sharing it? Why do I want to use logical partitions instead of just mounting the formatted array?

Thanks guys!


Jay

---

### Post by nerdtron on 2014-03-03
The purpose of LVM is to "create a pool" of storage and then from this pool of storage you can create "logical storage" which you can expand, shrink, anyway you want. Now if you already have the raid array you want and use the whole raid as a single storage, I guess there's no point to choosing LVM.

---

### Post by jason63 on 2014-03-03
Is there a performance hit for using LVM?  I'm only transferring over GBe.

---

### Post by nerdtron on 2014-03-03
Yes there is, I think it consumes a bit of CPU and write speed can be affected too due to the overhead of LVM. I think it can be negligible in server class hardware.

---

