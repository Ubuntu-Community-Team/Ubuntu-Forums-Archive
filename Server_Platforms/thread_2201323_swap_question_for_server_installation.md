---
title: "swap question for server installation"
date: 2014-01-23
forum: Server Platforms
---

### Post by MakOwner on 2014-01-23
I have been runnning an Ubunut 12.04 LTS installation for some time now as an NFS server for 16 ~ 24 TB of ext4 filespace.
I have never seen this server use any of the swap space, as reported by 'free'.

Given that the load and memory allocation will not change on this server, would it be safe to reinstall and not allocate a swap partition?

---

### Post by Bashing-om on 2014-01-23
MakOwner; Hi !

Swap is dependent on how much ram is onboard. When the system starts running short on ram, it starts using that swap space. With enough ram - in a server world where hibernation is not an issue - swap may not be needed, however consensus is to keep a "small" swap - just in case of never can tell what the demands on the server might happen to perchance.

[INDENT][INDENT]I heard it
[INDENT][INDENT][INDENT]through the grapevine
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-01-23
Swap is a safety precaution.  It gives you time to troubleshoot when your system slows down.  If you don't have swap and you have a runaway process that is gobbling up RAM, the kernel will unceremoniously start shutting down processes to recover RAM.  With swap, the system will slow down noticeably, your users will complain and you have time to see what is going on.

---

### Post by MakOwner on 2014-01-24
So, if I never see this thing hit swap, it would be just as safe to create a swap file instead of a swap partition for those just-in-case moments?

---

### Post by Bashing-om on 2014-01-24
MakOwner; Hey;

Nothing to say you can not try what ever arrangement that you want. One can always add that swap partition back in. But I say again, Having a swap partition, takes little disk space, is easy to maintain, and is good insurance for what might happen in the ram space.
The only time I have seen a forsaking of swap space is in a desk top environment where the ability to hibernate is not a consideration -   with greater than 8 gigs of ram.

[INDENT][INDENT]a lot to be said for 
[INDENT][INDENT][INDENT][INDENT]cheap insurance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

