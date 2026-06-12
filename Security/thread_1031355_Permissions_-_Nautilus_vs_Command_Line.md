---
title: "Permissions - Nautilus vs Command Line"
date: 2009-01-05
forum: Security
---

### Post by measekite on 2009-01-05
Intrepid 8.10

Situation: Using Live CD

USB flash drive for some reason became read only.  I cannot delete folders or files.  I brought up Nautilus and went to the Permissions tab of the properties of a folder.  These were the permissions:

Owner     It was me
Access:   Create and delete files
Files Access:   ,,,

Group:  root
Folder Access:  none
File Access:  ...

Others
Folder Access:  none
File Access:  ...

When I attempted (me as administrator and in the root Group) to delete either a folder or a file I was denied due to insufficient permissions.  I attempted to change the Group: from me to root and was denied.  I really could not make any changes to the permissions even though I was the owner.
[COLOR=Red][B]
QUESTIONS[/B][/COLOR]

What can I not make these changes in the GUI from nautilus?

Do I need to use chmod from the command line and will that work?

If the command line works then why can I not do the same thing from nautilus if the GUI just provides a dialog box to accomplish the same thing.

Is there some kind of a bug?


Please place you answer below each question.  Thanks in advance.

---

### Post by cdenley on 2009-01-05
FAT16 and FAT32 filesystems do not support UNIX permissions. The UNIX permissions which are used are assigned when the filesystem is mounted.

---

