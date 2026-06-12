---
title: "Nginx + php-fpm problem with running CGI scripts"
date: 2012-08-04
forum: Server Platforms
---

### Post by Jonakoudijs on 2012-08-04
I am installing a specialized server for an admin panel I am building. It has the following software:

Ubuntu 12.04
Nginx 1.1.19
PHP 5 FPM
Nagios 3

The admin panel is built on Nginx (performance and ease of configuration). Now I am trying to integrate nagios monitoring into the admin panel. The problem is that I am now finding out that cgi scripts don't work on this server. PHP / MySQL etc. work fine.
I tested it with a simple test script and it also didn't work. The browsers always returns: Access denied.
The Access log file just shows [GET] with the 403 error. The Error Log doesn't show anything. Has anyone an idea where I can look?

Oh and I have execute permissions on all the folder levels (/ , /www ,  /www/cgi-bin etc.).

---

### Post by Jonakoudijs on 2012-08-06
I found out that I didn't have any CGI wrappers installed. I followed this guide: [http://www.howtoforge.com/serving-cgi-scripts-with-nginx-on-debian-squeeze-ubuntu-11.04-p3](http://www.howtoforge.com/serving-cgi-scripts-with-nginx-on-debian-squeeze-ubuntu-11.04-p3)

And it works flawless!

---

