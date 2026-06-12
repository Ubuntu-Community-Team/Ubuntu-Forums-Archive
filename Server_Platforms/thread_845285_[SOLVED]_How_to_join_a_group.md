---
title: "[SOLVED] How to join a group"
date: 2008-06-30
forum: Server Platforms
---

### Post by skunkbad on 2008-06-30
If I want to make a new group, and then add myself to it, what would I do?

I've seen the addgroup command, and am guessing I can just use:
addgroup newgroup

but I have been reading and searching for how to add myself to the group.

---

### Post by sisco311 on 2008-06-30
```
sudo addgroup groupname
sudo addgroup username groupname
```

---

### Post by skunkbad on 2008-06-30
Thank you.

---

### Post by Iowan on 2008-07-01
**usermod** is another option, but there are some cavaets:  [http://ubuntuforums.org/showthread.php?t=814462]("http://ubuntuforums.org/showthread.php?t=814462")

---

### Post by sisco311 on 2008-07-01
with usermod you can add a user to multiple groups with a single command:
```
sudo usermod -a -G group1,group2,... username
```
-a = append

---

