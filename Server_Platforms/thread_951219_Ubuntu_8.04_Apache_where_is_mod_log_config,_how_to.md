---
title: "Ubuntu 8.04 Apache where is mod_log_config, how to modify CustomLog ???"
date: 2008-10-17
forum: Server Platforms
---

### Post by alienprdkt on 2008-10-17
I am new to Apache and Ubuntu, first time setup, and loving every minute of it. But have read about customizing what apache2 logs for you, and everything talks about a mod_log_config file,
[http://httpd.apache.org/docs/2.1/mod/mod_log_config.html]("http://httpd.apache.org/docs/2.1/mod/mod_log_config.html")
 which I can not find any info on or about with apache2 and Ubuntu. 

I guess I want to Log Image Requests from Local Pages

example I have this info (and some others):

Use SetEnvIfNoCase to restrict logging to only those requests from outside of your site:

<FilesMatch \.(jpg|gif|png)$>
    SetEnvIfNoCase Referer "^http://www.example.com/" local_referrer=1
</FilesMatch>
CustomLog logs/access_log combined env=!local_referrer


Question is where to put it, or what to do with it in Ubuntu 8.04?

(think there was a spot in /etc/apache2/apache2.conf but not to sure how to)

examples would be greatly appreciated.  Thanx in advance.

---

### Post by alienprdkt on 2008-10-18
ok,
here is a couple others, 

To automatically roll over the Apache logs at specific times without having to shut down and restart the server:

CustomLog "| /path/to/rotatelogs /path/to/logs/access_log.%Y-%m-%d 86400" combined


To see hostnames in your activity log instead of IP addresses,
let Apache use and log the IP addresses, and resolve them later when analyzing the logfile. Add this to http.conf:

CustomLog /path/to/logs/access_log.raw combined



Please help me customize the apache2 CustomLog.
thank you

---

### Post by alienprdkt on 2008-10-18
where do i put these requests for CustomLog?

---

### Post by alienprdkt on 2008-10-21
anyone know how this may be done?

---

### Post by alienprdkt on 2008-10-21
By default, the standard Apache distribution includes a module called mod_log_ 
config, which is responsible for the basic logging, and it writes CLF log files by 
default. You can alter this behavior using the LogFormatdirective. However, CLF 
covers logging requirements in most environments. The contents of each line in a 
CLF log fileare explained in the paragraphs that follow. 


Where would this file be found if there is no mod_log_ 
config???

---

### Post by pormogo on 2008-12-15
The standard debian package compiled the module into the server, Ubuntu likely does the same thing. For example 

[i]# apache2 -l

Compiled in modules:

  core.c

  mod_log_config.c

  mod_logio.c

  prefork.c

  http_core.c

  mod_so.c

[/i]

---

