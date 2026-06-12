---
title: "Downsizing a VMware disk"
date: 2008-03-31
forum: Server Platforms
---

### Post by Mackan2 on 2008-03-31
I have a VMware image that I am going to duplicate a few times to run in parallel for some tests. The vmdk-file is 2,6GB, but the file system is not that big. Is there a way to make the file smaller, like the size of the file system on it. 
I hope some of you understand what I'm trying to say...

---

### Post by dmizer on 2008-03-31
that sounds tiny if you're really running a vm with less than a 3 gig vmdk.  if you shrink the disk down to the size of the file system, your vm will not boot.  it needs space to write and rotate log files.  if you think you have enough room, and still want to shrink your drive, take a look here: [http://communities.vmware.com/thread/118010](http://communities.vmware.com/thread/118010)

---

