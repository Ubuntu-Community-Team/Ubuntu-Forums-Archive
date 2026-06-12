---
title: "initial snapshot"
date: 2006-04-22
forum: Server Platforms
---

### Post by gymsmoke on 2006-04-22
I have Ubuntu server setup and installed, and I would like to create a bakcup of this before moving on and adding other components (just in case).  
What i'd like to do is:
create the entire disk as a file that i can download to my pc, and burn an iso image of it.

i read the man page for dd, which i believe makes an image copy of a file/dir , so
dd if=/dev/hda1 of=/dev/hda2 would work, but i only have 1 hard drive, so my guess here is that it would need to write to the cd-drive (exccept that the cd-drive on my co-lo box isn't a burner).

for the moment, would just making a tarball of the entire disk and then downloading that to my local pc be sufficient? (i'm looking into a net-vault account next week, but i am not of a mind to re-install Ubuntu server, apache, dns, bind, qmail/vpopmail, ftp, ssh, ssl/tls, etc... again if something really goes bork).

if there's another way - i'd be grateful for the input

---

### Post by nagilum on 2006-04-23
Creating a tarball is sufficient, except that you need to reinstall the boot loader after restoring the root-fs from the tarball.
dd also can save things to regular files, use 'dd if=/dev/hda1 of=./some_file' for example. The tar-method is probably better though, since dd creates a file of exactly the size of your partition, not matter how much space is actually used by files. So you can't actually save the image of hda1 to a file on hda1.

---

