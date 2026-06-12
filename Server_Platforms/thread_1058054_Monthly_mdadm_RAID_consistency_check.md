---
title: "Monthly mdadm RAID consistency check"
date: 2009-02-02
forum: Server Platforms
---

### Post by iang on 2009-02-02
Hello everyone,

I have a new file server that is connected to another server (via NFS) that acts as a F/OSS mirror. It is a quite busy server I'd say. In that file server, I have a RAID5 with mdadm configured for 8x1TB harddisks setup. This is my first experience managing server with a RAID, so I still don't know much about maintaining it.

Last week, I found out that the "front end" server couldn't response to my request and after I checked it, it seemed that the NFS was not responding. I accessed the file server and I found out that there was a routine mdadm consistency check that probably the source of problem.

So, my question is.. do I really need to do that monthly routine check? Perhaps it is good to avoid data corruption but the "drawback" is probably too much for me who want my server can always response to the incoming requests. Checking 8x1TB harddisk takes hours!

Since the server and the disks are new (around 1 month), is it still ok to make this regular check for every, let say, 3 or 4 months?

and just to add some informations, the typical disk access in the file server is reading. On average, around 300-500 users connect to the server concurrently and constantly download around 30-50 Mbps all the time. The write access probably only at night when the server runs many rsync instances to resynchronize the mirror.

do you have any suggestions?

thanks!

---

