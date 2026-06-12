---
title: "Detect a virtual drive space change"
date: 2009-04-16
forum: Server Platforms
---

### Post by lelizondob on 2009-04-16
Hi, I'm running Ubuntu Server 8.10 in top of VMWare. I set up a 10GB hard drive, two partitions were created during install, the filesystem (8GB) and swap (2GB). Now I want to increase the virtual drive to 30GB, that's not a problem with VMWare, the problem is Ubuntu, because it's not detecting the size change. It says 8GB and 2GB.

How do I make ubuntu aware of this change?

I'm not running X so commands are better. I don't want to change the size of swap partition, only / 

Finally, I have everything on /, including home. 

Thanks in advance.

---

### Post by Thirtysixway on 2009-04-16
You're going to have to edit the partiton and resize it to use up your new free space.  It's like taking a cardboard box out of 1 room, and putting it into a bigger room: the cardboard box stays the same size.  So increase the size of the box :p

Idk if you have access to your server with a monitor, but using something like GParted Live is a very easy way to edit the partitons.  It's what I use to manage partitions.

---

### Post by lelizondob on 2009-04-16
I'm using [Partition Manager]("http://sourceforge.net/project/showfiles.php?group_id=198821"). It's great because I don't have to install gnome/xfce to use it, I just boot my server and start the partition manager.

Finally I just dumped my hard drive and created 3 virtual hd, one for the filesystem and swap, another one to mount /home and another one to mount /usr

I think (correct me if I'm wrong) in the next years those directories are the only ones that could grow out of control. With 10GB I think it's enought for the filesystem when home and usr are on a different partition.

Finally, with Partition Manager, I can resize the home and usr partition in less than 30 minutes so my server won't be down for too much of time.

---

