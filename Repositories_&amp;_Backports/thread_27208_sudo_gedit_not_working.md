---
title: "sudo gedit not working"
date: 2005-04-15
forum: Repositories &amp; Backports
---

### Post by lmellen on 2005-04-15
:? I just finished installing and am using the Unofficial Ubunto 50.4 Starter Guide to add extra repositories. The 1st line in the instructions worked well, the 2nd doesn't: sudo gedit /etc/apt/sources.list-- it returns: sudo: gedit: command not found. Anybody know how to fix this? --  Thanks -- Larry :smile:

---

### Post by jensyt on 2005-04-15
```
sudo apt-get install gedit
```

Alternately, you could use nano instead of gedit.

---

### Post by mendicant on 2005-04-15
And you should probably use aptitude instead of apt-get:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

---

### Post by lmellen on 2005-04-15
:) sudo apt-get install gedit --  worked fine -- Thank You -- Larry

---

