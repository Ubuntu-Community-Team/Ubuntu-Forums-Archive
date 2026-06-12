---
title: "What partitions to safely delete for dual boot?"
date: 2016-08-05
forum: Ubuntu/Debian BASED
---

### Post by waxcan on 2016-08-05
Hi guys,

I'm going to install Ubuntu or Kali Linux dual booted with Windows 10, and a say 400gb partition for music and Windows and Linux to access.

But I have a lot of partitions. Windows 10 is the only OS running and I can erase it if need, I'm backed up.

I have Dell OEM Windows 10 recovery USB. 

So do you know what partitions I can delete? 

I shrunk Windows 10 by 50gb for Kali, but was unsure how much space it requires. Might need to save pcaps, dictionaries etc.

The partitions seen on Windows disk manager

[IMG]http://i.imgur.com/B65wMj5.jpg[/IMG]

I have my external hdd attached. 

I was advised by one guy to:

Shrink Windows partition by 50gb
Create partitions:
Boot
  Kali Linux 
  SWAP
Music plus ( /home and Windows /users)
 Windows (pre existing)
Recovery


Thanks!!!

---

### Post by Bucky Ball on 2016-08-05
Unplug the external drive and post another screen shot (attach it by using Go Advanced or Advanced Reply and using the paperclip icon, please). Even better, boot from the Ubuntu install media, Try Ubuntu, get to a desktop, open Gparted and post the screenshot from that. Much more detail, although again, not sure how we'd know what to delete as that won't tell us what's on there either but at least we would be able to identify partition for discussion.

It is hard to know what you should delete when we have no idea what is on your partitions! I would have thought this is a question only you could answer. :-k

I can say this: If you are intending to have a 400Gb data partition your Ubuntu partition need only be 20-25Gb. /swap only needs to be 2Gb. 

You also have this:

Music plus ( /home and Windows /users)

Just to clarify: the Ubuntu /home partition is a dedicated, EXT* partition. Windows can't read it. Another way of going about this is to use an NTFS data partition which both can read/write. Leave /home as a directory inside your root partition (/) and create symlinks there to directories on the /data partition. 

If you give a partition the mount point /home during install it needs to be an EXT* filesystem which Windows can't use. You will not be creating Windows /users there either (although not sure what that is, sorry). A partition with the mountpoint /home will be used exclusively by Linux as a /home partition (where you user settings and default user folders are created by default). 

So, how you decide to go about this will dictate what you delete/create. If you want to keep Windows, simple way is delete everything but the Windows partition and install Ubuntu. If you already have an NTFS data partition, keep that, too and simply symlink Ubuntu to directories on it. 

Finally, are you installing Ubuntu or Kali? The specialised support areas here are not for Kali support as it is not a member of the official Ubuntu family. We have a section in 'Other OS' for it from memory (or the Ubuntu/Debian based forum?).

---

### Post by howefield on 2016-08-05
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

