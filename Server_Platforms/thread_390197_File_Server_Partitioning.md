---
title: "File Server Partitioning"
date: 2007-03-21
forum: Server Platforms
---

### Post by wayne on 2007-03-21
Suggestions needed,

I am building a file server for my home network and need some help on partitioning my drives.  I know these questions may seem simple to some, but I am a little confused on this topic.  I would like to set this server up for good performance and correct the first time around.

I have an 80GB IDE drive and a second 320GB SATA drive.  I was thinking of installing Ubuntu server 6.10 on the 80GB drive and using the big drive for data & music files.

I am not sure what partitions & size (like /, swp, var, home) to use for Ubuntu.  I will not be storing any files on the first drive. Should I use ext3 or rieserFS?  

Also, on the 320GB drive is it best to use ext3 or NTFS?  I will be using both Windows & Linux systems to connect to the server.

Thanks for any help in advance

---

### Post by stokedfish on 2007-03-21
I guess you will use samba anyway, so the filesystem doesn't really matter.

I recommend ext3 though.

---

### Post by j1mc on 2007-03-21
stokedfish, i am researching server partitioning for a home file server, too.  one helpful thing that i found is from the [debian security manual]("http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2").  it talks briefly about server partitioning, so you may want to check that out.

i'm not sure what size to make the /tmp and /var/tmp partitions, though.  (that's what i'm trying to find out).

someone else recommended samba, and i would recommend that, too.  linux does have the ability to read from ntfs partitions, but from what i understand, linux's ability to write to ntfs partitions is not always reliable.

i am setting up a samba server myself.  :-)

---

