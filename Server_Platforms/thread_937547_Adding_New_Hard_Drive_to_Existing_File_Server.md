---
title: "Adding New Hard Drive to Existing File Server"
date: 2008-10-04
forum: Server Platforms
---

### Post by cantdrive55 on 2008-10-04
I've currently got a home file server running that is using a single 320GB Seagate but I have run out of space and will be getting a new terabyte seagate in the next few weeks. I have Ubuntu 8.04.1 server edition and have the files in ```
/home/jclif/FileServer/
``` then within that main section I have
```
/Music/
/Movies/
/School/
/Shared/
/Pictures/
```
What I want to do is make it so the new drive is open for ```
/Movies/
/Shared/
``` as those are the biggest ones.

Is there a way for me to make the system see it all as one big drive? Or am I better off just re-installing everything onto the terabyte drive?

---

### Post by tigerstripedcat on 2008-10-04
The great thing about linux filesystem is that it doesn't use "drives" but "mount points".  You have a few options aside from the one you listed.  You can:

1) 
Partition the new drive such that you have two partitions that you can put in /etc/fstab as TWO SEPERATE mountpoints to:
/Movies/
/Shared/


2)Just make some directory somewhere called /storage or ~/storage which will be the mount point for the new drive and create symbolic links of these two directories to the new drive.

There's probably other options, but these two come to mind.

---

