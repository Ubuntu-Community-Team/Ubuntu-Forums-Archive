---
title: "Best way for multiple server replication"
date: 2009-02-12
forum: Server Platforms
---

### Post by fang0654 on 2009-02-12
I have 4 file servers spread across the US.  One of these servers has a 10 Mb connection, the other 3 just have 1.5Mb T-1s.  I want to synchronize all 4 servers nightly.  At first I was looking at using Unison, and synchronizing in a star topology, with the 10Mbit server in the middle.  The only problem with this, is that I can only synchronize two servers at a time, at a max of 1.5Mbit.  

Ideally, I would like to be able to get a list of changes from all servers concurrently, synchronize all new files back to the main server, and then replicate those changes back out to all the other servers at the same time.  Does anyone know of any way this is possible?

Any help is much appreciated.

---

### Post by faustcoder on 2009-02-12
You can do DRBD if I recall correctly. Possibly RSYNC cause it handles bandwidth well. Maybe even a clustered file system like cxfs? Hope this helps and if you succeed please let me know your solution!

---

### Post by fang0654 on 2009-02-12
I can't use DRBD or cxfs because they synchronize the data real time.  A lot of the files are audio, so they can get kind of large, and would slow the fileservers down to a crawl waiting to copy.  I'm going to look more into rsync, maybe I can script it in such a way as to do what I want.  Thanks.

---

