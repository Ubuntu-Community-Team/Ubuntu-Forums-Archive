---
title: "Group permission problem"
date: 2010-07-09
forum: Security
---

### Post by Turtle.net on 2010-07-09
Hi,
I have a problem access privileges on several folders like this one
```
$ ls -l
total 40
drwxrwx---  9   1000 finance    4096 2010-07-09 14:27 Finance
...
```
It clearly says that I have owner and group read write and search (it's a directory) privileges.
I login as user master part of group events
```

$ cat /etc/group|grep finance
finance:x:1003:master,....

```
But I can't access the folder (Permission denied).

Any idea ?

---

### Post by Yarui on 2010-07-09
Is the group that has permission for the folder the primary group of the user you are trying to access it with?  I feel like that shouldn't make a difference but there have been times when I have been unable to do things because the group with permissions wasn't my primary group.

---

### Post by jbrown96 on 2010-07-09
Primary group doesn't have anything to do with *this* problem; however you may have different problems with newly created files. 

Have you logged out since you were added to finances? That's my only thought.

---

### Post by Turtle.net on 2010-07-09
Yes I have logged oout then back in, no change
The group is not the primary group. This should not be the problem though.
I also tried to reboot (i know that was foolish) and no change (as expected).
;(

---

### Post by Sylvain Falardeau on 2010-07-09
> **Turtle.net said:**
> Hi,
```
$ ls -l
total 40
drwxrwx---  9   1000 finance    4096 2010-07-09 14:27 Finance
...
```It clearly says that I have owner and group read write and search (it's a directory) privileges.
I login as user master part of group events


The 1000 on your "ls -l" is supposed match a user and it's not, which is weird. The group "finance" seems to work fine but to be sure, do a "ls -ln" which shows numeric ids only. See if "finance" is really" 1003 (like in your group file) and that your current user has the group 1003 (finance) with the command "id".

Example:

```

$ id
uid=1000(sylvainf) gid=1000(sylvainf) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),121(admin),124(sambashare),1000(sylvainf)

```

Do numeric ids match?

---

### Post by Turtle.net on 2010-07-09
Yes numeric ids match ...
And the user 1000 doesn't exist on this system because the folder is a NFS mount from another box. The folder was created by user 1000 on this distant box.
I guess I should have pointed that out earlier ...

---

### Post by Sylvain Falardeau on 2010-07-09
Ok, that's right. If 1000 exists only on the remote system and you don't have it in your local passwd file, it won't show up in "ls".

NFS mounts can introduce problems because of the synchronization of uid/gid numbers (it only use the uid and gid for filesystem permission check). There is also a limit of 16 groups for a user in NFS (I am not sure if the Ubuntu or your server has this limitation). If the group on your local machine is the 17th, maybe it does get to the server and when it tries to access the filesystem... permission denied.

Did you try to connect with ssh directly on your remote server with a user who as the "finance" group (check with "id") and try to "cd" in the directory?

---

### Post by Turtle.net on 2010-07-09
> **Sylvain Falardeau said:**
> There is also a limit of 16 groups for a user in NFS (I am not sure if the Ubuntu or your server has this limitation).
Great idea. I had more than 16 groups, I reduced that to 13 ... no change.

---

### Post by Sylvain Falardeau on 2010-07-09
And did you try a remote ssh with a user in the "finance" group to cd into the directory in question?

---

### Post by jbrown96 on 2010-07-10
You should have mentioned that it was NFS earlier. 

You need to make sure that the GID for finance matches on the client and server.

---

### Post by Sylvain Falardeau on 2010-07-10
> **Turtle.net said:**
> Great idea. I had more than 16 groups, I reduced that to 13 ... no change.

When you reduced the groups on your NFS client machine, did your umount/mount to be sure the new information was not cached somewhere?

---

### Post by Turtle.net on 2010-07-10
> **Sylvain Falardeau said:**
> When you reduced the groups on your NFS client machine, did your umount/mount to be sure the new information was not cached somewhere?
Yes i did, i aso tried to relaunch NFS exports on the server, and also a reboot on both client and server, no results.

---

### Post by oldfred on 2010-07-10
I have not used NFS shares but saved these on related sharing:

Shared users using bindfs:
[http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by Turtle.net on 2010-07-10
Ok I solved it.
Thanks to all of you.
My problem was that my user had the correct gid on the client to access the folder, but the same uid was defined on the server with some gids missing. I think that the problem was that the NFS server was checking the permissions based on the gids defined on the server not on the client since it found a matching uid.
So i made sure to have the uid on both client and server matching and gids as well.
That made the trick.
Thanks again :)

---

