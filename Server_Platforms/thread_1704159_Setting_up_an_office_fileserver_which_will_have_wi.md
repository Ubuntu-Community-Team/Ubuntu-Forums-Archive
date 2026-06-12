---
title: "Setting up an office fileserver which will have windows clients"
date: 2011-03-10
forum: Server Platforms
---

### Post by gunnarflax on 2011-03-10
Hi! I'm thinking of setting up an Ubuntu 10.10 server but I have some questions I want answered before I proceed.

If I have SAMBA shares to the different clients, will there be any benefit in transfer rates depending on which filesystem I use? I mean, if the client have NTFS filesystem, will it be better to use NTFS or ext4 on the network share? Does it make any difference?

Also I was wondering if I host an application on the Ubuntu server which is for windows but requires no install, meaning that the files are just located there. Will I still be able to launch the application from the Windows client or will there be any incompatibility?

Thanks!

---

### Post by never say never on 2011-03-10
What kind of connectivity are you talking about here?  For instance if your client(s) connect at 10/100 the bottle neck is the network and not any file system.

What kind of data are we talking about here?  Are we talking about video files or word documents?  The type of file system could have an impact here as well.  

What kind of file system is on the network drive will make no difference to the client system. I would not use NTFS on a Linux box, unless it was a dual boot system and I wanted the drive accessible to both Windows and Linux.

The only real problem hosting an app on a file server (Windows or linux) is that you may run into file locking issues, where only one user can run the app at a time due to file locking.  This largely depends on how the software was written.

---

### Post by gunnarflax on 2011-03-10
The filetypes will mainly be documents of different sorts. No media or larger filetypes. I thought the real benefit of having the application on the server instead of the client is the need of only one license for the program, instead of having a license for each of the connected clients, am I right on this? But the problem with file locking is only when the clients are editing the same file right? so as long as they use the same app but edit different files there will be no harm done?

---

### Post by area124 on 2011-03-10
Someone can correct me, but I think if you are using SAMBA the underlying file system may not matter too much. I thing you may want to use the best file system for the OS you are using on the server. 

As far as hosting an application remotely on the file server, again, SAMBA will take care of getting the data across the network to the client. So  you should be OK there as well.

---

### Post by mciverza on 2011-03-10
> **gunnarflax said:**
> ...I thought the real benefit of having the application on the server instead of the client is the need of only one license for the program, instead of having a license for each of the connected clients, am I right on this? ...

I think you are probably incorrect. A licence is usually needed for wherever an application is executed/run. Even though the application's files might be on a network drive, when the the application is run, it executes on the client PC, using the client CPU and memory, not the samba server's memory. The fileserver is just providing an additional (network) drive to each PC client.

---

### Post by gunnarflax on 2011-03-10
> **area124 said:**
> Someone can correct me, but I think if you are using SAMBA the underlying file system may not matter too much. I thing you may want to use the best file system for the OS you are using on the server. 

As far as hosting an application remotely on the file server, again, SAMBA will take care of getting the data across the network to the client. So  you should be OK there as well.

Ok, good to know, this his been something I've been wondering about for a while now :)

> **mciverza said:**
> I think you are probably incorrect. A licence is usually needed for wherever an application is executed/run. Even though the application's files might be on a network drive, when the the application is run, it executes on the client PC, using the client CPU and memory, not the samba server's memory. The fileserver is just providing an additional (network) drive to each PC client.

All right, that sounds logical. I will give this server setup a shot I think (without the app on the server). There is no harm done in learning at least :) Thanks for the replies!

---

### Post by Jack Brown on 2011-03-31
hey gunnarflax,

follow-up question:

were you able to implement this?  you just samba shared everything to the windows clients?  things going well?

---

