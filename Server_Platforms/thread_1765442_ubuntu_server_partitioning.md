---
title: "ubuntu server partitioning"
date: 2011-05-23
forum: Server Platforms
---

### Post by ibrahim.k on 2011-05-23
Hi,

I want to install ubuntu server 10.4.2 lts on my server but I am not sure about what is the best way for partitioning, I have two hard discs and each one is 1tb.
It will be used as a mail server, Zimbra opensource email server.



Thnx in advance,

---

### Post by Grenage on 2011-05-23
If you're installing it *on* a server and yo have RAID1 support, then it's not a bad idea to mirror the drives.

As for the partitions, the default isn't 'bad'; I'd actually recommend it if you're unsure of what you want.  Personally, I might want a separate home, var and tmp directory - it depends what I'm running.  It's not going to cripple you, however you go.

---

### Post by Lars Noodén on 2011-05-23
> **ibrahim.k said:**
> ... I am not sure about what is the best way for partitioning, I have two hard discs and each one is 1tb...

The "right" partitioning scheme depends on how you will use the computer.  Tell us a little more on your plans for the machine.

---

### Post by ibrahim.k on 2011-05-23
It will be used as a mail server, Zimbra opensource email server.

---

### Post by spynappels on 2011-05-23
You need to consider if you will need more than 1TB storage in the lifetime of the server, if not, the simplest option is to mirror the disks using RAID1 as Grenage said and then install the OS on top of the RAID array. Using the defaults is normally fine.

If you think that you will need more than 1TB storage over the lifetime of the server, you need to work out where most of the data will live and place that folder on its own on one of the disks. For example, if Zimbra stores everything in a directory under /var you will want to install the OS on 1 disk, and mount the other as /var so that everything written to /var including its child folders is written to the other disk.

Remember to back up regularly as well, preferably to another server altogether using rsync.

---

