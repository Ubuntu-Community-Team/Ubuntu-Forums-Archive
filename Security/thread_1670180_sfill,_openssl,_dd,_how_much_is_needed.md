---
title: "sfill, openssl, dd, how much is needed?"
date: 2011-01-18
forum: Security
---

### Post by maxim99 on 2011-01-18
I don't really know a whole lot about encryption, or securely erasing data. I'm curious how much is really needed before I feel comfortable since I can't actually see what's going on, or do any trials to see if the data is recoverable.

I'm interested in wiping free space in a file system. I've found a couple of methods available which will write data to the drive. One is the sfill application in the secure-delete package available through apt-get. The other is using openssl to write data to a file, effectively filling the free space.

Here are examples of usage that i'm interested in:
```
sfill -llfv /home/maxim
```
```
dd if=/dev/random bs=1k count=1 | openssl enc -kfile /dev/fd/0 -in /dev/zero -aes-128-cbc > /home/maxim/file
```
My home directory is on a separate partition from the rest of the file system.

Using sfill with default options is very slow and would take a very long time to write to all of the free space, something probably around 150+ hours. I need to be able to use the system and there needs to be free space available. For a process taking so long it would not be reliable during that time in addition drive and processor activity would hinder performance.

What I'm looking to do is run a cronjob (on a daily or weekly basis) which will work the free space on the partition while the system is not in use. I'm looking to find a balance between the number, or degree of wiping and the frequency of the wipes. I think that if I can find something that finishes in a few hours and run that process frequently then I'll be relatively secure compared to running the process once every so often.

---

### Post by tubezninja on 2011-01-18
Just throwing this out here, but you could do away with all of this complexity but just using a tool like [dban]("http://www.dban.org/").  It does a fine job of wiping any drive your computer will recognize.  Just sayin'.

---

### Post by maxim99 on 2011-01-18
The drive in question has a partition mounted in the live file system. Both methods listed above are examples of wiping free space on a partition.

---

