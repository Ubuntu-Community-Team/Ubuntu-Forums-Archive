---
title: "root file system errors but clean from outside"
date: 2008-03-17
forum: Server Platforms
---

### Post by raik on 2008-03-17
Hi,

I am running a Ubuntu 7.04 server within VMWare and fsck.ext3 reports file system errors. I don't want to repair the mounted partition so I booted the virtual machine from an Ubuntu desktop CD, mounted the partition and run fsck on it (side question: is there a better way of doing this?). 

The funny thing is that this external fsck didn't find any errors. When I boot again from the root partition it still has errors::

brickitserver|~> sudo fsck.ext3 -nf /dev/sda1
e2fsck 1.40-WIP (14-Nov-2006)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (1759390, counted=1759370).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********


So what's going on here? From outside the partition looks ok, from inside it doesn't. 
Any idea anyone?

Thanks in advance
Raik

---

