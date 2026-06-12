---
title: "Space Problems"
date: 2007-08-10
forum: Server Platforms
---

### Post by TheSpecs on 2007-08-10
Hey.
 Right, i have a server in my cupboard running Ubuntu Feisty. Its has two HDDs, one 3GB one with the server OS on and one 40GB mounted at /data which holds websites and such.

I use it as a web server and have all the norm packages installed, apache2, php, mysql.... etc.

I finally got virtual hosts setup and working and then i decided to go and edit a file, which once i saved it emptyed the file instead :mad:

I thought this was weird, so i went on webmin and tried editing and saving the file and it said i that it ran out of diskspace. Went onto SSH terminal and used the df command to find that the 3GB HDD was full.

So ultimately my question is... can i move some of the big files of the OS to the other HDD or do you think i will just need to get a bigger HDD?

Thanks in advance! :)

---

### Post by aysiu on 2007-08-11
Ultimately, you'll need a bigger hard drive, but you can start by deleting the old installer files: ```
sudo apt-get clean
``` should free up some hard drive space.

---

### Post by koenn on 2007-08-11
you can move directories such as /var, /tmp, /home, /root ... or even subdirectories to the larger disk. Make sure to preserve permissions (or chmod them correctly afterwards). Then, modify /etc/fstab to reflect the changes, and run
```
mount -a
```

to 'move' directories, it's probably best to copy them, se if you can mount them, and delete the originals only if everything went as planned.

---

