---
title: "[SOLVED] public_html is not working"
date: 2008-08-01
forum: Server Platforms
---

### Post by squeekmore on 2008-08-01
I'm a Windows admin trying out Ubuntu 8.04 server for the first time and I'm having a problem getting a web page hosted.

For a general guideline, I've been following the instructions at: 

[http://www.parcival.org/2006/07/14/howto-install-joomla-on-your-very-own-ubuntu-server/](http://www.parcival.org/2006/07/14/howto-install-joomla-on-your-very-own-ubuntu-server/)

The server is running in VMware with LAMP, ssh, and sambo, and my WinXP desktop has puTTY to connect.

If I access [http://IPaddress](http://IPaddress) I get a page saying "It works!", but if I try to access [http://IPaddress/~username](http://IPaddress/~username) I get a 404 error.

Is there a resource available that explains this in detail?

---

### Post by mbeach on 2008-08-01
I think you just need to:
```

sudo a2enmod userdir
```
and restart the server with
```
sudo /etc/init.d/apache2 restart
```

---

### Post by mbeach on 2008-08-01
some documentation:
[http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

I think if you want to change the name of the 'public_html' you can so so in:
/etc/apache2/mods-available/userdir.conf

---

### Post by squeekmore on 2008-08-01
Thank you, that a2enmod command did the trick.

---

