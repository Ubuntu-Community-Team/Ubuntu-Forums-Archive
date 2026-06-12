---
title: "Recovery required"
date: 2010-06-23
forum: Server Platforms
---

### Post by happyhacker on 2010-06-23
My server is not accessible any longer locally (192.168.0.2). If I attach a keyboard and login (I have done one pass of recovery from the Ubuntu live CD which helped) and check the IP address it seems to be set. However looking at the syslog file there is a line which says ext3-fs: info: recovery required on read only files system.

Is there a more extensive ext3 recovery facility I can use bearing in mind I will not (?) be able to install it?

I think I'm running 8.6 but not sure where to look to find it.

---

### Post by iponeverything on 2010-06-23
This is the command to check and fix you filesystem, where the "xx" is your disk and partition. The "-y" is "Assume  an answer of ‘yes’ to all questions" -- run:

```
sudo -i
```

to have root privileges to fix the file system.

```
fsck.ext3 -y /dev/sdxx
```

To see your Ubuntu version run:

```
cat /etc/lsb-release
```

---

### Post by happyhacker on 2010-06-24
What does sdxx mean? Do I just type "sdxx" in?

---

### Post by iponeverything on 2010-06-24
xx is the disk and partition respectively. 

to see what your root partition is run the command:

```
mount |grep " / "
```

it should print something like:

```
/dev/sdxx on / type ext3 (rw,relatime,errors=remount-ro)
```

the xx will be your disk and root partition.

---

### Post by happyhacker on 2010-06-25
Thanks, I tried that but it said that all was OK. But I cannot start the system and see it on my network. I start the Live CD and if I look at the sda1 filessystem lots of the folders are crossed out and sais I do not have permissions to access them. Also during the boot process on the screen (not the live CD) things like the Apache logs cannot be opened or Apache started. Is it possible I have a corrupted boot sector? How can I check?

---

