---
title: "Why can I not open .htaccess files?"
date: 2012-05-31
forum: Server Platforms
---

### Post by Jacob72 on 2012-05-31
I am not hosting websites, I am running LAMP to build and test locally on ubuntu 10.04. I want to be able to edit .htaccess files. I have read Ubuntus's article about [Enabling the use of the .htaccess]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles") file, and would like to check before following the guide that I am not going to create any issues by doing so?

Thanks

---

### Post by Lars Noodén on 2012-05-31
You'll see .htaccess talked about a lot because there are situations where the user does not have access to the web server configuration.  However, I bet you're not one of those cases.[indent]
"*In general, you should never use .htaccess files unless you don't have access to the main server configuration file. *"
--[https://httpd.apache.org/docs/2.2/howto/htaccess.html#when](https://httpd.apache.org/docs/2.2/howto/htaccess.html#when)
[/indent]
If you're working locally and have control over the server, or at least one of the virtual hosts, then you can skip using .htaccess and put the changes directly in the web server's configuration file.  .htaccess is only a work-around for cases where the user doesn't actually have access to the web server configuration.  It's better to keep everything in the same place and use the configuration files that came with the server.

---

### Post by Lars Noodén on 2012-05-31
Just so you know, the web configurations are in /etc/apache2/sites-available/  You can assign group write privileges to any virtual host that has its config files there.  If you need even finer granularity then you can use [Include](https://httpd.apache.org/docs/2.2/mod/core.html#include) to farm out parts of the configuration file to specific individuals.  It's a lot tidier and better performance than the .htaccess kludge.

---

