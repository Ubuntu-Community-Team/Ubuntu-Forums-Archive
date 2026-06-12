---
title: "Cake PHP Trying to enable mod rewrite Apache Ubuntu 9.10"
date: 2009-11-25
forum: Server Platforms
---

### Post by jonesyp on 2009-11-25
Hi,

I am trying to run Cake PHP with Ubuntu 9.10 Desktop.  I have installed the LAMP packages (With the install by type in apt and I chose LAMP server)

How do I enable mod_rewrite?  I have seen various commands mentioned, but also told there is a bug in 9.10.

Final question - How to I make var/www writable?

Kind regards

Peter Jones

---

### Post by speedy18us on 2009-12-17
To make var/www writable:

sudo chmod 777 /var/www

And to enable mod-rewrite:

[http://ubuntu-for-humans.blogspot.com/2009/11/enable-mode-rewrite-on-apache-ubuntu.html](http://ubuntu-for-humans.blogspot.com/2009/11/enable-mode-rewrite-on-apache-ubuntu.html)
or
[http://komunitasweb.com/2009/02/cakephp-tutorial-installing-cakephp-on-ubuntu/](http://komunitasweb.com/2009/02/cakephp-tutorial-installing-cakephp-on-ubuntu/)

---

### Post by CalamityJane on 2010-02-23
I have a similar problem and those two tutorials didn't work. 

mod_rewrite is loaded and works for other sites, but not for Cake. I adapted the default file following the tutorial but I get an 500 Error. If I keep "none" instead of the suggested "all" I get a plain HTML page and the links won't work.
Did the tutorials work for you or has anybody another suggestion for a solution?

Jane

---

### Post by jogrady on 2010-03-17
The first blog post worked for me.  I didn't need to look at the second.  Make sure you Enable mod-rewrite per the instructions.  It's easy to overlook.

sudo a2enmod rewrite

and dont forget to restart apache 

$ sudo /etc/init.d/apache2 restart

---

