---
title: "Shared folder permissions"
date: 2010-05-31
forum: Security
---

### Post by tristicles on 2010-05-31
Hi folks. Having a bit of a problem with sharing. This could be my lack of understanding of UNIX file permissions. Let's see if that's the case....!

All partitions involved are ext4.

My friend Clive runs a small company with one employee, Peter. I've set up a Lucid server and two lucid workstations. Using NFS, I'm sharing server:/data/drives/shared to the local network, mounting it on /media/shared on the workstations.

I've created a group called "shared" on the server and workstations and it has the same group ID on all three boxes. Likewise the users and their respective groups have the same user/group ids across the board.

The /data/drives/shared folder on the server has permissions of -rwxrwx--- root shared, as does the mount point on the workstations.

The shared folder is being mounted successfully via /etc/fstab.

When Peter saves a file on /media/shared, it is created with peter as the owner (obviously) and peter as the group. Obviously Unix differs from Windows (sorry to swear in here) in that new files don't inherit the permission of the folder they're created in.

To get around this problem, I did a usermod -g on peter and clive's accounts, giving them "shared" as the primary group (again on all three boxes).

This has nearly resolved the problem as they can read each others files. They can't amend or delete though. Peter's new file is listed as 

```
-rwxr-x-- peter shared 2010-05-02 00:01 document1.odt
```

rather than

```
-rwxrwx--- peter shared 2010-05-02 00:01 document1.odt
```

as I'd have expected (eg, the group has read-only rather than write permissions). What can I do, if anything, to get around this?

Thanks,
Tris

---

### Post by oldfred on 2010-05-31
I do not know ownership and permission well but saved this, but it was for one PC not networking:

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by Lucky. on 2010-05-31
> The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

This is beautiful advice right here.

> To get around this problem, I did a usermod -g on peter and clive's accounts, giving them "shared" as the primary group (again on all three boxes).

This was a great try, and if it works, it works!  Another good way is to try oldfred's advice.  Using his way, you can avoid changing each user's primary group.  So peter can keep his primary group as peter, and clive can keep his primary group as clive.

To elaborate a bit more:

1.  Put peter and clive's primary groups back as peter and clive.

2.  Make sure that peter and clive are still members of the "shared" group.  It doesn't have to be their primary group, but just make sure they are members of that group.

3.  From the server, reset the permissions and the group on your shared folder (and all subfolders/files).  So if the folder is "/data/drives/shared", try the following:

The first command changes the primary group to shared:

```

chgrp -R shared /data/drives/shared

```

The second command resets your permissions on files and folders to rwxrwx--- (2770) in case there's any stragglers.

```

chmod -R 2770 /data/drives/shared

```

I noticed that you set your files to have execute properties.  That's good if you want that, but most of the time files only need "rw-" properties.  Of course if you use recursion on the "chmod" command, that screws up your directories.  Gah!  Here's another way to change permissions recursively to make directories executable while keeping files straight read/write:

The first command finds any files and sets them to 0660 (rw-rw----).  They don't need the SGID bit since they're not directories (so nobody will inherit from them).

```

find /data/drives/shared -type f -exec chmod 0660 {} \;

```

The second command finds any directories and sets them to 2770 (rwxrwS---).  Really this is "rwxrwx---", but the SGID bit makes it look a little different.

```

find /data/drives/shared -type d -exec chmod 2770 {} \;

```

With the SGID bit set (the 2 in front), all files and folders created inside of /data/drives/shared will inherit the same group as the directory itself (which is now set to "shared").

That takes care of the group, but it still won't inherit permission bits.  I feel your pain, Windows takes care of inheritance very elegantly, and it's real different in Linux.

Using standard permissions, the only way to get your new files to look like "rwxrwx---" (770) is to change your umask on every client machine that accesses the server.  The umask is what is referred to each time you create a new file or folder...it has nothing to do with inheritance at all.  Take a look at [this thread](http://ubuntuforums.org/showthread.php?t=1491819) to show how you can change the umask permanently (basically just edit /etc/profiles and modify the bottom line to "umask 007" if you want "770" permissions).

To get much nicer inheritance, you can use access control lists (ACL).  Give standard permissions / umask a chance and master it before moving on though.  The first time I set up a server I went gung-ho on ACLs.  After some experience, I realized I hardly needed them.  When I finally came back to use them, I had found my previous experience made me use ACLs much more effectively.

---

### Post by tristicles on 2010-06-06
You guys rock!!

Oldfred, thanks for the info re folder permissions. I've applied that and it's enabled me to put back the primary groups as you suggested.

Lucky, many thanks for the heads up re umask. This is exactly what I was looking for. Thanks for the find syntax, too. That was really helpful. Will have to squirrel that one away for future use. May have a look at ACLs further down the line. Too much new technology for me to look at. Don't know where to start.

Thanks again,
Tris

---

### Post by diablo2nd on 2010-11-10
I know this is an old thread however the infomation contained within is the most detailed yet simple to understand explanation of sGID i have come across. I also was having the same issue of requiring a shared folder. for the last month  or two I had been doing chgrp admin /data -R && chmod 777 -R from cron every half hour.

**I would also like to note and more importantly, the nautilus issue was resolved for me by adding umask 007 into ~/.gnomerc (creating the file if it doesn't exist)**

---

