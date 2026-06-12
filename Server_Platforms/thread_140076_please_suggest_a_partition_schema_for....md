---
title: "please suggest a partition schema for..."
date: 2006-03-05
forum: Server Platforms
---

### Post by vincent orange on 2006-03-05
Hello everyone,

I'm a new convert to kubuntu and I'm liking everything so far. 

At present I'm setting up a multiple user, web, mail, ftp, DNS and general file server and I would like some pointers on how to partition the drives so that I can **swap out the user data and OS** as necessary for backups and etc.

I have 5 hard drives and I'm thinking of using the following partitions

1 X 40Gb
   swap  1.5Gb
   /        
   /tmp   2Gb
   /boot   50mb
   /usr     5Gb


2 X 80Gb (RAID 1)
   /var

1 X 160Gb
   /ftp

1 X 400Gb
   /home


Am I missing any other partitions for what I want? 

I will be using Quota, so all the users have about 5Gb in their home directory. My question is when they ftp to the server and transfer files will it go to the /home/user directory or where the ftp server is installed. I ask this as my other web servers always used a single drive so I'm not sure.

Thanks for your input, it's much appreciated
Vincent Orange
:)

---

