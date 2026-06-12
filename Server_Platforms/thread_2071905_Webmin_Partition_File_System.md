---
title: "Webmin Partition File System"
date: 2012-10-16
forum: Server Platforms
---

### Post by MortenSJ on 2012-10-16
Hi

I just installed Webmin and Samba. This is my first Ubuntu Server so i'm quite new to this. I have a system disk which is an 60GB SSD and a storage disk at 2TB. I want to add the 2TB storage disk but i'm not really sure which file system i need to use. There is so many?

When the disk is mounted, can i use the file manager to add folders like Documents, Movies and so on?

---

### Post by ubhi on 2012-10-16
1. you can create ext2 or ext3 for your storage partion where you want to store files, 2. you can mount new hard drive in /etc/fstab on some folder see disk mounting on google

---

### Post by MortenSJ on 2012-10-16
Thanks, will i be able to see them on a mac?

What about Samba, i installed Samba Server but i'm not really sure what it does.

---

### Post by darkod on 2012-10-16
If the disk doesn't have any partitions on it, you will have to create partition(s) first. I suggest you use parted for that from the command line of the server (not webmin). In fact, I wouldn't use webmin at all, or use it minimally.

All you can do and learn from the CLI, do it.

After creating the partitions with the sizes you want, you will need to create a filesystem on them, like ext4.

Then you can create entries in /etc/fstab so that the partitions get mounted at boot on specific mount points.

Samba server is used to create shares which can be seen in your network. Yes, a Mac should be able to see them.

---

