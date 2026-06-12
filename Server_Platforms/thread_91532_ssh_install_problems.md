---
title: "ssh install problems"
date: 2005-11-17
forum: Server Platforms
---

### Post by urbanride on 2005-11-17
im not quite sure if this is the place ... so i loged into my ubuntu box via ssh

and evey time i try to install a package i get this error



```
urban@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
```

its the same "E: Couldn't find package " error ... 

keep in mind i am a super *nix n00b

---

### Post by grendelkhan on 2005-11-17
That's a package from breezy extras, do you have that repository enabled?

Do an apt-cache search after an apt-get update.

---

