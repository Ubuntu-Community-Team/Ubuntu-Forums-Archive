---
title: "Apache died after an update with apt (LTS 14.04)"
date: 2015-03-01
forum: Server Platforms
---

### Post by Pépou on 2015-03-01
Hi all,

I run ubuntu 14.04 LTS server
I just did an upgrade with apt-get dist-pgrade

Then, after restart, apache2 refuses to start... :(

```
pepou@sd-...:~$ sudo service apache2 start
 * Starting web server apache2                                                   * 
 * The apache2 configtest failed.
Output of config test was:
apache2: Syntax error on line 140 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: symbol xmlOutputBufferGetSize, version LIBXML2_2.9.0 not defined in file libxml2.so.2 with link time reference
Action 'configtest' failed.
The Apache error log may have more information.
```

Please any help is very welcome...!

Thank you in advance

---

### Post by Tom_Jefferson on 2015-03-01
Does Apache with the indicated line commented start up?
Have you tried removing and purging PHP/Apache + PHP stack (just be aware that the configuration directories should AFAIR empty or at least not modified if apt-get --purge remove package is to be successful - so move your configuration files to another, safe directory)? What is on this subject in the mentioned error log? Can you give the full output of the command:

apachectl configtest

if there's anything more than what you quoted?

---

### Post by Pépou on 2015-03-02
Thank you for your answer.
Here is the full output of the command line you :
> apache2: Syntax error on line 140 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: symbol xmlOutputBufferGetSize, version LIBXML2_2.9.0 not defined in file libxml2.so.2 with link time reference
Action 'configtest' failed.
The Apache error log may have more information.

---

### Post by Pépou on 2015-03-02
> **Tom_Jefferson said:**
> Have you tried removing and purging PHP/Apache + PHP stack (just be aware that the configuration directories should AFAIR empty or at least not modified if apt-get --purge remove package is to be successful - so move your configuration files to another, safe directory)?
I tried this, but didn't solve the problem. I still have the same error message.. :(

---

### Post by Habitual on 2015-03-02
open a terminal > 
```
sudo a2dismod php5
service apache2 restart
a2enmod php5
service apache2 restart
sudo -k

``` Please post any informational messages back here.

---

