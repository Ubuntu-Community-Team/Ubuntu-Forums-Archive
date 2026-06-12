---
title: "access restrictions on mounted ntfs HDDs - links"
date: 2010-07-12
forum: Server Platforms
---

### Post by krack3rz on 2010-07-12
So i made me a home server and I wanted to share files but sadly since I'm dual booting most of those files are in NTFS formatted HDDs. I cant chnage the format into ext4 because its too much data and I dont have space...I mount those HDDs at every restart.

So what I need to do is to set it so that they automount themselves at startup (I have no clue how this can even be done)

and

so that I can make symbolic links to those files so that others may access them, which is not possible now since ntfs only allows for one permission type - the user (me) #-o

i want to keep those links to folders and individual files in a folder /var/www/links or somethin like that.

help! ](*,)

---

### Post by arrrghhh on 2010-07-12
Automount with fstab.

As for symlinks... You may want to look into a 'bind' mount, not sure what would be best for you in that situation.

---

### Post by ruffEdgz on 2010-07-12
I don't know about the symbolic link question but for the mounting of NTSF Windows Partitions to your Ubuntu system, did you check out this link?

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

See if that helps as it talks about how to get NTFS partitions to work on Ubuntu and once you get that, you can edit /etc/fstab to help automount them if you reboot or what not.

---

