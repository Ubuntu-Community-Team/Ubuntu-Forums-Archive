---
title: "How can I create multiple partitions on a mdadm array"
date: 2015-03-10
forum: Server Platforms
---

### Post by ltburch2000 on 2015-03-10
I have an existing mdadm 3 disk raid 5 array and I want to be able to split it into two partitions.  Unfortuntely I can't seem to figure out how to do it or if it is possible.

I resized the partition and now I have about a 1TB of contiguous space at the end of the array but gparted does not seem to allow me to create a new partition there.

Is there some trick to this?

If for whatever reason I can't partition the array is there a way to simulate that some how?  I need to have the appearance of a device with about 1TB of storage (to enable auto-expiration of items on the disk) I can't just create a folder in the large array because mythtv storage groups only support the idea of "minimum of xGB free" and not "maximum size of xGB".  If I can't limit it, it could grow and try and gobble up the whole array.

---

### Post by ltburch2000 on 2015-03-10
I was looking for an alternate solution and I came across one way to do it that simulates a partition.  It is a tiny bit kludgey but given that it is on a fault tolerant array it might not be so bad.  Use a virtual file system created as a very large file on the array.  Then mount that file system in the appropriate location and you will have a file system availible that will be of the fixed size of the created virtual file system.  Here is a tutorial, they talk about implementing quotas but that is not relevant to my needs.

[http://souptonuts.sourceforge.net/quota_tutorial.html](http://souptonuts.sourceforge.net/quota_tutorial.html)

---

### Post by darkod on 2015-03-11
As far as I know a md device is not designed to be partitioned. The idea is to create the md devices with the size you want and use them in a way you would use partitions.
So, you can destroy the big array moving the data to a temp location first, and create two smaller partitions on the disks and then two smaller arrays with them.
Another option is to use LVM on top of the big mdadm array which will give you flexibility for the LV sizes. But again the data needs to be temporarily moved because creating the lvm on your current array will destroy the data on it.

---

