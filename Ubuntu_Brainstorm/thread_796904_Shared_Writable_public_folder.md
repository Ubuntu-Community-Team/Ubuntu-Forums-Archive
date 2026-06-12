---
title: "Shared Writable public folder"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-16
To be used for certain config files applicable to all users, for example game high score tables (so every user of the system sees the same high scores), and also for file sharing between users.

It would also be good for system config files that it should be possible to change without sudo access, for example the previous position of the volume control or the screen brightness.

Maybe this already exists, but if it does I've overlooked it.

---

### Post by smartboyathome on 2008-05-16
I think this could be a potential security flaw. If there is a "shared writable folder", then malicious code could store its files there, and then use those to exploit a system.

---

### Post by CrazyGuy123 on 2008-05-16
Yes it is a potential security flaw, not particularly from executables, but from exploiting bugs in parsers of the config files stored there.

There still needs to be a reasonable way (ie. non sudo) for one user of an Ubuntu system to send some documents to another user of the same system without resorting to using a usb stick.  (effectively a usb stick is a shared writable folder as well, so the security risks are comparable)

---

### Post by smartboyathome on 2008-05-16
There is, make a folder, right click on it, click properties > permissions (I think thats it) and make it read/write between the users group. I think a function where you can go to properties and click "share with other users" would be acceptable.

---

