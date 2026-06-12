---
title: "KVM OpenSolaris guest with physical disks."
date: 2008-12-31
forum: Virtualisation
---

### Post by eldaria on 2008-12-31
I wanted to install OpenSolaris as a guest OS in KVM on Ubuntu 8.10 Server.
My server has 4 Harddrives, 1 160GB and 3x 250GB, I want to use OpenSolaris to be the file server to get access to the advantages of ZFS and use the 3 Harddrives for this.

Anyone tried this, and how did you do it?

Regards,
Brian Levinsen

---

### Post by faviann on 2009-09-30
I'm curious since I'm looking for this exact same setup but I can't seem to find any info on that.

So I'm wondering:
[LIST=1]
[*]Have you tried it?
[*]Is it stable?
[*]What are the specs I should be looking for if I want it to to be close to a small dedicated setup (performance-wise)? I've read the guest OS will need at least 2GiB of RAM for good ZFS performance.
[*]What will be the performance out of my storage pool? 
[/LIST]

I really hope this setup works. Instead of having multiple dedicated boxes I could run my NAS along with my LAMP setup on the same server. :D

Thanks
Faviann

---

### Post by eldaria on 2009-10-01
I never got around to implement it.
The reason beeing that probably the overhead would be to high.

Right now I'm just running Linux with Ext4 instead, I might revisit the idea at a later point, or go all out and run Solaris on the server, and then run Linux virtualized for the things that need Linux.
I just don't like Solaris, I much more like to work with Ubuntu.

Another thing one could hope for is that Oracle will change the license for ZFS now they bought SUN, but I guess that is wishful thinking.

---

### Post by faviann on 2009-10-02
I agree on the wishful thinking part.... especially since Oracle is behind btrfs. Here's a really nice article of why btrfs looks like it'll have an even brighter future thank ZFS: [http://lwn.net/Articles/342892/]("http://lwn.net/Articles/342892/")

About the file server setup, in my case, I'm probably gonna run solaris directly on the hardware.

After reading [this]("http://www.opensolaris.org/jive/thread.jspa?threadID=108213&tstart=0"), I've convinced myself to forget about the idea of virtualizing Solaris/ZFS. 
Plus I found lots of very interesting sites explaining in details how to install ZFS+Solaris as a home NAS.

I just need some more cash to buy the disk required since you currently can't grow a pool with ZFS.:(

I'd rather have it right the first time. :)

---

