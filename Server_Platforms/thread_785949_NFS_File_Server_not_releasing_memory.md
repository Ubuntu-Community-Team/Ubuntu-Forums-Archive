---
title: "NFS File Server not releasing memory"
date: 2008-05-07
forum: Server Platforms
---

### Post by s3fddiz on 2008-05-07
When copying files from my Ubuntu server, it is not releasing the memory.  I use 'free -m' and watch the memory grow during the file transfer.  Once the transfer is complete, the memory does not drop back down.  

Eventually, all of the system memory is consumed.  How do I get it to drop the memory after a file transfer?

---

### Post by s3fddiz on 2008-05-08
Bump, anyone have an idea as to why this is happening?

---

### Post by subliminalcecil on 2008-08-15
I have installed ubuntu server 8.04 as well and tried NFS sharing rather then samba. Im getting this exact problem with the RAM as well. I watch files using VLC accessing the NFS share, the RAM is fully occupied (2gb) after watching a few files (totalling the 2gb).

I have done a bit of googling but found nothing, did you ever get a result?

---

### Post by windependence on 2008-08-15
This is normal Linux memory management. Unlike Windows, Linux will use the entire physical memory available to it. Once memory is full, Linux will swap out files in memory as needed. This is a much more efficient model and results in less disk activity.

-Tim

---

### Post by subliminalcecil on 2008-08-15
Will NFS ever release the memory after a set period of in activity? or just keep filling the swap?

Does this effect the performance of anything else? not that i have much else activity on the server.


Thanks for your time! much appreciated.

---

### Post by windependence on 2008-08-15
No, it will stay cached unitl more memory is needed for another application. It doesn't take any resources to keep it there. Once the data is stored in the registers, it just sits there, and if it is needed, it does  not have to be pulled from the disk, that's a good thing. :)

-Tim

---

