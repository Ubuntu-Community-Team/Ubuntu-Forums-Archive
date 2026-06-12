---
title: "[APACHE2]Create an Vhost"
date: 2010-12-28
forum: Server Platforms
---

### Post by AdrianWierciochPHP on 2010-12-28
Hi!
I`m new so again hi all! 
I`ve problem with set up a Virtual Host on my Ubuntu machine (LTS 10.0.4). I did all according to this tutorials:
[http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/](http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/)
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
and I can`t create it. I don`t now why, because when i check status is all right and nothing problem with reload apache engine.
I have installed zend server earlier and its vhost isn`t work too. I reinstalled once my ubuntu, but problem is repeating.

Sorry for my english I`m from Poland and it`s my the first time I have written post in english :)

---

### Post by howefield on 2010-12-29
Moved to Server Platforms.

---

### Post by bttw on 2010-12-29
If you could post the vhost file, it would help.

If you're having trouble creating the actual file, try:

```
sudo nano /etc/apache2/sites-enabled/vhost

```

That should open a new file in the editor.

---

