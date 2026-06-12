---
title: "Can't connect to MySQL on LAMP implementation"
date: 2006-07-24
forum: Server Platforms
---

### Post by kenquad on 2006-07-24
Hi all:

I have Ubuntu LAMP installed on a Dell box with a database configured full of sample data.  I have set up a user called Dreamweaver with permission to access the base from anywhere.  This user can log into the database directly with no problems.  However, when I try to access the server over LAN using a gui tool such as Navicat, I get an unable to connect error.  I poked around in MySQL's my.cnf file (after back it up - fortunately since I broke it badly) and found a setting that referred to the program by default listening for connections only on localhost.  If this is the case, how can I alter that setting from the command line?  If not, does anyone have an idea why this might be happening?  And is there a simple diagnostic tool that would run on Windows (my terminal's OS) for testing the connection?  Incidentally, both the Windows terminal and the Ubuntu server can ping each other with no problems.

Thanks,
Ken Ha Quad

---

### Post by az on 2006-07-24
[http://ubuntuforums.org/showthread.php?t=215716](http://ubuntuforums.org/showthread.php?t=215716)

---

### Post by kenquad on 2006-07-24
Hi:

ALL RIGHT!!!  Weird thing is, I found that same binding setting in my.cnf, only I approached it from the other direction, changing that IP address to the one for the terminal from which I was attempting access.  Still can't bring the connection up in Dreamweaver, but that's another forum.

Thanks!

Ken Ha Quad

---

