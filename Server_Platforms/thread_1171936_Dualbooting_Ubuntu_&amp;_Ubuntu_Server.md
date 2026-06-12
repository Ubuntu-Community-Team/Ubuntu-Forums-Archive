---
title: "Dualbooting Ubuntu &amp; Ubuntu Server"
date: 2009-05-27
forum: Server Platforms
---

### Post by SilverSnakeEyes on 2009-05-27
I've got a pretty decent computer I'd like to use as a server. The problem is, I have a windows xp partition I can't access, next to a Ubuntu partition I CAN access. The problem is however, I need to figure out how to delete the windows partition, expand part of it to the Ubuntu partition, and use the leftovers to create a specific option in GRUB for a Ubuntu LAMPP server. I want to be able to choose between using it for my leisure/use and using it for a server on startup 

(What I'm asking without all the filler is, What tool can I use to delete a partition, expand one, and create one? (And how can I dual boot this Ubuntu Partition with normal ubuntu) That's the simple way of saying it.)

Also, how can I set up this server so I can update the htdocs from another computer? (I'd rather it be a mounted network drive than FTP)

---

### Post by cariboo on 2009-05-28
Gparted is the tool your are looking for. Boot from the LiveCD and do what you want to the partitions. Look for gparted under System-->Administration-->Partition Editor.

---

### Post by SilverSnakeEyes on 2009-05-28
Okay, thanks!

---

