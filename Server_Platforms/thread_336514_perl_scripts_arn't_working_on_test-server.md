---
title: "perl scripts arn't working on test-server"
date: 2007-01-11
forum: Server Platforms
---

### Post by poadshaw on 2007-01-11
hi gang,

I cannot seem to get perl scripts to run on my newly setup test server.  I got apache2 php5 and mySql running ok.  I have made a cgi-bin folder in /var/www/ but when I visit [http://localhost/cgi-bin/](http://localhost/cgi-bin/) in my browser, I get "forbiden You don't have permission to access /cgi-bin/ on this server."

I added these lines to my /etc/apache2/apache2.conf file

<Directory /var/www>
	ExecCGI
</Directory>

Here are my permissions in /var/www/
$ ls -l
total 44
drwxr-xr-x 2 root     root 4096 2007-01-11 13:31 apache2-default
drwxrwxrwx 2 phil     phil 4096 2007-01-11 15:13 cgi-bin
drwxr-xr-x 6 www-data root 4096 2007-01-11 14:10 feeds
-rw------- 1 phil     phil 5250 2007-01-11 15:27 links.htm
lrwxrwxrwx 1 root     root   21 2007-01-11 14:05 phpmyadmin -> /usr/share/phpmyadmin
-rw-r--r-- 1 phil     phil 4473 2007-01-11 15:27 shaw.htm
-rw-r--r-- 1 phil     phil 2566 2007-01-11 15:27 Style.css
-rw-r--r-- 1 root     root   20 2007-01-11 14:02 testphp.php
-rwxr-xr-x 1 phil     phil  195 2007-01-11 16:14 testpl.pl
-rw-r--r-- 1 phil     phil 1179 2007-01-11 15:27 time.js


Here are my permissions in /var/www/cgi-bin/
$ ls
testhtml.pl
phil@phil-laptop:/var/www/cgi-bin$ ls -l
total 4
-rwxrwxrwx 1 phil phil 195 2007-01-11 14:21 testhtml.pl



typing [http://localhost/cgi-bin/testhtml.pl](http://localhost/cgi-bin/testhtml.pl) in the browser yields
"not found The requested URL /cgi-bin/testhtml.pl was not found on this server."



I can't figure this out.  Anyone know what I am missing?  I'll supply any additional info if needed.  I am still pretty new to ubuntu but loving it so far!!!!

---

### Post by geek_Man on 2007-02-11
I have Apache on Windows so it might be a little different, but... Unless you have cgi-bin in htdocs, there should be a line in your apache2.conf file saying that /cgi-bin/ actually points to /var/cgi-bin or where ever it is. Cgi-bin also has to be accessible to everyone. I have to say that I haven't messed with Apache for a while so I can't give really specific directions.

---

