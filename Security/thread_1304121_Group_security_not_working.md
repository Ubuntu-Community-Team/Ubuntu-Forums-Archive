---
title: "Group security not working?"
date: 2009-10-28
forum: Security
---

### Post by JKringen on 2009-10-28
Hi, I'm hoping this is just some obvious mistake that I'm missing somehow. I have a /mnt folder where I mounted a series or RAID drives on my network server that's running Ubuntu. These folders and all of their files are owned by root. Root permissions are rwx and I created groups for each of these volumes. For example, I created a 'documents' group for the Documents folder, etc. The group permissions are rw only and everyone else has no permissions at all. The idea was that any user belonging to the 'documents' group would have read/write access to the Documents folder but none of the others, etc. Pretty simple. However, I'm noticing that even though my username is a member of these groups, it still denies me! I'm not sure why that would be. I've included a shell excerpt so you can see the folders, permissions, user information, and when it denies me still. ANy ideas here?

jason@JMK-SRV:/mnt$ id
uid=1000(jason) gid=0(root) 
groups=0(root),10(uucp),1002(documents),1003(media),1004(applications),1007(suuser)

jason@JMK-SRV:/mnt$ ls -al
total 32
drwxr-xr-x  6   root root                4096 2009-06-04 14:55 .
drwxr-xr-x  21 root root               4096 2009-10-24 11:10 ..
drwxrw---- 36 root applications 4096 2009-09-29 14:28 Applications
drwxrw---- 15 root documents    4096 2009-09-29 16:10 Documents
-rw-r--r--  1   root root                6148 2009-08-24 21:48 .DS_Store
drwxr-xr-x  2   root root                4096 2009-06-04 14:55 ExternalHD
drwxrw---- 10 root media            4096 2009-09-21 11:22 Media

jason@JMK-SRV:/mnt$ cd Media
bash: cd: Media: Permission denied

???

---

### Post by Agent ME on 2009-10-29
Have you logged out and logged back in? Changing a logged in user's groups doesn't take affect until they log in again.

---

### Post by JKringen on 2009-10-29
Hi, yep the machine has been restarted even quite a few times since the user's group was changed. I actually made those groups & assigned them to the user before I even created the folders, knowing that I was going to be using that. =/ Seems very odd to me that it's denying the user when he's a member of the group and the group has RW access....

---

### Post by JKringen on 2009-10-31
Bumping this...any ideas here? I just installed a new Ubuntu system for a client of mine and I'm seeing this same behavior! Even though I had users in a group that has RWX access to files/folders, they are denied access to them....:(

---

### Post by Agent ME on 2009-11-01
Oh, I just remembered! The folder needs to have +x permission to be able to see its contents. So running "sudo chmod g+x /mnt/Media" will do the trick.

---

