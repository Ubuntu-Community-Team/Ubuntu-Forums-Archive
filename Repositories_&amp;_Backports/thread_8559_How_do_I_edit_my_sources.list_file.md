---
title: "How do I edit my sources.list file?"
date: 2004-12-18
forum: Repositories &amp; Backports
---

### Post by hypersonic5 on 2004-12-18
Ubuntu newbie here. I want to add a bunch of new repositories to Ubuntu but I can't seem to figure out how to edit the file itself. I can't log in as root in Ubuntu therefore I can't directly edit it and save like any other file. Can someone please show me how to do this? I'm sorry if it has been asked before, but I searched for sources.list and came up with nothing. 

Thanks in advance.

---

### Post by crun on 2004-12-18
You can either fire up synaptic and go to "setting -> repositories" or edit the sources.list file by typing

$ sudo gedit /etc/apt/sources.list

Remember that Ubuntu does everything with "sudo" - that's your access to the root account

---

### Post by ykpaiha on 2004-12-18
hello
/etc/apt/sources.list
if you have mc installed (sudo mc) then F4 you can easy pass or copy inside
or more ubuntu way (maybe : sudo gedit /etc/apt/sources.list)

---

### Post by hypersonic5 on 2004-12-18
Thank you so much guys! I got it!

---

