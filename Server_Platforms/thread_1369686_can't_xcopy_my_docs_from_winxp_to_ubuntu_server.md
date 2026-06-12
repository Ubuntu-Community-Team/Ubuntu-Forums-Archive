---
title: "can't xcopy my docs from winxp to ubuntu server"
date: 2010-01-01
forum: Server Platforms
---

### Post by mendo on 2010-01-01
i want to write a batch file to copy s:\my documents (winxp) to q:\backup\my documents (ubuntu server)

q:\backup is a samba share on an ubuntu server

when i try to execute a simple xcopy command to copy My Docs to the server from the command line on the winxp machine, i get an error telling me "access denied"  and "unable to create directory"

using the same xcopy command, i can copy other directories from the same drive (s:) on the winxp machine to the same backup destination (q:).

i can drag  and drop my documents from s: to q:.  the copy completes w/o error.

from command prompt in winxp, i can create directories in the backup destination.

i don't get it.  is there something special about the My Documents folder?

My Documents = 2.25 GB  is that a problem?

i hope that's all the relevant info.  thanks.

happy new year.

---

### Post by sylvester_0 on 2010-01-03
Hmm, this isn't a direct answer to your question but here goes. What about using rsync (deltacopy on Windows) to backup your MyDocs to the Ubuntu server?

When I setup up a client/server network, I usually have all documents living on the server (which is backed up offsite.) You can easily "move" the My Documents folder to the samba server by right clicking it and choosing properties.

---

### Post by CharlesA on 2010-01-04
The My Docs folder is usually set so that only you can access it. I don't know why it's having problems.

For XP, you could try using deltacopy but I've not used it (or heard of it).

I mostly use rsync.

---

### Post by mendo on 2010-01-05
thanks for the feedback.  i am looking into rsync next.

i don't know why my docs would be giving me trouble either.  it's so weird that i can drag and drop it to the server, but not xcopy it.

i am following this thread about this issue as well:

[http://ubuntuforums.org/showthread.php?t=1367387&highlight=rsync](http://ubuntuforums.org/showthread.php?t=1367387&highlight=rsync)

---

