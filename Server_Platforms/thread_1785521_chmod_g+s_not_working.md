---
title: "chmod g+s not working"
date: 2011-06-18
forum: Server Platforms
---

### Post by markab on 2011-06-18
Hi,

I have spent the last 2 hours trying to get this to work and it is driving me crazy, I have a 11.04 box and have setup some zfs filesystems for data storage, I have 2 users and have created a group called media and added both of the users to the group.

I have changed the group of the directory to media and have set chmod g+s

root@saturn:/tank/data# ls -l
total 8
drwxrws--- 2 root media 2 2011-06-18 13:59 Backups
drwxrws--- 2 root media 2 2011-06-18 14:26 Music
drwxrws--- 2 root media 2 2011-06-18 12:44 Pictures
drwxrws--- 2 root media 2 2011-06-18 14:07 Video

if I then go to the directory with one of my users and touch test_file I get

mark@saturn:/tank/data/Music$ touch test_file
mark@saturn:/tank/data/Music$ ls -l
total 1
-rw-r--r-- 1 mark mark 0 2011-06-18 14:49 test_file

or mkdir

mark@saturn:/tank/data/Music$ ls -l
total 3
drwxr-sr-x 2 mark mark 2 2011-06-18 14:49 test1
-rw-r--r-- 1 mark mark 0 2011-06-18 14:49 test_file

should the file and directory creation not inherit the group of the parent directory???

---

### Post by egpetrich on 2011-06-18
That does sound strange. I would expect the group inheritance as well.

I just ran some quick test commands similar to your commands, but on the ext2 filesystem on my server. The group inheritance worked as expected. Do you have the ability to do a quick test on a non-zfs filesystem to see if the problem shows there as well?

Oh, in the just-checking category, can you run the command "groups" while logged in as "mark" and verify that the group "media" appears in the output? If it doesn't, you need to log out of "mark" and log back in.

---

