---
title: "Opera mailbox sharing"
date: 2006-11-28
forum: The Cafe
---

### Post by HeSh on 2006-11-28
Is it possible to make Opera share mailboxes between systems? I want to use Opera on WinXP and Ubuntu but in that way so it shares mail folder and all mail.

I was thinking on using -personaldir switch and direct linux opera to windows settings, but as I see in Opera's .ini files, all paths are not relative but full file paths. Next thought was just to change "Mail Root Directory" in Opera.ini, but in mail settings all paths are also full.

Anyone has any idea how to do this?

---

### Post by bailout on 2006-11-28
I do this but the best way is to have a fat32 partition with opera installed to under windows and then sort out the linux install. You need opera on fat32 because Lnux is unreliable writing to ntfs. Basically you either edit the opera.ini file or use symlinks in the linux opera folder to redirect to the windows install.

Here is a post on the Opera forum I made about it.

[http://my.opera.com/community/forums/topic.dml?id=128708](http://my.opera.com/community/forums/topic.dml?id=128708)

Worth reading through as other people came up with interesting points. The second post has a link to a page that details the settings used in the opera.ini file.

---

### Post by HeSh on 2006-11-28
Thanks. I'll check out the link. I already have all files that i want shared on FAT32 so all i need is configure everything.

---

### Post by Aleksandersen on 2006-11-30
```
rsync
```

---

