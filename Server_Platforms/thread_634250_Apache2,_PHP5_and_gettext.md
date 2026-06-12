---
title: "Apache2, PHP5 and gettext"
date: 2007-12-07
forum: Server Platforms
---

### Post by knj on 2007-12-07
Hi all.

I am trying to get gettext to work on a webserver with no luck at all.

I have installed PHP5 like:
sudo apt-get install php5 libapache2-mod-php5

(also mysql-module and a bit more).


I have a graphical interface running for some other uses as well. I have installed the PHP-GTK-module for running some of those applications, where gettext works!

Though on my webserver, it will not work at all... After hours of debugging, I have found out, that gettext wont work if the php-gtk-module is not loaded? (so if I insert dl("php_gtk2.so") and run it in CLI-mode, then it works! (it does not work in CLI-mode without PHP-GTK loaded as well)).

A temporary soulution could be to just load php_gtk2.so at all times, but that wont load unless it is startet from a terminal connected to a display - which Apache is not.


Can someone help me out?

---

### Post by knj on 2007-12-08
I have now written a kind of locales-abstraction-layer, which can work with the normal locales extension and the "php-gettext"-module (a locales-module written in PHP).

If someone has any interest in this, they are more than welcome to have it. Just write me on [email]kaspernj@gmail.com[/email]. Its less than 100 lines of code.

This way I can activate the "normal" gettext-extension, if the gettext-extension actually works, or just use the php-gettext... Maybe this is a bit of an overkill?

---

