---
title: "Where is php config file ?"
date: 2009-10-03
forum: Server Platforms
---

### Post by xx77aBs on 2009-10-03
Hello ! I have successfully installed lighttpd, php-cgi and php-gd module and everything is working great :)

But I'm a little bit curious, where are php settings stored ?
I've looked into /etc/php5/cgi/php.ini and /etc/php5/cli/php.ini, but I can't find a referece to php-gd module that I've installed ...

Can you tell me where I can find part that tells php to load php-gd module ??

Thanks :)

---

### Post by R.Bucky on 2009-10-04
It is here: /etc/php5/apache2/conf.d/gd.ini
Your php settings are in /etc/php5/apache2/php.ini

---

### Post by xx77aBs on 2009-10-05
I don't have apache installed (I have lighttpd), so I don't have that folder ...

But you've helped me to find it, thanks :)

It's located in /etc/php5/conf.d/

:)

---

