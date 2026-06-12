---
title: "[SOLVED] HTTPS SSL with Squirrelmail"
date: 2008-06-15
forum: Server Platforms
---

### Post by dash86no on 2008-06-15
Hi,

I have set up a postfix/dovecot/squirrelmail mail server.

At the moment, I'm accessing through [http://mydomain/squirrelmail](http://mydomain/squirrelmail)

I would like to access via [https://mydomain/squirrelmail](https://mydomain/squirrelmail)

Can anybody point me in the right direction? I believe I have a web server capable of SSL because I am accessing Webmin via a HTTPS connection.

PS. I have Ubuntu Hardy server installed with:

Webmin, Apache, Postfix, Squirrell installed, all latest versions as far as I can tell. 

Thanks,

---

### Post by dash86no on 2008-06-15
OK...


So I finally figured out I needed to actually enable SSL in apache. (What was confusing me, was that I was accessing Webmin via HTTPS. It turns out that Webmin is acting as its own SSL enabled web server and apache has nothing to do with it)

Anyway, I followed the guide here: [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

It seemed to go OK, except towards the end I got the errors:

"VirtualHost *:80 -- mixing * ports and non * ports with a NameVirtualHost is not supported, proceeding with undefined results"

"Warn NameVirtualHost *:80 has no virtualHosts"

Both of the above are actually repeated one more time, before the web server appears to come up ok 

I can now access my Webmail ok on http, but when I try to access over HTTPS I get the following error:

ssl_error_rx_record_too_long

Anyone get any ideas?

Cheers,

---

### Post by dash86no on 2008-06-16
OK,

I'm not sure why, but I resolved this issue by simply changing the /etc/apache2/sites-available/default file lines to:

NameVirtualHost *
<VirtualHost *>

and my /etc/apache2/sites-available/ssl file to:


NameVirtualHost *:443
<VirtualHost *:443>

and then restarting apache.

Now SSL seems to be working just fine.

---

