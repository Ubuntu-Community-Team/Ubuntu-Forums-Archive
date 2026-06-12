---
title: "ubuntu server + apache question"
date: 2015-03-23
forum: Server Platforms
---

### Post by Mepiis on 2015-03-23
Hello everyone,

Running ubuntu server 14.04 with webmin 1.720 installed as well as apache, mysql and php.  I have this box name xyz.abc.local on my network.  I have the default web site up and running, installed wordpress and it is working.  I created a virtual host, created the directory in /var/www/example-test, chmod permissions to 755.  No matter what I do, I cannot browse to xyz.abc.local/example-test/index.html.  I have made an error somewhere but I am not sure where.  I was thinking I could create the example-test dir and simply browse to it after setting up the virtual host. I am trying to browse to the server from a box connected to the LAN. Please let me know if you need some more information and thanks for your time and help.

---

### Post by Lars Noodén on 2015-03-23
If you're using the default vhost settings for Apache2 then the [DocumentRoot](http://httpd.apache.org/docs/2.4/mod/core.html#documentroot) is /var/www/html/ instead of /var/www/  

So to find your directory via the browser you'd need to move it to where the web server can find it: /var/www/html/example-test/

---

### Post by Mepiis on 2015-03-23
> **Lars Noodén said:**
> If you're using the default vhost settings for Apache2 then the [DocumentRoot]("http://httpd.apache.org/docs/2.4/mod/core.html#documentroot") is /var/www/html/ instead of /var/www/  

So to find your directory via the browser you'd need to move it to where the web server can find it: /var/www/html/example-test/

Thank you very much, did the trick!  Really appreciate the quick help, love the linux community, always helpful!

---

