---
title: "Apache Overlap error"
date: 2009-03-01
forum: Server Platforms
---

### Post by LOG123 on 2009-03-01
so i was trying to reload APACHE2 today because it was acting strange and i got this error:
> sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] VirtualHost 192.168.2.8:80 overlaps with VirtualHost 192.168.2.8:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Sun Mar 01 13:48:53 2009] [warn] NameVirtualHost 192.168.2.4:80 has no VirtualHosts
   ...done.

---

### Post by etali on 2009-03-01
What sites do you have configured?

Could you post the contents of your apache2.conf / any sites defined in the /sites-available folder.

---

### Post by LOG123 on 2009-03-09
Now i'm getting 404's and with some websites its "application/x-phpd" and the option to download:confused:

---

### Post by schmoo2x on 2009-03-09
Sounds like you've got a Virtual Host problem in your apache config. Run this and copy the results in here: 
sudo cat /etc/apache2/apache2.conf

also,
ls /etc/apache2/sites-available/
Then we can see what is going on over there! :)

---

### Post by LOG123 on 2009-03-09
This is the Log Files:
[http://pastebin.com/m32a943b3](http://pastebin.com/m32a943b3)

---

### Post by volkswagner on 2009-03-10
Without seeing your vhost files I assume you have all host files started with the following.

<VirtualHost 192.168.2.8:80>

If this is true you should change them all to 

<VirtualHost *>

When you specify an IP or port, Apache does not want identical entries.  This is where the overlap error comes from.  IP directive is for use with multiple IP addresses for a single server or multiple virtual servers.

Also add the following to httpd.conf

```
NameVirtualHost *

```

---

### Post by LOG123 on 2009-03-10
whoops page wouldn't reload I TAKE BACK THAT BUMP

---

### Post by LOG123 on 2009-03-10
now i get this:
```
 :
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using earthzon.com for ServerName
[Tue Mar 10 19:49:42 2009] [warn] NameVirtualHost 192.168.2.4:80 has no VirtualHosts
[Tue Mar 10 19:49:42 2009] [warn] NameVirtualHost *:0 has no VirtualHosts
   ...done.


```

---

### Post by LOG123 on 2009-03-10
*bump* COME ON MY BOSS IS GETTING MAD.:mad:

---

### Post by volkswagner on 2009-03-10
> **LOG123 said:**
> *bump* COME ON MY BOSS IS GETTING MAD.:mad:


Since you have several vhosts, you should disable all but one then enable one at a time to find the faulty file.

---

### Post by LOG123 on 2009-03-10
how do i disable them?

---

### Post by volkswagner on 2009-03-10
I guess the first question would be are they enabled?  The following will list the site configs for enabled sites.

```
ls /etc/apache2/sites-enabled
```

From the list yielded from the above, insert each file name like the following...

Apache2 disable site:
```
sudo a2dissite earthzon.biz.conf
```


Once you disable all the sites but one restart apache.

```
sudo /etc/init.d/apache2 reload
```

Then enable one at a time while restarting apache after each.

Apache2 enable site:
```
sudo a2ensite earthzon.biz.conf
```

```
sudo /etc/init.d/apache2 reload
```

---

### Post by LOG123 on 2009-03-11
didnt work ._.

---

### Post by volkswagner on 2009-03-12
> **LOG123 said:**
> didnt work ._.

You still had the overlap error with only one host enabled?  All nine errors?

Do you have any config files in /etc/apache2/conf.d?

```
ls -alt /etc/apache2/conf.d

```

The more descriptive you are the more folks can help.  ;)

---

### Post by LOG123 on 2009-03-14
i'm not getting the overlap error anymore, but when I run your command it says:
```
total 12
drwxr-xr-x 7 root root 4096 2009-03-11 14:46 ..
drwxr-xr-x 2 root root 4096 2009-03-11 14:37 .
-rw-r--r-- 1 root root  269 2008-06-25 09:49 charset
```
and when i run start apache from webmin it says:
```
Failed to start apache :

 :
 * Starting web server apache2
   ...done.

```

---

### Post by volkswagner on 2009-03-14
Post your apache log files.

```
cat /var/log/apache2/error.log
```

What is in sites enabled at the moment?

```
ls -alt /etc/apache2/sites-enabled
```

---

### Post by LOG123 on 2009-03-14
when i run cat /var/log/apache2/error.log i get this:
[http://pastebin.com/d46924ab5](http://pastebin.com/d46924ab5)
and when i run ls -alt /etc/apache2/sites-enabled i get :
[http://pastebin.com/d207cbb6d](http://pastebin.com/d207cbb6d)

---

### Post by volkswagner on 2009-03-14
You have many sites.  One of the sites may have errors in configuration of their respective files.

Again, you will need to disable all but the simplest site.  Hopefully you have a basic html simple site for testing or even the default.  Then reload or start apache to see if it is related to an internal problem with an existing site.  It may not be an apache problem.

Without knowing what types of sites are installed it is difficult to say.

Googling the error yields several starting points.

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/msql.so' - /usr/lib/php5/20060613+lfs/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

What types of sites do you have installed?  One search mentioned gallery2.

---

### Post by LOG123 on 2009-03-14
all the sites i have are Magento/Joomla no basic HTML

---

### Post by volkswagner on 2009-03-14
You will need to hunt down the error message.  

My guess is apache is fine. 

Again for troubleshooting purposes you should follow my above instructions.  This will tell you if it is a Magento/Joomla problem or an apache problem.

EDIT: It can also help identify if it is all or just one site.

I am not at all familiar with Magento/Joomla.

---

