---
title: "Apache not called Apache, right?"
date: 2011-03-03
forum: Server Platforms
---

### Post by Learning Linux 2011 on 2011-03-03
Hi,

I'm new.

The web server component of Apache isn't actually called "Apache" right?  It is called something else? I didn't realize there were so many parts.

Also, is there a good newbie introduction to how to configure it for a basic web server?

Thanks

---

### Post by jwcalla on 2011-03-03
If you grab it from Synaptic it's called "apache2".  Personally I think their website has some decent documentation for settings.

---

### Post by HugoSerrano on 2011-03-03
Hello!

For a basic setup, you can do:

sudo apt-get install apache2

And that's it! You got your server running ;-)

By default the server will serve the content in the folder /var/www/ that belongs to user and group www-data:www-data

Regards!

---

### Post by James78 on 2011-03-03
For a [LAMP]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") (**L**inux-**A**pache-**M**ySQL-**P**HP) installation, you could use [this article]("https://help.ubuntu.com/community/ApacheMySQLPHP") for information (also serves as a good 'newbie introduction'). To install it you could use a command like:
```
sudo tasksel install lamp-server
```
If tasksel doesn't exist on your system, just install it:
```
sudo apt-get install tasksel
```
Some more help resources
[URL="https://help.ubuntu.com/8.04/serverguide/C/httpd.html"]Apache2 on Ubuntu
[/URL][Apache2 official documentation]("http://httpd.apache.org/docs/2.2/")

---

### Post by HugoSerrano on 2011-03-03
Don't need to install tasksel

> sudo apt-get install lamp-server^

will do the trick

Regards!

---

### Post by James78 on 2011-03-03
> **HugoSerrano said:**
> Don't need to install tasksel
Certainly. I forgot to mention that better method. ;)

---

