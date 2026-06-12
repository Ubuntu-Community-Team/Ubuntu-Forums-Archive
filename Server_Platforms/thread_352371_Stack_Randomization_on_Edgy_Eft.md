---
title: "Stack Randomization on Edgy Eft ?"
date: 2007-02-03
forum: Server Platforms
---

### Post by Adnarim on 2007-02-03
Hi,
I've a question. Is there a standard stack randomization on Ubuntu Edgy Eft? It's really important for me to know that because I think it is. And furthermore is there a way to switch it temporarly off/on?

greets

EDIT: I found the answer somewhere else. As root (sudo su)
```
echo 0 > /proc/sys/kernel/randomize_va_space
```
swichtes Virtual Address Space Randomization off and with 1 it switches it on...

---

