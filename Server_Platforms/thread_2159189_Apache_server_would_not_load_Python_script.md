---
title: "Apache server would not load Python script"
date: 2013-07-02
forum: Server Platforms
---

### Post by Snitz on 2013-07-02
Hello,

I installed Apache server, php and mysql on my Ubuntu 12.04 x86
if you goto [http://37.139.4.232](http://37.139.4.232) it says 'it Works' and PHP works as well [http://37.139.4.232/phpinfo.php](http://37.139.4.232/phpinfo.php)
Which is fine.

I then installed Reddit script which uses Python and Postgres in /var/www/maghnatis

Now whenever I navigate to [http://37.139.4.232/maghnatis](http://37.139.4.232/maghnatis)
I get a directory list. It would not load the site.

What should I do?

---

### Post by DJ_Max on 2013-07-02
If the root directory for the script is /var/www/maghnatis, than localhost/maghnatis will look for /var/www/maghnatis/maghnatis

You've given no indication of an issue aside from you saying it doesn't load. What is the error message, what do your logs say? What version of Python and what module are you using?

---

### Post by SeijiSensei on 2013-07-02
If there is no "index" file in /var/www/maghnatis, like an index.php or index.html, then you will get a directory listing (depending on the Options specified in the configuration file for the site).  Apparently whatever installation script you ran put the index file in some other location.

---

### Post by Snitz on 2013-07-03
I checked the installation script and I can't seem to find an index anywhere.
[https://github.com/reddit/reddit](https://github.com/reddit/reddit)

---

### Post by DJ_Max on 2013-07-03
There is no index file necessarily when using Python.

Post your httpd.conf

---

