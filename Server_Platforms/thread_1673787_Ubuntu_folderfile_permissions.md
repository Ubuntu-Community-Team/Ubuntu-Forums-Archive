---
title: "Ubuntu folder/file permissions"
date: 2011-01-22
forum: Server Platforms
---

### Post by rysliv on 2011-01-22
Every time I try to change file or folder permissions on a separate internal drive in ubuntu 10.10 desktop in sudo file manager, It sets it right back to the way it was before and doesn't save the permissions I want to change it to. The files aren't critical system files that are not even existent on this hard drive.

Its on a completely separate drive, Yet aren't I suppose to be in control of what gets changed to what? Instead of a Operating System doing something just for my safety? A simple AVI files permissions being changed shouldn't hurt anything.

How to I stop ubuntu 10.10 from auto setting the permissions of my folders and files?
Its really starting to **** me off right now..

I've been looking around on google for Auto reset permissions for ubuntu, Haven't found one word about it.

Yet I'm just going to assume someone might know how to resolve this? Or has dealed with this before.

I'm just trying to Forcefully set my folders on my separate drive all to 777 because they are all 775 and 755 and I can only access them with Write privileges if I run the SUDO file manager which I really hate having to do every so often I'm sure you can relate to how annoying it is to have to open up terminal and type something in to open a fully priviledged file manager.


any ideas?

---

### Post by bab1 on 2011-01-22
> **rysliv said:**
> Every time I try to change file or folder permissions on a separate internal drive in ubuntu 10.10 desktop in sudo file manager, It sets it right back to the way it was before and doesn't save the permissions I want to change it to. The files aren't critical system files that are not even existent on this hard drive.

Its on a completely separate drive, Yet aren't I suppose to be in control of what gets changed to what? Instead of a Operating System doing something just for my safety? A simple AVI files permissions being changed shouldn't hurt anything.

How to I stop ubuntu 10.10 from auto setting the permissions of my folders and files?
Its really starting to **** me off right now..

I've been looking around on google for Auto reset permissions for ubuntu, Haven't found one word about it.

Yet I'm just going to assume someone might know how to resolve this? Or has dealed with this before.

I'm just trying to Forcefully set my folders on my separate drive all to 777 because they are all 775 and 755 and I can only access them with Write privileges if I run the SUDO file manager which I really hate having to do every so often I'm sure you can relate to how annoying it is to have to open up terminal and type something in to open a fully priviledged file manager.


any ideas?

What file system does the drive have (EXT or NTFS or ...)?

---

### Post by amsterdamharu on 2011-01-23
It would help if we know how the drive is mounted.

Could you post the output of the following commands?

```
sudo fdisk -l
cat /etc/fstab
umask
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code]Your pasted stuff&#91;/code]

Could you tell us which drive is the drive you're talking about ( /dev/sd?? )

---

### Post by rysliv on 2011-01-23
The drive uses a NTFS file system.

Yet I'm starting to think that NTFS does not have extended support for Linux CHMODs

---

### Post by bab1 on 2011-01-23
> **rysliv said:**
> The drive uses a NTFS file system.

Yet I'm starting to think that NTFS does not have extended support for Linux CHMODs

You can't use chmod with NTFS.  The best you can do is mount the system with the user and group permissions you want.  See [**[COLOR="Blue"]_here _[/COLOR]**]("http://opensuse.swerdna.org/susentfs.html")for the general idea.

---

### Post by amsterdamharu on 2011-01-23
The ntfs driver in Linux doesn't support chmod but it still might be mounted read only, could you post the output of the commands as I've requested before so we can add something to the fstab to mount it read write, owned by your user?

---

