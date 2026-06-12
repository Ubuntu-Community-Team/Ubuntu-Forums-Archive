---
title: "&quot;It Works&quot; not displaying...Apache?"
date: 2011-07-04
forum: Server Platforms
---

### Post by rileyb76 on 2011-07-04
Guys,
Just installed a LAMP server.  Set my static IP at 192.168.1.128.  Got a test Wordpress blog setup at: [http://192.168.1.128/blog](http://192.168.1.128/blog)  

However, if I goto just 192.168.1.128  (where it used to display It Works!), well now it just gives a folder listing - Index of / - of Blog and thats it.  Does that mean something with Apache isn't functioning correctly, or turned on?

Or is it a DNS issue maybe?  Something with the resolv.conf file?

Thanks!

---

### Post by rileyb76 on 2011-07-04
Tried to restart Apache2 and received an error:



~$ /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!

---

### Post by CharlesA on 2011-07-04
Check what the documentroot is set for.

See [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html").

---

### Post by rileyb76 on 2011-07-04
Thanks for the reply.  I believe you are correct.

I was playing around (doh!) and deleted the first wordpress site here: /var/www
I must've deleted something else.  I think there was an index.html file I removed also.  

What all was inside that file?

Thanks!

---

### Post by CharlesA on 2011-07-05
Here's what was inside that file:

```

<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>

```

---

### Post by rileyb76 on 2011-07-05
Perfect!  Thanks for your help!

---

