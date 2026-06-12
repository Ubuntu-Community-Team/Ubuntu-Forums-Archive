---
title: "Migrating users to new Samba PDC"
date: 2011-04-07
forum: Server Platforms
---

### Post by collisionystm on 2011-04-07
Hello everyone.

Before I ask any questions I will explain the situation I have.
I just recently came on board with a company that is running a samba PDC on Ubuntu Server 9.10. I have used Ubuntu for quite a while but this is the first samba server  I have ever dealt with. I am learning alot about it and I think I have a good bit figured out.
The server is a Dual Core with a 600 GB hard drive that is almost completely full. I am very uncomfortable with the box because it is getting old. 
I have built a NEW Samba Server on a seperate hardware platform that has RAID10 with hot swappable drives and Ubuntu Server 10.10.

I have built Samba, installed bind9, setup my shares and I am ready to port users over. The old server is NOT using roaming profiles due to space, however I would like to implement  this function due to the fact that I now have 4 TB of drive space for users.

I have already ported over usernames, passwords, shared folders and permissions. 

the question is....

Does anyone know of the best way to port these users files over to the new roaming profiles on the new server? Unfortunately that are not intelligent enough to backup their own files and I am stuck moving them over manually. There are 60 users.

Any ideas how I can best accomplish this task?

---

