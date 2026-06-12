---
title: "System became slow after add too many files to disk"
date: 2009-09-18
forum: Server Platforms
---

### Post by diddyrock on 2009-09-18
Hi

My ubuntu 8.04 system became extreme slow after I put about 10,0000 files in the file system.All the programs became very slow. but after I increase the file number to 1 million, the system didnot became slower than the 10,0000 files condition.  I have tried to decrease the file number to 50000, and the system became fast again, 

could you please tell me why does that happen?
Is there any work aroud this case?
need I change some settings in the system?

Thanks!

---

### Post by hessiess on 2009-09-18
The more files there are in the filesystem, the more the OS has to sift through to access spasific files, which would slow things down. Try breaking the filesystem across several partitions.

---

### Post by openfly on 2009-09-18
Well more files in a path means the more data needs to be parsed by any application walking that path.

Also you'll want to be careful you don't run into any ulimit issues in working with that many files.

---

