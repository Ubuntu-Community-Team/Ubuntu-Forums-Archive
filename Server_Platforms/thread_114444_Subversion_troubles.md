---
title: "Subversion troubles"
date: 2006-01-08
forum: Server Platforms
---

### Post by Silent1 on 2006-01-08
I've been using subversion for a couple of months now and i'm now running into trouble when i restarted my workstation. My workstation is winxp  pro and installed subversion/apache2/webdav thru apt-get on my ubuntu server. I used to just edit the file and then commit and type a message with tortoiseSVN.
BTW if i use tortoisesvn i get these same error msg's, this code below is what i type on the server.
```

sudo svn commit -F mmenuns4.js
svn: Log message file is a versioned file; use '--force-log' to override
sofa@hawtmail:/var/fix/trunk/old/milonic/js$ sudo svn commit --force-log -F mmenuns4.js
svn: Commit failed (details follow):
svn: '/var/fix/trunk/old/milonic' is not under version control and is not part of the commit, yet its child '/var/fix/trunk/old/milonic/js' is part of the commit

```
Now if i try to add the dir js its says "theres nothing to add", lately what i've been doing is deleting the old files then importing them. Any ideas, thanks in advance.

---

### Post by ZylGadis on 2006-01-08
I would urge you to use the time-proven cvs instead of svn. I know two quite knowledgeable administrators who decided to switch to svn and have only had trouble with it - something is broken all the time. Besides, I have yet to see a major open-source vendor use svn instead of cvs. Perhaps there is a reason for that.
Svn is all very shiny with new functions, etc, but after all, it's supposed to be run on a server, i.e. it should be very stable before somebody uses it seriously.

---

### Post by tageiru on 2006-01-08
[QUOTE=Alex.P]I would urge you to use the time-proven cvs instead of svn. I know two quite knowledgeable administrators who decided to switch to svn and have only had trouble with it - something is broken all the time. Besides, I have yet to see a major open-source vendor use svn instead of cvs. Perhaps there is a reason for that.
Svn is all very shiny with new functions, etc, but after all, it's supposed to be run on a server, i.e. it should be very stable before somebody uses it seriously.[/QUOTE]
How about Mono and KDE? I have used subversion in many projects and it has always worked perfectly. It brings some major improvements in comparison to CVS. Moving files and folders with the metadata intact and atomic commits...

And to solve the problem the thread author had; the -F flag specifies that the file is a change log that will be used for the commit log. This is incorrect since you specify the actual file that you want to commit.

Use svn ci file instead, or svn ci file -m "commit message" if you want to specify the commit message on the command line.

---

### Post by Silent1 on 2006-01-08
well after an entire day of messing around all it was the current version i had checked out and had nothing to do with the svn repo itself. Just check'd out a new version and now everything is running smoothly again. Thanks

---

