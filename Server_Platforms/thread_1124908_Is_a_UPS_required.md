---
title: "Is a UPS required?"
date: 2009-04-13
forum: Server Platforms
---

### Post by leonv12 on 2009-04-13
I am running ubuntu server to backup windows boxes (with rsync).  In the old UNIX days, file system corruption could occur if a shutdown occurred due to power loss.  Is a UPS (with software shutdown) required to avoid this problem with ubuntu server?

Thanks,
Leon

---

### Post by mrsteveman1 on 2009-04-13
UPS is a good idea, but technically a journaled filesystem should prevent corruption from an unclean shutdown. However, i don't trust that, so i don't let the systems i manage power off unexpectedly.

They are cheap though, and most of them provide surge protection and line conditioning as well, to prevent under and overvoltage problems.

---

### Post by jms1989 on 2009-04-13
I don't think so, I have a server setup without a UPS and it works fine. Just be sure to use a ext3 filesystem or any filesystem that supports a file journal. Consult wikipedia on the current filesystems.

A filesystem with journaling enabled, ie. ext3, will reduce the risk of file corruption as long as no files are being written to during a power loss. Otherwise, file corruption is possible if the connection to the source of the file download to the server is lost. If its just running and you encounter a power loss, it will just run its fsck program to repair any errors in the filesystem.

To answer the question, yes and no. It really depends if you need it online all the time but it couldn't hurt to add one. :)

---

### Post by BkkBonanza on 2009-04-14
A UPS is always nice for a server but it depends on how sensitive you are to spending a little money and how critical your data is. I would say that for a backup server where you are always dealing with second copies of data it's likely not so critical. But as others say here, you can't go wrong by having one and it may reduce some headaches later. It's another level of safety.

---

### Post by leonv12 on 2009-04-15
Thanks for the feedback!  The critical feedback seems to be - if a file is being written when a power loss hits, corruption could occur.  That's a risk I can't take, so I'll continue to use a UPS.

Thanks again,
Leon

---

