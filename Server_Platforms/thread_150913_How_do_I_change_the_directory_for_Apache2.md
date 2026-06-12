---
title: "How do I change the directory for Apache2?"
date: 2006-03-26
forum: Server Platforms
---

### Post by echo $USER on 2006-03-26
I have looked all through /etc/apache2 for the place to change the default directory from /var/www to /home/**** 

Thanks for the help, and I included my apache2.conf if that helps.

---

### Post by henriquemaia on 2006-03-26
[QUOTE=echo $USER]I have looked all through /etc/apache2 for the place to change the default directory from /var/www to /home/**** 

Thanks for the help, and I included my apache2.conf if that helps.[/QUOTE]

Probably there are more elegant solutions, but you can make /var/www a link pointing to whatever folder you want to use as your default apache folder. It's very simple and you don't have to change the configuration file.

It works on mine.

---

### Post by harisund on 2006-03-27
[http://ubuntuforums.org/showthread.php?t=149611](http://ubuntuforums.org/showthread.php?t=149611)

There is a thread on configuring apache2

---

### Post by LordHunter317 on 2006-03-27
You would change the DocumentRoot in /etc/apache2/sites-enabled/000default.

But why?

---

### Post by echo $USER on 2006-03-27
Thanks for the help.  Just what I was looking for.

---

