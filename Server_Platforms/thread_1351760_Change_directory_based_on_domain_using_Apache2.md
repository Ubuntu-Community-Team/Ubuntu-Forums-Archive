---
title: "Change directory based on domain using Apache2"
date: 2009-12-10
forum: Server Platforms
---

### Post by PadawanGeek on 2009-12-10
Hi everyone,

I host multiple websites from my server, and I recently had a client who bought their own domain. Basically, when you type their domain, you get /var/www/index.php, rather than /var/www/markmckibbin/index.html, because they can only direct the domain to an IP, not a subdirectory of an IP.

Is there a way that I can configure Apache so that when the server is accessed through their domain ([http://www.markmckibbin.com/](http://www.markmckibbin.com/)) it goes to the directory that I want (/var/www/markmckibbin/), even though their domain points to just the /var/www/ directory.

Thanks!

---

### Post by JonRohan on 2009-12-10
You need to use virtual hosts. 

See: [https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)

---

### Post by Lars Noodén on 2009-12-11
The Apache2 documentation for vhosts also has a tutorial on name-based virtual hosts:
 [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

If you make the old addresses unavailable, please have the courtesy to set up redirects from the old urls.  Usually this can be done with one-to-one mapping, if it's just a matter of having moved the old documents.

 [http://httpd.apache.org/docs/2.2/rewrite/](http://httpd.apache.org/docs/2.2/rewrite/)

Apache's rewrite engine is very, very powerful and flexible.

---

