---
title: "start apache at bootup"
date: 2005-11-15
forum: Server Platforms
---

### Post by benlen on 2005-11-15
Hi
I try to get apache to start when I start Ubuntu, but I can't get it to work.

i hav made a link in /etc/rc5.d to apachectl

Any ideas?
Is there a log I can look in?

---

### Post by ebrowne on 2005-11-15
Hey Assumeing you have apache installed the nessassary files should already be in /etc/rcX.d if not useing update-rc.d  apache2 defaults .  On the next reboot it should start up.  Oh I noticed in my config /etc/init.d/apache2 there is a line that reference a ON BOOT option in /etc/apache2/"filename" edit that file to be a 1 and your all set.

---

### Post by LordHunter317 on 2005-11-15
Runlevel 5 is not the default runlevel in Ubuntu, 2 is.

---

