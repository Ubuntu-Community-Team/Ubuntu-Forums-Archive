---
title: "Trying to install Sony Vegas 8.1 (64 bit) or 8.0 (32 bit) with Wine troubles."
date: 2009-02-06
forum: Wine
---

### Post by GARoss on 2009-02-06
I've installed Wine on Ubuntu 8.10-64 bit & am trying to install Sony Vegas 8.1 (64 bit) or 8.0 (32 bit) with Wine & have troubles. I do own these & have the necessary product keys. Currently, I am trying to keep everything in Ubuntu instead of a dual boot.
1st, the 64 bit version does nothing. I did, however, get some response with 8.0 which is 32 bit but on install it said I needed NetFramwork 3.0 & another MS OS app installed 1st. It went through a download of these, then it abruptly failed to install.
I'm guessing it's because of the differences in Linux & XP file management systems but don't have a clue how to work-a-round or if this possible at all. Maybe it's a MS thing, too?
Any ideas?
George

---

### Post by sedawk on 2009-02-06
There is an entry in Wine's application database for vegas:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15288](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15288)

As you found out already, the problem is to get Net 3.0 and the C++ stuff
to install.
Net 3.0 doesn't seem to work in Wine currently:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9828](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9828)

The C++ Redistributable seems to work fine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5766](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5766)

---

### Post by GARoss on 2009-02-06
Yep! That's a shame, Vegas is a great program.
Thanks

---

