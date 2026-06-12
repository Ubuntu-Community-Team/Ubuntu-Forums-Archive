---
title: "Rsync selected directories in users home dir"
date: 2011-11-15
forum: Server Platforms
---

### Post by clubbing80s on 2011-11-15
Hi. 
I'm tying to rsync  users /home directories to a new server. But I want to only copy selected files and directories.   

typically :

clubbing80s/.bash_history
clubbing80s/.bash_logout
clubbing80s/.bashrc
clubbing80s/.gitconfig
clubbing80s/.mysql_history
clubbing80s/.nano_history
clubbing80s/.profile
clubbing80s/.ssh/*

and exclude anything else.
I have been playing with variations of

 rsync -av '--include=.ssh/*' '--exclude=*' /home/ /tmp/

as a test , but I sill get other files / dirs I don't want.

Any suggestions ?

GM

---

### Post by papibe on 2011-11-15
Hi clubbing80s.

Since you are excluding anything else at the end, you need to include explicitly the the path of the files (clubbing80s/ or */ for all users).

For me, it is easier to use the option --include-from, and put all include and exclude rules in one file. For example (includes.txt):
```
+ */
+ .bash_history
+ .bash_logout
+ .bashrc
+ .gitconfig
+ .mysql_history
+ .nano_history
+ .profile
+ .ssh/
+ .ssh/*
- *

```
Now, you may be seeing lots of things being copied any way. That is because rync has in my opinion the 'bad practice' of always copying the whole directory tree, even if it's not copying any file under it. You can avoid that using the option --prune-empty-dirs (or -m for short).

Considering all of the above, this should work:
```
rsync -avm --include-from=includes.txt  /home/  /tmp/
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by clubbing80s on 2011-11-15
Works like a charm.

Many Thanks !!!

G

---

### Post by papibe on 2011-11-15
:D Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

