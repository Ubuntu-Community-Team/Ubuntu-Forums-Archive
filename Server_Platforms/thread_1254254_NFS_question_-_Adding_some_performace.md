---
title: "NFS question - Adding some performace ?"
date: 2009-08-31
forum: Server Platforms
---

### Post by zeevikn on 2009-08-31
I'm running an NFS server, and would like to boost a little its performance.

The main performace issue looks like loading new files to memory.
for example, I have an FTP server, which using the NFS server as main storage.
First download of a 58MB file can take minutes, @ 300-500KB/sec
Second and later downloads takes seconds at 10MB/sec.

any ideas ?
What does RPCNFSDCOUNT mean (/etc/default/nfs-kernel-server) ? i.e. what would be the affect of increasing or decreasing this value ? (currently, set to 8)

Thanks,
Zeevik.

---

### Post by samosamo on 2009-08-31
[http://blogs.techrepublic.com.com/opensource/?p=64](http://blogs.techrepublic.com.com/opensource/?p=64)

Cliffnotes: Mount the NFS share with these options: rsize=32768,wsize=32768,intr,noatime

---

