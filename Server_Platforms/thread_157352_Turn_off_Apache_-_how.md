---
title: "Turn off Apache - how?"
date: 2006-04-09
forum: Server Platforms
---

### Post by 3rdalbum on 2006-04-09
I have Apache installed to serve files occasionally to people who request them on MSN. I'd like to turn off Apache at the times that I'm not using it.

I thought that, in order to shut down Apache, you typed:
```
apache2ctl -k stop
```

But when I do that, it tells me that "httpd is not running". And indeed, the server does keep running.

I have Apache listening on a high numbered port (in the 6000s).

Is there another way of shutting down Apache from the command line?

---

### Post by petterah on 2006-04-09
Hi, you could use the invoke-rc.d script, or specify full path, like this:

   /etc/init.d/apache2 stop

or

   invoke-rc.d apache2 stop

If you want to disable the apache2 at boot, try this:

   update-rc.d -f apache2 remove

To enable it again, this should do the trick:

   update-rc.d apache2 defaults 91

The last number is the priority, when apache will start... the default number with me when apache was installed was 91, but if you don't specify a number it will give a smaller number pri - it will start quiker... i think the 91 is ok to use on a desktop system.

-Petter-

---

### Post by armen_shlang on 2007-12-29
I'm also having the same problem and i tried all the command s that you have listed but trying all those gave me this message:

open: Permission denied
 * Stopping web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5775?) not running
open: Permission denied

Cheers.

---

### Post by finferflu on 2007-12-29
Did you try with sudo?

```
sudo /etc/init.d/apache2 stop
```

---

