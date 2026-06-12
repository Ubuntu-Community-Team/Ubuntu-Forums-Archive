---
title: "Change http port"
date: 2009-11-03
forum: Server Platforms
---

### Post by any.linux12 on 2009-11-03
Hi!

Can I have more than one http port and chose the file (index.html) that represents that port? for example, can I have one website on the default port (80) and one in the 81,82...9999 whatever?

---

### Post by Lars Noodén on 2009-11-03
That would be setting up port-based virtual hosts:

[http://httpd.apache.org/docs/2.0/vhosts/examples.html#port](http://httpd.apache.org/docs/2.0/vhosts/examples.html#port)

One of the files to look at will be /etc/apache2/ports.conf in addition to one configuration file per vhost.

---

