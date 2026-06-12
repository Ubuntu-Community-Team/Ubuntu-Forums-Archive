---
title: "LAMP problems"
date: 2008-08-06
forum: Server Platforms
---

### Post by jasonwipos on 2008-08-06
Hi guys,
Bit of a weird one. After having a bit of a accident I removed nearly everything, including my nicely set up LAMP. After spending quite a while reinstalling everything I have got everything just about working except...

PHP files in...

/var/www

just comes out as the plain text when you open them in a browser

But...

phpmyadmin works fine.

Any ideas?

Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Server at server Port 80 

Is my configuration.

---

### Post by kihjin on 2008-08-06
Phpmyadmin isn't installed under /var/www ?

Check your httpd.conf, make sure it has

AddType application/x-httpd-php .php

If your php scripts don't end in .php, either change the scripts or change the argument.

---

### Post by jasonwipos on 2008-08-07
Thanks for your reply.

It was something to do with AddType. From cutting and pasting from various 'configure PHP for apache' tutorials I had managed to somehow end up with 

AddType text/html .php

After the 

AddType application/x-httpd-php .php

line, which struck me as odd, so I deleted it and it worked.

---

