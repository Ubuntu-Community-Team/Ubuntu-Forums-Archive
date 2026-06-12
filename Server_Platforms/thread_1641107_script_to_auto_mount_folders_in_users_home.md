---
title: "script to auto mount folders in users /home"
date: 2010-12-08
forum: Server Platforms
---

### Post by BarryDocks on 2010-12-08
I would like to mount some folders in every users /home folder.  I first thought this might be achievable by modifying fstab but clearly not:
[http://ubuntuforums.org/showthread.php?p=10213680#post10213680]("http://ubuntuforums.org/showthread.php?p=10213680#post10213680")

Next I think it would be better to write a bash script that will do this and can be run at boot.  I know that the shell variables $HOME and $USER are going to be useful, but I have no idea where to start:(

I would like to:
1. check if /home/<username>/mountpoint exists for all users and if not create it with approptiate read/write permissions
2. mount /mountdir in /home/<username>/mountpoint for all users

I would like to avoid symlinks as I want to use ftp access and jail the users to their /home folders (which is easy to do with ProFTP)

Any help would be warmly welcome!

---

### Post by Vegan on 2010-12-08
One idea is to make a shell script and put it in the startup for each user than has mount commands for the resources you want to provide.

---

### Post by BarryDocks on 2010-12-09
> **Vegan said:**
> One idea is to make a shell script and put it in the startup for each user than has mount commands for the resources you want to provide.
Thanks for your reply, would this work for users logging on as both a remote ftp client and a local samba client?

Also, I have not got the first clue about were to start writing such a script? any suggestions?

---

