---
title: "apache2 and mod_rewrite"
date: 2009-08-11
forum: Server Platforms
---

### Post by rompstar on 2009-08-11
Hi,

I have Ubuntu 9.04 Server and the default Apache2 install.

I need to see if mod_rewrite module is activated and running.

Three Questions

1) How do I check ?

2) If I have to edit some configuration file, which one ?

3) Once it is running, I need to prevent hot image linking!  How do I do that ?

My httpd.conf file is empty, and most of my host specific details are here:

/etc/apache2/sites-available/default

Thanks!

---

### Post by rompstar on 2009-08-11
I found the answer for the first 2 questions.

#1 

execute command

sudo a2enmod rewrite

#2 restart apache2


Just need help with Question 3

---

### Post by rompstar on 2009-08-11
nevermind, googles it, thanks!

:P

---

