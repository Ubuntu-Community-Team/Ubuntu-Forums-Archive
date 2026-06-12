---
title: "Converting form U Server to UEC - Storage questions"
date: 2011-04-30
forum: Ubuntu Cloud and Juju
---

### Post by sasampson on 2011-04-30
Hello:

I'm running a 10.04 server with and 8TB RAID-5 array attached to it.  I'm looking into changing that into a CLC, CC, SC WS3 server and using another few systems as nodes.  One thing I really don't understand, and I've read a bit of the documentation, is how storage is handled in the UEC environment.  Most of the documentation seems to assume one has a really good working knowledge of AWS WS3/SC equivalents and how they are architected and managed, which I don't.

Does my existing array end up turning into a bunch of disks (/dev/sda, /dev/sdb, etc.) that the SC allocates based on configured demand?   Can I configure RAID storage and make that available to the SC?

Is there any detailed documentation that explains what is happening at the OS/hardware level once you have installed UEC?  How do I, or do I, control how physical storage is managed?  Or, how do I add and configure new (physical) storage and make it available to the SC?

As you can tell, I'm a bit confused.  It could be I'm missing something really obvious here.  Any guidance would be much appreciated.

Thanks!

---

### Post by kim0 on 2011-05-03
UEC offers two storage types
- Walrus (like S3) this is simply a key-value store. You store a file, get back a key. You use that key to get back the file again! It is not a disk, not a block device. You probably don't want this :)

- Volume (like EBS) this is a remote iscsi or aoe volume that gets plugged into your VM and appears as a disk (/dev/xdh) for example. You format and mount this as a normal disk

You can google for S3 vs EBS, should find tons of info

---

