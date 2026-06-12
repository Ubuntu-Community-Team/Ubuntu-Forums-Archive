---
title: "Keeping Users in their Home directory"
date: 2006-09-10
forum: Server Platforms
---

### Post by BlueFusionX on 2006-09-10
Okay, I am going to be hosting people on my server.  The thing is, I don't want people to read my configuration files to find out my MySQL passwords, nor do I want people seeing the files of other people.

How would I accomplish this?  I already tried chmodding my config files to 700, but now I get a PHP error: Permission denied.

What should I do?  I was considering a jail shell, but would it still work with Apache's user directories mod?

---

### Post by rastilin on 2006-09-11
What do you mean by hosting people on your server?

---

### Post by etcpool on 2006-09-19
did u mean to hosting the shell service on your machine?

if so, there're a lot of jailed shells out there..


try searching on the internet for chrooted shell


;)

---

