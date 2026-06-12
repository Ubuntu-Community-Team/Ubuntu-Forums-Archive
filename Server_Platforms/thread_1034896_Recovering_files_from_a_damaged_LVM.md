---
title: "Recovering files from a damaged LVM?"
date: 2009-01-09
forum: Server Platforms
---

### Post by patlabor on 2009-01-09
Hello everyone,

i have a big problem. i set up an ubuntu server 8.10 with lvm devaults during install. everything was fine till i had the stupid idea to add another harddrive to the root lv. and after about 1 week the second disk had what appeared to be a headcrash.
now when i boot the box i get complains about a corrupted filesystem and fsck is runned exiting with a error 4 telling me that i need to run fsck manually. when i do that the first hd is working compleatly trou but as soon as the second one starts i hear funny noises and i get lots of scrollin text about media error, short read and whatever.

when i take the second drive out and boot without it i get complains that the system can not be loaded cuz the drive with the id this and that is missing.

stupid as i am i also dont have a backup of the data.

i guess the 30gb on the second hd are toast, but is there a way to at least recover the data on the first drive?

thanks in advance.

---

### Post by matpol on 2009-01-09
Maybe this will help:
[http://www.chickenskinners.com/2007/08/28/bad-superblock/](http://www.chickenskinners.com/2007/08/28/bad-superblock/)

---

