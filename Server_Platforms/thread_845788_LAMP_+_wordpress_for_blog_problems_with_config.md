---
title: "LAMP + wordpress for blog problems with config"
date: 2008-06-30
forum: Server Platforms
---

### Post by joe_l on 2008-06-30
Ok, here's the situation. I installed Ubuntu (LAMP install), then proceeded to install wordpress for my blog that I want to setup. Everything went/was kosher, until I made a change that I can not seem to trace for the life of me, and it's bugging the hell out of me b/c I can usually find my mistakes with some careful back-tracking.

Now, on to the problem. When I navigate to the URL of my blog [http://mydomain.net/apache2-default/blog](http://mydomain.net/apache2-default/blog) I get redirected to [http://myinternalserverIP/apache2-default/blog](http://myinternalserverIP/apache2-default/blog)

I can not find which conf file is the cause of this. Can anyone point me in the right direction please? Or, would this be better suited for the WP forums?

---

### Post by dominiquec on 2008-06-30
I believe the file you're looking for is wp-config.php.

---

### Post by joe_l on 2008-06-30
Ok, I think it's fixed now. While testing before going live, I was setup on a different port, thus I had the IP entered instead of my domain.

For others FYI:
under Options
Wordpress address (URL):
and Blog (URL):

make sure those are not IPs

---

### Post by joe_l on 2008-06-30
Alright, now I just need to get rid of [http://mydomain.net/](http://mydomain.net/)**apache2-default**/blog

I would like it to be [http://mydomain.net/blog](http://mydomain.net/blog)

I recently migrated to apache2 and am still getting use to it. What are the necessary steps to accomplish getting rid of **apache2-default**?

---

### Post by dominiquec on 2008-07-01
The simplest way is to install WordPress in the "blog" directory of your web server's root. :-)  (I'm assuming this is a fresh install so no major problems with a reinstallation.)

If you just want to get rid of apache-default without moving any of your files, then you'll have to edit your Apache configuration files.  I think that's a bit more trouble than it's worth.  Anyway...[http://httpd.apache.org/docs/2.2/configuring.html](http://httpd.apache.org/docs/2.2/configuring.html)

---

### Post by joe_l on 2008-07-01
It can't be that hard to make this change. Can anyone tell me what I need to change to get rid of   [http://mydomain.net/](http://mydomain.net/)**apache2-default**/xxx ?

---

### Post by mrpeenut24 on 2008-07-01
Try this:

```

sudo mv /var/www/apache2-default/blog /var/www/blog

```

Then go and edit the config file again.

---

