---
title: "Drive designaion change"
date: 2009-01-13
forum: Server Platforms
---

### Post by DarwinLabs on 2009-01-13
I am having an issue with my ubuntu setup. I have an IDE drive that I'm using for the os and I have been adding sata hard drives every couple of pay checks or so. anyway I am wondering why is the identifier, the ide started off as sda then when I added a new drive to it the os drive which is the IDE drive changed to sdb and the sata went to sda. why is this happening from what I remember the letters shouldn't be changing. when I add another drive it changes yet again. can anyone be explain why?

---

### Post by cariboo on 2009-01-14
This is a commmon problem when you mix IDE and SATA drives. Use the drive's uuid to mount it in fstab eg:

```
#/dev/sdb1
UUID=0160b7ed-810e-45e9-9a23-2d54e36aeff3  /home/backups  ext3	  relatime	02
```

To find the uuid's of your drives at the prompt type:

```
blkid
```

the result should look something like this:

```
/dev/sda1: UUID="a386879b-3e2f-484b-ab40-3383cc8bffbe" TYPE="ext3" 
/dev/sda3: UUID="54e6cf1b-2578-43f0-89d6-cd8c8c4f672b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a2a43c18-fa1e-4faf-8cb5-dfcbf1ee58c6" 
/dev/sdd1: UUID="5a1aaf46-6de7-4df5-8bd8-0fd958b2ecba" TYPE="ext3"
```

I also use uuid's in grub.

Jim

---

### Post by DarwinLabs on 2009-01-14
Awesome, thanks for the info I'll try it when I get home.

---

### Post by Traumadog on 2009-01-14
FYI:

You can also assign a label to the volume if UUIDs are not to your liking.  The process to assign a label is as follows:

```
tune2fs -L Label_Name /dev/hda1
```

This will label the first partition on the first hard drive on the system "Label_Name".

Hope this helps! :)

Traumadog.

---

