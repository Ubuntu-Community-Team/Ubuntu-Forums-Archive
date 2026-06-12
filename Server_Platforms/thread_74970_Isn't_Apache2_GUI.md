---
title: "Isn't Apache2 GUI?"
date: 2005-10-13
forum: Server Platforms
---

### Post by werty on 2005-10-13
I am pretty new to ubuntu.
How am i supposed to view the Apache Web Server Console. 
Isn't Apache Graphical like IIS?
Im very much lost.....

---

### Post by phrozen on 2005-10-13
hahaha
no, sorry mate, apache is not GUI
you mite want to check this thread plus im pretty sure ive seen a few other around, just do a search for apache GUI or something 
[http://ubuntuforums.org/showthread.php?t=71781](http://ubuntuforums.org/showthread.php?t=71781)

---

### Post by az on 2005-10-13
The GUI is not neccessary and a security risk.  Servers typically do not run them.

On a unix system, the graphical environment (X windows) is optional.  It is built on top of the rest of the system and your system does not depend on it.

You can burn a cd, log into a remote box, listen to music, pretty much anything from the command line. 

apache is the most popular web server in the world and it's complete source code package is only 7.5 Megs big.

You can install the apache2-doc package to learn how to configure it.  It is not that difficult.

---

### Post by skirkpatrick on 2005-10-13
Or install WebAdmin, which will allow you to administer more than just your Apache.

---

### Post by brentoboy on 2005-10-14
I kind of wish I could:
dpkg-reconfigure apache2

even if it is command based question and answer, at least it would be "easy" to do, if I have special needs, then I would go take the result and tweak the settings file. (like I do with xorg.conf)

Same with samba, & other "server" stuff that has no GUI options.

Of course, a gui option would be even better.
I can boot to X in order to have the nice GUI tools, and still be smart enough to close out of X durring normal use.

---

### Post by pingswept on 2005-10-15
[QUOTE=skirkpatrick]Or install WebAdmin, which will allow you to administer more than just your Apache.[/QUOTE]

You mean Webmin, no?

---

### Post by Jad on 2005-10-15
or use apache toolbox
[http://www.apachetoolbox.com/](http://www.apachetoolbox.com/)

---

### Post by az on 2005-10-15
[QUOTE=brentoboy]I kind of wish I could:
dpkg-reconfigure apache2

even if it is command based question and answer, at least it would be "easy" to do, if I have special needs, then I would go take the result and tweak the settings file. (like I do with xorg.conf)

Same with samba, & other "server" stuff that has no GUI options.

Of course, a gui option would be even better.
I can boot to X in order to have the nice GUI tools, and still be smart enough to close out of X durring normal use.[/QUOTE]
Installing apache2 gives you a default configuration file to edit.  You also have some nice command-line tools for apache2.  There is a gui for samba, it is the shared-folders configuration tool.

---

### Post by bluck on 2005-10-17
[QUOTE=werty]I am pretty new to ubuntu.
How am i supposed to view the Apache Web Server Console. 
Isn't Apache Graphical like IIS?
Im very much lost.....[/QUOTE]

Apache is very different. 
take a look at your *.conf files, which will be in  /etc/apache2 


and dont stress.. *nix is actually very simple, just takes a lot of reading n typing ;)

---

