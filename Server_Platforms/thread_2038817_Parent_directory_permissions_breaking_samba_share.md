---
title: "Parent directory permissions breaking samba share"
date: 2012-08-07
forum: Server Platforms
---

### Post by MrKravin on 2012-08-07
Greetings,

I'm building a NAS server, but I'm running into a problem. I was working on creating an rsync test when I discovered my samba share folders had broken. I've checked the individual share permissions, all set to 770, but I can't get them to prompt for a password anymore. I get a "You do not have permission" error. Even if I do 777, it still won't let me in.

Currently, my shares sit in /mnt/Data/. Inside /Data/, I have 4 folders, each with a different group that can access it.  The only way I can get into the shares is if I start to alter the parent directories permissions, such as changing the group owner to All(all users), or by applying 777. If I do either of these, it then opens up all of the subdirectories to everyone, despite specific permissions having been set per folder. 

I've made sure that no changes are being made recursively, at least not in the commands I enter. How can I fix this situation?

---

### Post by bakegoodz on 2012-08-12
Forgive me for a basic question. Are you making sure the permissions are set on the folder its self and not just the files inside?
```
ls -ld foldername
```
Or while inside the folder
```
ls -ld .
```

---

