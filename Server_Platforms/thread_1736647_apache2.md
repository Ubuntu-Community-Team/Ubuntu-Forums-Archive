---
title: "apache2"
date: 2011-04-22
forum: Server Platforms
---

### Post by Mosabama on 2011-04-22
Hello, 

is there away to reduce the information provided by Apache logging to access.log?

I mean it logs EVERY thing including the icon files it has accessed each time a client requests a page. its being really informative which makes it difficult for me to keep track of important logs.

I know there are some programs to view the logs in a proper way, but I am not interested in that. I just want to know if there is a way to limit it to "who accessed the page and when, and some other info like the clients OS and browser and stuff like that.

thanks in advance.

---

### Post by ruffEdgz on 2011-04-22
It doesn't look like there is an easy way to just change the access level like you can with Error Logs, but here is a link to the Apache website that can help:

[http://httpd.apache.org/docs/2.0/logs.html#accesslog](http://httpd.apache.org/docs/2.0/logs.html#accesslog)

It seems you have the power to make a 'custom format' for your access.log file. Here is another link to help you understand the 'LogFormat' directive:

[http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#logformat](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#logformat)

If you just want to know some of the basic things you want, I would do something like:
> LogFormat "%h %t %U" common
Something like that...

Hope that helps.

---

### Post by Mosabama on 2011-04-22
Thanks ... I will read that and I will let you know..

---

