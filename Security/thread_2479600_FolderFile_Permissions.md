---
title: "Folder/File Permissions"
date: 2022-09-29
forum: Security
---

### Post by pushbike06 on 2022-09-29
Ubuntu 22.04/Files application.

Question: 

If I set the Permission for Folders and included files of .mozilla and .thunderbird to deny read/write access to "others", will this interfere with the updating and upgrading of the respective applications.

Read/write access is set for "me" and my "log in name group" only.

My intention is to restrict access to data associated with these applications e.g email addresses and content.

---

### Post by TheFu on 2022-09-29
If the ~/ (same as $HOME) removes any access for other, then no directories or files below it can be accessed by anyone who isn't the userid for that $HOME or in the same group.

You know, you really should test this in /tmp/somewhere and see it for yourself.

Setting HOME to be 700 (more restrictive than asked) shouldn't break anything.  Same for any directory under it.
Now, snap packaged programs often have strange thoughts about this and seem to break with any non-default settings, but I haven't tested this specific scenario.  Test it. See if it breaks anything.  If so, put it back or restore from your backups.  You do have backups, right?

---

