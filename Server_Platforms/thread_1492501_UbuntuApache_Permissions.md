---
title: "Ubuntu/Apache Permissions"
date: 2010-05-24
forum: Server Platforms
---

### Post by cisco_kid0708 on 2010-05-24
Hi,
 
I am trying to learn Linux System Administration. I am sure that there may be another thread or forum that already has the answer to my problem(s), but I am not finding it.
 
I have Ubuntu Server version 9.10 setup with an Apache Server. I have NOT changed any user permissions nor have I changed any of the configurations of Apache. The Apache will work fine until I add an html file to the default Document Root of "/var/www", then when I try to access the newly added html file I get a 403 permissions denied error. For example, when I try [http://server/test.html](http://server/test.html), I get this error.
 
I added my user to the www-data group.
 
I looked at the file permissions using "ls -l" and the file permissions for the newly added file is:
Read and Write only for the owner which is www-data and every user in the www-data group, but no permissions for anyone else
 
I can add another file to the directory, and it too will get the same permissions.
 
I have tried to added sticky flag permissions, but it doesn't work.
 
I would appreciate any help!!
 
Thanks!

---

### Post by terazen on 2010-05-25
Is there anything in /var/log/apache2/error.log or /var/log/apache2/access.log concerning test.html when you try and view the page?

---

### Post by cisco_kid0708 on 2010-05-25
I apologize for this, but I had no idea about log files or their locations.   I will check the specified logs, and will reply ASAP.

Thank you!!!

---

### Post by cisco_kid0708 on 2010-05-25
Ok  I have checked /var/log/apache2/error.log, and the following are the errors found in the log.

Directory index forbidden by Options directive: /var/www/

and

(13)Permission denied: file permissions deny server access: /var/www/

( Of course there are errors about File does not exist: /var/www/favicon.ico), but I haven't made an favicon yet, much less any image files, etc.

I have also check /var/log/apache2/access.log, and the following is found in the log and they are request sent from my computer to the Apache Server.  The 403 errors are from any newly added files to the /var/www/ folder, and the permitted access is only to the index.html that comes default with Apache.  In order to access any other files, I must change permissions manually.

"GET /test.html HTTP/1.1" 200 415 "-" "Mozilla/4.0 (c$

"GET /test2.html HTTP/1.1" 200 415 "-" "Mozilla/4.0 ($

"GET / HTTP/1.1" 200 512 "-" "Mozilla/4.0 (compatible$

"GET / HTTP/1.1" 304 208 "-" "Mozilla/5.0 (X11; U; Li$

"GET / HTTP/1.1" 403 505 "-" "Mozilla/5.0 (Windows; U$

"GET / HTTP/1.1" 403 499 "-" "Mozilla/5.0 (Windows; U$


Yes, I know this is confusing, but I don't know what to do.

Thanks!!

---

### Post by terazen on 2010-05-25
> Directory index forbidden by Options directive: /var/www/
This is referring to your site file.  Can you `cat /etc/apache2/sites-enabled/*`?

Please return the output of `ls -la /var/www` and `ps -eaf | grep apache`.

---

### Post by cisco_kid0708 on 2010-05-25
here is "la -la /var/www"

drwxr-sr-x  5 jordan jordan 4096 2010-05-24 18:51 .
drwxr-xr-x 15 root   root   4096 2010-05-14 22:45 ..
drwxr-xr-x  2 jordan jordan 4096 2010-05-24 17:51 backups
-rwxr-xr-x  1 jordan jordan  278 2010-05-24 17:51 fileupload.html
-rwxr-xr-x  1 jordan jordan  432 2010-05-24 17:51 fileupload.php
-rwxr-xr-x  1 jordan jordan  267 2010-05-24 18:50 fp.html
-rwxr-xr-x  1 jordan jordan  230 2010-05-24 17:51 index.html
-rwxr-xr-x  1 jordan jordan   97 2010-05-24 17:51 index.php
drwxr-xr-x  2 jordan jordan 4096 2010-05-24 17:51 Pictures
drwxr-xr-x  2 jordan jordan 4096 2010-05-24 16:40 public_html
-rwxr-xr-x  1 jordan jordan  390 2010-05-24 17:51 stylesheet.css
-rw-------  1 jordan jordan   95 2010-05-24 18:51 test2.html
-rwxr-xr-x  1 jordan jordan   95 2010-05-24 18:37 test.html
-rwxr-xr-x  1 jordan jordan   30 2010-05-24 18:36 test.php
-rwxr-xr-x  1 jordan jordan  883 2010-05-24 18:20 upload_file.php
-rwxr-xr-x  1 jordan jordan 1366 2010-05-24 17:51 upload.form.php
-rwxr-xr-x  1 jordan jordan 3316 2010-05-24 17:51 upload.processor.php
-rwxr-xr-x  1 jordan jordan  519 2010-05-24 17:51 upload.success.php


Here is "ps -eaf | grep apache"

root      1237     1  0 May24 ?        00:00:02 /usr/sbin/apache2 -k start
jordan    1259  1237  0 May24 ?        00:00:00 /usr/sbin/apache2 -k start
jordan    1260  1237  0 May24 ?        00:00:00 /usr/sbin/apache2 -k start
jordan    1261  1237  0 May24 ?        00:00:00 /usr/sbin/apache2 -k start
jordan    1262  1237  0 May24 ?        00:00:00 /usr/sbin/apache2 -k start
jordan    1263  1237  0 May24 ?        00:00:00 /usr/sbin/apache2 -k start
jordan    2127  2106  0 09:42 pts/0    00:00:00 grep --color=auto apache


I apologize, but I also changed the user that Apache runs under to "jordan" to see if it would fix the issue.

---

### Post by terazen on 2010-05-25
I'd change the user back and run `sudo chown -R www-data:www-data /var/www` to reset permissions.  What's the output of `cat /etc/apache2/sites-enabled/*`?  Do you have the Indexes option set?  Somewhere in the file it should have something like this:

>        [B] <Directory /var/www/>
                Options Indexes[/B] FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

---

### Post by cisco_kid0708 on 2010-05-25
> 
[B]<Directory /var/www/>
                Options Indexes[/B] FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory> 			 		


I did everything that you said, and also changed the AllowOverride back to None

---

### Post by cisco_kid0708 on 2010-05-25
I applied all changes, and restarted the whole server.

The www-data is the new owner, but I cannot add files.  Also, the test2.html is still having the same file permissions applied to it.  -rw-------   1 www-data www-data

---

### Post by terazen on 2010-05-27
Hrmm, all I can think of would be to backup your files from /var/www to somewhere else, then do a `sudo apt-get purge apache2` and `sudo apt-get install apache2`.  The default configuration of apache should just require www-data to have read privileges to the files.

When you want to edit a file, like apache2.conf or anything in your /etc/apache2/sites-available you should always make a backup.  Personally I have always added .bak to the end of all my filenames. (sudo cp apache2.conf apache2.conf.bak...)  Then you can edit your file and if you break something, it's easy to revert to the old configuration.

---

