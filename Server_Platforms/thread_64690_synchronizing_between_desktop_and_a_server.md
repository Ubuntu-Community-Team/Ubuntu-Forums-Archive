---
title: "synchronizing between desktop and a server"
date: 2005-09-11
forum: Server Platforms
---

### Post by muszek on 2005-09-11
It's about time to start thinking about synchronizing versions between two computers.  There are two of them (there might be more in the future, but they're not important enough for us right now to waste our time) :
1.  WinXP machine, where a coder develops the crucial part of our project (php website).
-- accessible through Samba from the server.
-- no ftp server installed (not a problem to install, though)
-- no ssh server installed (I guess not a problem, either)

2.  Ubuntu server, which is used by others (those that are not in the network) to access the project files (it's the only one visible from outside).
-- not accessible via Samba (and I'd rather not mess with it)
-- accessible via ssh and samba.

What I want to do:
1.  have two directories: current and stable.
2.  files in current would be automatically synchronized with some dirs on winxp machine  (one way only, winxp machine --> server).
3.  files in stable would be synchronized with either current or winxp folder.  Not automatically, but only upon request.

I'll handle backing up/versioning separately, so it's not important.

Any tips on how to do it and what software to use?  Thanks in advance.

---

### Post by mlomker on 2005-09-12
Most sysadmins use a command-line tool called rsync.  There are versions for windows.

[Rsync homepage](http://rsync.samba.org/)

---

### Post by deuce868 on 2005-09-12
You might checkout subversion. You could host the repository on the linux server and check out a copy on it. Then you would checkout/update the copy on the windows machine and with subversion you can setup a stable and a testing branch. It's not direct file sync, but it sounds like what you need.

---

