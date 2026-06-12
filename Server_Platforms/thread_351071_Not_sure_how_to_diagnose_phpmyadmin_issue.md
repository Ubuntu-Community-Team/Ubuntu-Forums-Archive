---
title: "Not sure how to diagnose phpmyadmin issue"
date: 2007-02-01
forum: Server Platforms
---

### Post by qwert231 on 2007-02-01
I would like to use phpmyadmin. I am trying to follow the instructions here:
[http://flurdy.com/docs/postfix/#conf_admin](http://flurdy.com/docs/postfix/#conf_admin)

However... even before that, if I go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I get:
Not Found

The requested URL /phpmyadmin was not found on this server.

I currently have 2 sites running off this box. Synaptic says phpmyadmin is installed.

Where should I start to look?

---

### Post by JamieC on 2007-02-01
I use CentOS but with Linux you must remember that files and folders are case sensitive. Have you tried /phpMyAdmin/?

If it does not work are you sure that the httpd server is up and running? Do HTTP requests to localhost work?

If so check if a directory similar to /phpMyAdmin/ exists in the defined document root. If it does not, check to see if an alias is set up in the webserver configuration file (Apache's is httpd.conf).

Sorry I couldn't be of more help.

---

