---
title: "Lost Space after Cloning (Samba, Windows XP)"
date: 2011-05-16
forum: Server Platforms
---

### Post by Doghnut on 2011-05-16
Apologies if this has already been posted; I've searched quite a bit and found nothing.

I recently installed Ubuntu Server 10.04.2 and configured it to be used as a network storage device. I installed it on an 80GB HDD initially. Everything was fine -- I could read and write to the drive and I could set permissions from my Windows XP machine.

I decided I wanted a bigger HDD. It had taken a few hours of configuration to get it to work the first time, so I didn't want to go through that again. I instead created a clone with Clonezilla and then slapped the image onto a 1.5TB drive. I then used gparted to resize the partitions.

Everything seems fine from the server side of things (I'm fairly new to it, so I could be missing something, but it all looks good). The server correctly sees that I am using 2-3GB of the 1.5TB drive. It sees the rest of the space as free and part of the primary partition.

Here comes the problem -- Windows isn't reading the drive space correctly. It sees that 80GB of the space is taken (the size of the original HDD) instead of 2-3GB. I'm not sure if it will actually let me write to the space or not. But whether the reading is simply cosmetic or if Windows really thinks it's taken, I would like to fix it either way.

Any ideas?

---

### Post by Doghnut on 2011-05-16
One more thing:

I don't have enough experience to know whether this is normal or not, but I thought it was worth mentioning.

When I login to the server, it gives me all of the current system information. All of that info is correct and normal. Then it gives me the system info again, but the second time, it has all of the old info in it (from before the cloning). 

The second one never changes. At first, I thought the server would give me the current info and then always follow with the newest old info. But instead the second info never changes.



"
  System information as of Mon May 16 14:13:25 EDT 2011

  System load:  0.11             Processes:           114
  Usage of /:   0.1% of 1.34TB   Users logged in:     0
  Memory usage: 4%               IP address for eth0: x
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Wed May 11 11:22:50 EDT 2011

  System load:  0.23              Processes:           105
  Usage of /:   1.3% of 70.71GB   Users logged in:     1
  Memory usage: 5%                IP address for eth0: x
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
"

---

### Post by Doghnut on 2011-05-16
Nevermind to that last problem. I thought it might be related, but I just found the fix for it and it had no effect on my original problem.

---

### Post by Doghnut on 2011-05-17
Just wanted to bump this in case someone has any ideas.

---

