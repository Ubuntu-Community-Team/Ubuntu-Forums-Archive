---
title: "Firestarter: Root Privileges"
date: 2005-02-19
forum: Server Platforms
---

### Post by ceti on 2005-02-19
Since I set/changed/enabled root user password, everytime I boot into Ubuntu I get this error message:

INSUFFICIENT PRIVILEGES:
You must have root user privileges to use Firestarter

Nonetheless, the program starts normally.
I used chown, chgrp, chmod 777 & chmod a+x to change permissions, but to no avail:  this annoying message insists in show up. How do I get rid of it?
Thanks in advance for any help.

---

### Post by xinel on 2005-02-19
Hello Ceti

have you read this explination?

[http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter)

- xinel

---

### Post by ceti on 2005-02-20
[QUOTE=xinel]Hello Ceti
 
 have you read this explination?
 
 [http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter]("http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter")
 
 - xinel[/QUOTE]
 
 Thank you, xine, but it didn't work.
 
 ceti

---

### Post by aton77 on 2006-04-10
[QUOTE=ceti]Since I set/changed/enabled root user password, everytime I boot into Ubuntu I get this error message:

INSUFFICIENT PRIVILEGES:
You must have root user privileges to use Firestarter

Nonetheless, the program starts normally.
I used chown, chgrp, chmod 777 & chmod a+x to change permissions, but to no avail:  this annoying message insists in show up. How do I get rid of it?
Thanks in advance for any help.[/QUOTE]

I was having the same problem.  I got it to stop by disabling "start/restart firewall on program startup" in the firestarter preferences.

Hope this helps.

---

