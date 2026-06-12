---
title: "Enabling ftp access for friends"
date: 2007-10-04
forum: Server Platforms
---

### Post by holiday on 2007-10-04
I want to give friends sftp access to a sub-directory of a drive mounted at /media.

I've set permissions like this:

ls -al  | grep disc2

drwxrwxrwt  7 holiday friends 4096 2007-09-27 17:40 disc2

And these cascade into the subdirs.

Desperate? You're right. 

So I give my friend's home directory a symlink into a sub of disc2  but when I logon as that user, and try to access that directory, this is what I get:

Couldn't canonicalise: Permission denied

What's going on?

---

### Post by netlogic on 2007-10-04
I would love to help, but I can't understand your question. Can you please re-state your question? Take your time with it.

---

