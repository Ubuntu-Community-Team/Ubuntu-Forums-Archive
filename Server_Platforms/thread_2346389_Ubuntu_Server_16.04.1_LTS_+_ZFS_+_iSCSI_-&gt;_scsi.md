---
title: "Ubuntu Server 16.04.1 LTS + ZFS + iSCSI -&gt; scsi unmap?"
date: 2016-12-14
forum: Server Platforms
---

### Post by xemius on 2016-12-14
Hi all!
I new to Ubuntu and the ubuntu forums.

Recently i've started testing ZFS on Ubuntu 16.04.1 LTS, everything is working great but... there is just this one thing :D

When i've created a zpool and a zvol, attach this to an iSCSI target (tgt) and then initiate it on a Windows Server 2012 R2 create an NTFS filesystem on it everything is still ok.
When I delete files on this NTFS filesystem and I look at ZFS on ubuntu the space is not reclaimed.

I've been reading upon the internet about scsi unmap, so I was looking at TGT and saw that this has a thin_provisioning=1 option, did that, not working.
Also as I should believe from reading Server 2012 R2 is able to do scsi unmap.

Are there people here on the forum that are having or had the same experience?

I currently work around this problem by using sdelete on the W2K12R2 os, but getting scsi unmap to work would be so much nicer :)


Greetings,
xemius

---

### Post by xemius on 2016-12-14
Solved my problem by replacing tgt with scst, everything is working like a charm now!

Greetings,
xemius

---

