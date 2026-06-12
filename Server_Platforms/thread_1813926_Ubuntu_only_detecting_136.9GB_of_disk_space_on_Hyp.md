---
title: "Ubuntu only detecting 136.9GB of disk space on Hyper-V"
date: 2011-07-28
forum: Server Platforms
---

### Post by Madman6510 on 2011-07-28
We're trying to install Ubuntu Server 11.04 on Hyper-V so we can run FOG and image computers that way.

When it comes to partition/format the drive, Ubuntu is only detecting 136.9GB of disk space, even though I allocated 500GB for it to be able to use. I made the disk static, not dynamically expanding.

The Hyper-V host is running Windows Server 2008 R2 Datacenter.

I was going to use Virtualbox on that server since it plays nicer with Linux, but we already have Hyper-V established and you can't do both.

---

### Post by Drewlander42 on 2011-09-16
> **Madman6510 said:**
> We're trying to install Ubuntu Server 11.04 on Hyper-V so we can run FOG and image computers that way.
 
When it comes to partition/format the drive, Ubuntu is only detecting 136.9GB of disk space, even though I allocated 500GB for it to be able to use. I made the disk static, not dynamically expanding.
 
The Hyper-V host is running Windows Server 2008 R2 Datacenter.
 
I was going to use Virtualbox on that server since it plays nicer with Linux, but we already have Hyper-V established and you can't do both.
 
 
Did you ever figure out the issue?  I am having the exact same problem.

---

### Post by horonym on 2012-02-01
Same problem...did you figure it out?

---

### Post by daxx on 2012-03-23
Same here , please help. :confused:

---

### Post by Grenage on 2012-03-23
I believe there is a Hyber-V bug with LBA48 support; which is why it seems to cut out at that magic number.

---

