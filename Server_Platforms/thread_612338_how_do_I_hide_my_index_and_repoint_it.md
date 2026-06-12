---
title: "how do I hide my index and repoint it?"
date: 2007-11-13
forum: Server Platforms
---

### Post by kustomjs on 2007-11-13
Hi Guys
I need to know how to hide my index and repoint it so my domain can be correct because right now this what i got for my domain setup: 
and this what i am talking about to hide :
[IMG]http://i22.photobucket.com/albums/b324/xtremesunfire/untitled.jpg[/IMG]
[http://206.51.165.11/jbodyconnection/oscommerce-2.2rc1/catalog/](http://206.51.165.11/jbodyconnection/oscommerce-2.2rc1/catalog/)

I want the domain name to be like this jbodyconnection.com/catalog but i dont know how to do that.

---

### Post by doanut on 2007-11-13
You should use Virtual hosts, otherwise you can create a symlink on your document root

ie
ln -s /var/www/jbodyconnection/index.php /var/www/index.php

Or you could setup a virtual host (better way to do things)

*replace .php with .html if required.

---

### Post by kustomjs on 2007-11-13
so should I delete every thing out of var/www/ and put it where?
then reset it up under virtual host? or what would be the best way of doing this and being secure about this?

---

### Post by doanut on 2007-11-13
Just had a look at your configuration.

you may need to change the symlink to the following:

ln -s /var/www/jbodyconnection/oscommerce-2.2rc1/catalog/index.php /var/www/index.php

But do use Virtual hosts unless this is a 1 site per server setup.

---

### Post by kustomjs on 2007-11-13
when i did that switch now I got error:
[http://jbodyconnection.com/](http://jbodyconnection.com/)

---

### Post by doanut on 2007-11-13
delete the index.php in /var/www

setup a virtual host. and you should be good to go.
Make sure you choose the document root as /var/www/jbodyconnection/oscommerce-2.2rc1/catalog/

---

### Post by kustomjs on 2007-11-13
how can I install virtual host?

---

### Post by doanut on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=201460](http://ubuntuforums.org/showthread.php?t=201460)

Check out that thread.

---

