---
title: "Local development server"
date: 2008-09-28
forum: Server Platforms
---

### Post by cu3edweb on 2008-09-28
I have set up my laptop as a local development server. The problem is I downloaded a website that I have but when I navigate to it in my browser (firefox and opera) it trys to save it as a phtml file and wont open it?

Please help.

---

### Post by RealPSL on 2008-09-28
Is your local Web Server configured to handle .phtml files? If you not you will have to edit the httpd.conf or the relevant included file to add it e.g.```
AddType application/x-httpd-php .phtml .php
```

You will need to restart the web server as well ```
/etc/init.d/apache2 restart
```

---

### Post by cu3edweb on 2008-09-28
I did that but I am still getting the same result.

---

### Post by cu3edweb on 2008-09-28
Also if it matters phpmyadmin works fine and so does a php test page.

---

### Post by cariboo on 2008-09-29
Dumb question, but did you restart apache after making changes to the configuration file?

Jim

---

### Post by RealPSL on 2008-09-30
I would love to see the access log file that this is producing if possible.

---

### Post by cu3edweb on 2008-09-30
This is what is in the access log when I try to open that site.

127.0.0.1 - - [30/Sep/2008:11:20:06 -0700] "GET /gordon HTTP/1.1" 301 363 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3"

any help would be great. Also I just noticed that if I go to another page from that site it works so:

[http://localhost/test/](http://localhost/test/) - doesn't work

and

[http://localhost/test/about](http://localhost/test/about) - does work

Thanks

I am using a frogcms if that matters?

---

### Post by RealPSL on 2008-09-30
I assume /gordon is a directory that contains an index file of time .phtml correct? Can we see the configuration for the directories that work and the ones that do not?

---

