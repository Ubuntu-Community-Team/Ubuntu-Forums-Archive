---
title: "[SOLVED] PHP: Cannot open files for writing"
date: 2007-07-24
forum: Server Platforms
---

### Post by pc_michael on 2007-07-24
I'm running Apache 2 and PHP 5.  Currently, my PHP scripts can open files for reading (and indeed read them), but it cannot open files for writing, returning a "permission denied."

I'm assuming I have to chgrp my DocumentRoot to add it to some sort of apache or PHP group or something?  I tried chgrp-ing it to www-data, since that seemed like the most obvious choice,but it didn't work.  Both my usernames (the admin and my personal account which currently owns the web directories) are part of the www-data group as well.

What should I do?

---

### Post by Mr. C. on 2007-07-24
If your group owns the files, and you have group write permissions, the www-data needs to belong to *your* group, not the other way around.

You must restart apache after adding to supplemental groups, because they are read when a process starts.

MrC

---

### Post by pc_michael on 2007-07-24
Thank you for replying.  I tried adding user www-data to both my username's groups, as both primary and secondary groups (does that matter?), restarting apache each time, but to no avail.

How can I check what group owns the directories?  Maybe I'm not adding www-data to the correct group.

---

### Post by Mr. C. on 2007-07-24
```
ls -ld /path/to/directory
ls -l /path/to/*

```

MrC

---

### Post by pc_michael on 2007-07-24
Ah!  I reread your post, and checked to make sure my directories had group write permissions, and it didn't.  So I fixed that, added my group to www-data, and it worked!  Thank you very, very much. :)

---

