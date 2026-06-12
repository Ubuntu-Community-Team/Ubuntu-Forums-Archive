---
title: "Apache2 -&gt; .pl and .phtml will download, not show (want sql-ledger to work)"
date: 2006-10-15
forum: Server Platforms
---

### Post by Garyu on 2006-10-15
I installed apache and mysql in order to get sql-ledger running, but I have run into some problems. The guide I followed is this one:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

After installation, apache works fine, I can put files in /var/www/ and they are displayed using [http://localhost/](http://localhost/). I tried putting a "http://localhost/testphp.php" there to run phpinfo() and it displays the information correctly with my server name, Apache 2.0 and also:
```
Registered PHP Streams 	php, file, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
```

The problem is, even after I installed sql-ledger it resides in /usr/lib/sql-ledger/ so I made a link there with something like
```
ln /var/www/sql-ledger /usr/lib/sql-ledger/
```
and in the terminal, if I "cd /var/www/sql-ledger" everything works fine. The permissions on the link is "lrwxrwxrwx". But, when I use Firefox on "http://localhost/sql-ledger/" I get the index.html showing, which wants to load login.pl, but instead of running this script as cgi/perl Firefox opens up a download dialog.

Also, I tried installing phpmyadmin, which automatically creates a link similar to the one I made with sql-ledger, but phpmyadmin uses ".phtml" as extension for the index, and this will also open a download dialog.

So, how do I make Apache run these .pl and .phtml files so I can use sql-ledger and phpmyadmin?

---

### Post by s3ntinel76 on 2006-10-15
**.pl**

Check the file permissions on the .pl file. Does it have execute permission for the apache user? Does the apache user also have read (and possibly also write) permissions for the folder that the file is located in?

**.phtml**

Ensure that php is invoked to interpret the .phtml file - this is set in the apache configuration file.

in /etc/apache2/apache2.conf

```
AddType application/x-httpd-php .php .phtml
```

You might also have to add:
```

# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi
AddHandler cgi-script .pl
```

The apache User and Group are also in the same config file

---

### Post by Garyu on 2006-10-15
All of the files and folders for sql-ledger are owned by "root" and group "root". But they have read and execute rights for everyone, so I don't think user and group should make a difference? My apache user is default (www-data.www-data).

As for phpmyadmin, I can't find any .phtml files, only .php and when I call them directly, they seem to work to some extent. It is when I call [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) that the question pops up "Download .phtml ?"

I edited /etc/apache2/apache2.conf as you said, with
```
[CODE]AddType application/x-httpd-php .php .phtml
AddHandler cgi-script .pl
```
(first line changed from only using .php, second line added)

I still have the same problems.

EDIT: I found [a post on sql-ledger]("http://www.ubuntuforums.org/showthread.php?t=71418&highlight=apache+perl") that I didn't find before, but it deals with installing it on Breezy. Anyhow, I copied this into /etc/apache2/apache2.conf
```
##########################
# SQL-Ledger
##########################
Alias /sql-ledger /usr/lib/sql-ledger/
<Directory /usr/lib/sql-ledger>
  AllowOverride All
  AddHandler cgi-script .pl
  AddDefaultCharset On
  Options ExecCGI Includes FollowSymlinks
  Order Allow,Deny
  Allow from All
</Directory>

<Directory /usr/lib/sql-ledger/users>
  Order Deny,Allow
  Deny from All
</Directory>
##########################
```
Then I removed the symbolic link. This makes apache2 the one to handle all of the redirects rather than the file system, so it should be the better solution. BUT, I still get the same question for downloading the .pl file... *sigh* ](*,)

---

### Post by s3ntinel76 on 2006-10-15
Sorry - probably obvious, you have restarted apache?

---

### Post by Garyu on 2006-10-15
> **s3ntinel76 said:**
> Sorry - probably obvious, you have restarted apache?

yup, a number of times. but I finally got it to work. I found an installation instruction on sql-ledger that said I have to use PostgreSQL, not MySQL, and run the /sql-ledger/admin.pl which actually worked fine. So after I did that, the login.pl changed from downloading to running on the server. I guess I deserve a "RTFM" after that, but I'm so used to having things work after installing from Synaptic so I didn't go through all of the manuals properly.

For some reason, phpmyadmin works as well. What I did was to close down Firefox. Even though I used the "F5"/"Update page" it wouldn't load properly, but after a Firefox restart, everything works fine. Maybe this affected the .pl download-thing as well, I'm not sure. 

In any case, things are working now. Thank you for your help. :)

If I find the time I think I will try to reinstall all of this on my other computer and try to compose a howto, because I have found a lot of threads on this and other forums about this issue (or similar ones) and not very many answers. So a step-by-step solution should be well needed. After all, accounting software is one of the weak points of any linux install, and having sql-ledger working is a very good thing for small business installations. :cool:

---

