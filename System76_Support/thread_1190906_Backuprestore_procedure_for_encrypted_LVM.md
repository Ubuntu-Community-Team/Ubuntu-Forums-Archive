---
title: "Backup/restore procedure for encrypted LVM?"
date: 2009-06-18
forum: System76 Support
---

### Post by phyzome on 2009-06-18
I will be leaving the US for a research trip later this week, and I had hoped to move my system into an encrypted LVM for security at the border crossing. (Some border security agents have taken it upon themselves to act as digital police, demanding passwords, invasively searching for files, and confiscating computers if travelers do not comply.)

Yesterday I backed up my machine and used the Intrepid 64-bit alternate installer disk to lay down an encrypted LVM, then booted to Jaunty Live CD to restore my system into the encrypted space.

However, I discovered that the Live CD does not carry tools with which to manipulate LVMs, let alone encrypted ones! Furthermore, after installing those tools from the internet, I was not able to restore from backup, since it was not clear how to set up separate home and OS partitions. In the end, I was forced to wipe the drive and blast my 100+ GiBs back onto the disk, which took the entire evening.

So, here are my questions:
[LIST]
[*]How do I move my existing OS and /home into an encrypted LVM, with the same partitioning setup? (A.k.a., perform a restore.)
[*]How do I backup such a system while it is not running?
[/LIST]

---

