---
title: "public_html works locally but not from another machine"
date: 2007-05-19
forum: Server Platforms
---

### Post by Permafrost91 on 2007-05-19
My laptop is set up with Apache so that I can develop websites within my public_html folder and preview them locally. This works all fine and dandy, just the way I like it (including PHP). All websites I work on are subfolders of public_html so I access site XYZ with localhost/~user/XYZ. Locally, this works.

However, I don't run Windows (obviously) but I need IE to test my sites. Usually ies4linux works alright but lately IE6 is having some weird formatting issues (even weirder than IE6 on Windows). So I want to access my sites from the IE on my other computer (same local network). I can access my public_html folder just fine it seems: all the subdirectories show up in the remote browser window, but I cannot get into any subdirectories (and hence, websites).

What's the deal? How come I have access to my public_html folder from another machine but not to any subfolders within it?

Any help would be greatly appreciated! Thanks!

P.S.: This is the latest Feisty.

---

### Post by mbradlcu on 2007-05-22
I'm able to brows subdirs from ~/www/
here's the relative section in my /etc/apache2/apache2.conf

UserDir www
UserDir disabled root
<Directory /home/*/www>
    AllowOverride FileInfo AuthConfig Limit
    Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

here's the perms on those directories found in my ~/www

drwxr-xr-x  6 satch satch  4096 2007-05-21 20:51 .
drwxr-xr-x 43 satch satch  4096 2007-05-21 22:49 ..
drwxr-xr-x  3 satch satch  4096 2007-04-17 17:16 Astro
drwxr-xr-x  2 root  root   4096 2006-12-05 16:46 dci
-rw-r--r--  1 satch satch 93208 2005-01-27 05:37 libart_lgpl_2.so.2.3.17
drwxr-xr-x  4 satch satch  4096 2007-04-25 23:40 Music
drwxr-xr-x  7 satch satch  4096 2007-05-04 16:38 PHPscripts
-rw-r--r--  1 satch satch 68700 2007-05-21 11:47 pix2.png
-rw-r--r--  1 satch satch 79213 2007-05-21 11:47 pix3.png

note, dir dci isn't accessible.

if you haven't already I would do a:
```
tail -f /var/log/apache2/auth.log
```
and see what you get when trying to connect from an outside box.

---

### Post by Permafrost91 on 2007-05-22
Thanks, mbradlcu. My /etc/apache2/mods-enabled/userdir.conf looks the same. Also, permissions are the same (I even tried setting permissions to 777).

Looking at through the logs, it seems that people get 302 errors for subdirs.

Thanks for your help!

---

### Post by mbradlcu on 2007-05-22
you may already know about 302 errors but I didn't so here's the best explanation I found:
> 		
Code 302 Redirected requests result whenever you specify a directory for a URL. For example, if you specify:
[http://www.he.net/~rflyer](http://www.he.net/~rflyer)
the server redirects the browser to request:
[http://www.he.net/~flyer/index.html](http://www.he.net/~flyer/index.html)
The server handles the redirection in this manner in conformance with HTTP standards. It is quite normal. 

so if you created a index.html in a subdir would it be displayed?,,, I guess the real mystery is why it's working fine when looking at the dirs locally..

---

### Post by Permafrost91 on 2007-05-26
That's just it, there are index.php files in those subdirs, which are displayed (and further subdirs as well) locally, just not when I look at them from other computers on my local network ...

---

### Post by mbradlcu on 2007-05-27
sorry I don't have an answer but  does the /var/log/apache2/access.log&error.log show anything interesting when trying to connect from your lan

---

### Post by Permafrost91 on 2007-05-27
Here's the output in apache.log I just got after trying to access a subfolder on my machine from another machine's internet explorer:

```
192.168.1.100 - - [27/May/2007:14:23:06 -0400] "GET /~user/subdir/ HTTP/1.1" 301 330 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; InfoPath.1)"
192.168.1.100 - - [27/May/2007:14:23:06 -0400] "GET /~user/subdir/ HTTP/1.1" 302 - "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; InfoPath.1)"
```

---

### Post by Permafrost91 on 2007-05-27
I just discovered that PHP is somehow the culprit ... PHP files are not executed remotely, only when I access them locally. So, how can I fix that?

---

### Post by mbradlcu on 2007-05-29
check for this line in your /etc/apache2/apache2.conf:
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
and maybe un-comment out this line:
#AddType application/x-httpd-php .php

I futzed with my apache2.conf a lot so I'm not sure if this is a stock line or I added index.php

Please let me know if this fixes it or if you find a fix, this is one of those funky problems that could eat a lot of time.

---

