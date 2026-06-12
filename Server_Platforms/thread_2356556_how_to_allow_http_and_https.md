---
title: "how to allow http and https"
date: 2017-03-24
forum: Server Platforms
---

### Post by monster-it on 2017-03-24
Hi Guys,

I'm still learning Linux after years of being molly cuddled by Windows easy to use GUI I thought command line was the better more powerful tool seeing Microsoft has gone down hill now and always been a fan for gaming with linux servers so I'm creating a webserver I've already got a domain working with port 80 but I need to get a new site with port 80 and 443.

Here is my virtual host file any help would be great.

```
<VirtualHost *:80>
ServerAdmin helpme@monster-it.co.uk
DocumentRoot /var/www/html/beckysboutiques/public_html/
ServerName beckysboutiques.com
ServerAlias www.beckysboutiques.com
<Directory /var/www/html/beckysboutiques/>
Options FollowSymLinks
AllowOverride All
Order allow,deny
allow from all
</Directory>
ErrorLog /var/log/apache2/beckysboutiques.com-error_log
CustomLog /var/log/apache2/backysboutiques.com-access_log common
</VirtualHost>

```

---

### Post by TheFu on 2017-03-24
Usually people setup a port 80 redirector to https on 443.  Lots and lots of how-tos for that.  If you use Let's Encrypt" for the cert, then you don't need to buy any certs.

So, exactly, what is the specific question?  What have you tried that didn't work?

---

### Post by monster-it on 2017-03-24
what should my .conf file look like.

---

### Post by TheFu on 2017-03-24
> **monster-it said:**
> what should my .conf file look like.

Google found this: [https://wiki.apache.org/httpd/RedirectSSL](https://wiki.apache.org/httpd/RedirectSSL)
and
[https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)

If you don't make the effort, how will you learn?

---

### Post by monster-it on 2017-03-24
Yeah i've gone through the tutorial's about 6 times and i keep breaking the %$£"£$ server each time :(

---

### Post by TheFu on 2017-03-24
And what are the error messages that go with the changes you've made?

Use a test setup if you can't screw with the production system. That should go without saying.

Also, you need to use the apache how-tos for the version you are actually running. Hard for anyone to help without that data - or what you are trying to accomplish. Is this a webapp? Is there a DB? Is this just a static site?  It is self-hosted or on some hosting provider?  Is is a VPS and you have root?

Hard to help without a little background.

"show me how" isn't a good question. Show your work. Show the log failures. It could be permissions. Can't tell anything from "it doesn't work" answers.

---

### Post by monster-it on 2017-03-24
Yeah, the test system just roots to the main index folder page. it for some reason does not forward to the actual /var/www/html/user1/public_html folder just to /var/www/html.

---

