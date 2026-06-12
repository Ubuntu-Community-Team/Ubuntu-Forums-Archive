---
title: "chmod directory and all contents"
date: 2008-04-27
forum: Server Platforms
---

### Post by Tavorisch on 2008-04-27
hey when im in a folder, and i type chmod 777 * it chmods all the directories and files,, how do i chmod everything in the subfolders..
like if im in /etc/steam/  and i type chmod 777 * it chmods all folders and files.. if i go into any of those chmodded folders none of the files or subdirectories are chmodded.. simple question.. but what do you type in a search... why are so many people worried about other peoples security? im not a threat its just for a game server.. and as im aware only users can do anything with the files.

---

### Post by scragar on 2008-04-27
```
chmod -R 777 .
```will chmod the current directory, and all sub directories and files.

---

### Post by Tavorisch on 2008-04-27
done deal. thx...

---

### Post by koenn on 2008-04-27
recipe for disaster

---

### Post by Dr Small on 2008-04-27
> **koenn said:**
> recipe for disaster
+1
Never execute the above command in /

---

### Post by scragar on 2008-04-27
I would never recomend it on anything other than an already public file, and then the universal execute perms will cause problems, just because they always do, so it's by far not a perfect solution, rather than chmodding it's always best to see what can be done first with chown and groups, since this way permtions are left alone.

---

