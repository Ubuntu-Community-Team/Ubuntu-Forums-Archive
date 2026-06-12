---
title: "restoring backups with encrypted partition"
date: 2009-02-06
forum: Security
---

### Post by treymul on 2009-02-06
I had some issues the other day and had a little difficulty figuring out how to solve them.  So I wanted to put an overview of what I had to do, just in case someone else needed it.
     I have a dual boot system, windows and ubuntu.  Ubuntu / and swap are on an encrypted partition.  I have a small boot partition that is not.  I also use tar to tar up my entire system every couple of days to back things up.  I do this in two parts; the / folder and then a seperate file for /boot(which is the boot partition).  This all came from this post(which shows how to restore also) 

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backing+system]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backing+system")

     The problem I had the other day is that I ran out of room on my windows partition.  I tried shrinking my other partition so it could be extended, but it would not allow it. So I went into windows and just extended the partition.  I figured I could just restore ubuntu onto a smaller partition.
     The problem with this is that all information is pointing to partitions that do not exist anymore.  I took me quit a while, but I figured out what all had to be changed.

     First I install the new base system to the newly partitioned encrypted drive using the alternate cd.  Restart and log in.  Then I made copies of /etc/fstab, /etc/crypttab, and /boot/grub/menu.lst.  Now I can restore my files to /.  I then had to compare fstab and crypttab to the copies I made and change any differences in the new to show the same paths and uuid as the copied files. 
     Next I mount my /boot, delete the content, and untar my boot backup.  I then compare the menu.lst with the copied one, and again make the new one reflect the paths of the copied on(with respect to the pertinent partitions).
     This is where I stopped several times and rebooted only to find that something is not right.  what you need to do at this point is update all initrmds files on your boot partition.  This is done with "update-initrmfs -k all -u".

This took me the better part of the day yesterday to figure out.  Just wanted to give anyone else who needs it an idea of what direction to go.

---

