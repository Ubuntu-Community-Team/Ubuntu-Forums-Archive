---
title: "Firestarter"
date: 2006-03-28
forum: Server Platforms
---

### Post by xXx 0wn3d xXx on 2006-03-28
I had firestarter installed, but I then removed it and reinstalled. Now I get an error message while trying to install. What can I do to fix this ?

---

### Post by CompShrink on 2006-03-28
What is the error message?

---

### Post by mdmarmer on 2006-03-28
Also

sudo apt-get remove firestarter

may not remove config files

you may remove more with

sudo apt-get remove firestarter --purge

but it's possible that may not remove everything either, as presumably firestarter sets itself up to start automatically and these scripts, etc. might not be removed

see

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

 Mike

---

### Post by Neur0s1s on 2006-03-30
I just did the same thing.  I used sudo apt-get remove firestarter but that was after killing all pid (not sure if that was necessary, i just did it).  Then afterwards I removed the /etc/firestarter/ directory as thats where the config files were.

---

