---
title: "[SOLVED] apt-get install not working"
date: 2009-01-10
forum: Server Platforms
---

### Post by joey_p1979 on 2009-01-10
I just built a ubuntu 8.10 server and apt-get install is not working. I can't install anything please help. 

jrplowman@Net-J-S1:~$ sudo apt-get install rwho
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rwho

---

### Post by tubezninja on 2009-01-10
If you just installed, you need to update package indexes first:

```
sudo apt-get update
```

Then you should be able to install your packages.

In fact it's good practice pretty much before the start of a new install session, if you haven't done it in over a day or so.

---

### Post by joey_p1979 on 2009-01-10
Thank you that worked. I was doing apt-get install update...can you tell I'm a newbie!!

---

