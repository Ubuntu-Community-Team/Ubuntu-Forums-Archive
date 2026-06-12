---
title: "Php server not getting permissopb tp acces files"
date: 2011-11-09
forum: Server Platforms
---

### Post by shubham1 on 2011-11-09
First up I will like to clear that by this I do nOt mean I cant creare files I mean php server says permission denied when creTinv or fopen files/folder i am posting via mobile as my pc is not getting net problem so please i mean web server

---

### Post by vasile002 on 2011-11-09
it depends on how you run php on your webserver. Check the file and folder permissions

---

### Post by shubham1 on 2011-11-10
> **vasile002 said:**
> it depends on how you run php on your webserver. Check the file and folder permissions

how to check i cant find

---

### Post by shubham1 on 2011-11-16
please reply back any one

---

### Post by shubham1 on 2011-11-18
no one

---

### Post by Jonathan L on 2011-11-18
> **vasile002 said:**
> it depends on how you run php on your webserver. Check the file and folder permissions

Hi Shubham

Do you have shell access to your web server and can run commands?

If so, run these and post the results back here.
```

ls -l /var/www
fgrep APACHE_RUN_ /etc/apache2/*
```What directory are you wanting read/write files in?  Please also do
```
ls -ld /that/directory
```Kind regards,
Jonathan

---

### Post by shubham1 on 2011-11-18
/etc/apache2/apache2.conf:User ${APACHE_RUN_USER}
/etc/apache2/apache2.conf:Group ${APACHE_RUN_GROUP}
/etc/apache2/envvars:export APACHE_RUN_USER=www-data
/etc/apache2/envvars:export APACHE_RUN_GROUP=www-data
/etc/apache2/envvars:export APACHE_RUN_DIR=/var/run/apache2$SUFFIX[/CODE]

---

### Post by shubham1 on 2011-11-18
drwxrwxrwx 16 www-data www-data 12288 2011-11-10 12:15 /var/www/

---

### Post by Jonathan L on 2011-11-18
> **shubham1 said:**
> drwxrwxrwx 16 www-data www-data 12288 2011-11-10 12:15 /var/www/

Hi Shubham

Seems like you've got it very open indeed! And have lots of unecessary permissions.  Files in /var/www should really be 664 at most.  You also have a lot of things in there which you probably don't want the world to see, like your backups and what not.  I'd advise some caution!

Please can you edit your post to remove the long list of files?  You shouldn't advertise all that.  Thanks!

Back to what you asked help for:

Could you be explicit about where you're trying to write, and the log file message you get?

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2011-11-18
Are you sure your application is writing the files to /var/www and not somewhere else?  Can you post the error you get from /var/log/apache2/error.log?

---

### Post by shubham1 on 2011-11-19
yes
sorry the file contents are big and ubuntu server cant process them and take over 60 seconds
**Fatal error**:  Maximum execution time of 60 seconds exceeded in **/srv/www.ubuntuforums.org/public_html/includes/functions.php** on line **1838**

---

### Post by SeijiSensei on 2011-11-19
[http://davidwalsh.name/increase-php-script-execution-time-limit-ini_set](http://davidwalsh.name/increase-php-script-execution-time-limit-ini_set)

---

### Post by shubham1 on 2011-11-19
This you shpuld tell to ubuntu forums devloper as this happened in their servers you have got it wrong :)

---

### Post by shubham1 on 2011-11-20
what is the solution

---

### Post by Jonathan L on 2011-11-20
Hi Shubham

You'll need to post at least the tail of the log so we can see what  error message you've got.  Otherwise we really have got no way to help  you find your solution.

Kind regards,
Jonathan.

---

### Post by shubham1 on 2011-11-21
> **Jonathan L said:**
> Hi Shubham

You'll need to post at least the tail of the log so we can see what error message you've got.  Otherwise we really have got no way to help you find your solution.

Kind regards,
Jonathan.
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/imap.so' - /usr/lib/php5/20090626/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/suhosin.so' - /usr/lib/php5/20090626/suhosin.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun Nov 20 11:13:17 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/imap.so' - /usr/lib/php5/20090626/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/suhosin.so' - /usr/lib/php5/20090626/suhosin.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun Nov 20 18:26:42 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Nov 20 18:27:48 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: http://localhost/resource/projects/dir/dir.php
```

---

### Post by Jonathan L on 2011-11-21
Hi Shubham

I did actually mean the error message for the problem you asked for help on!
> php server says permission denied1.  What file are you trying to create, in what directory?
2.  What error message do you get?

It's not possible to help without the basic information.

Kind regards,
Jonathan.

---

### Post by shubham1 on 2011-11-21
dirs and files txt
error:
Warning: mkdir(): Permission denied in /var/www/lamp/9.php on line 2 
;

---

### Post by Jonathan L on 2011-11-21
Hi again Shubham

> Warning: mkdir(): Permission denied in /var/www/lamp/9.php on line 2 
;Good.  Now: what directory are you trying to make?

Kind regards,
Jonathan.

---

### Post by shubham1 on 2011-11-22
> **Jonathan L said:**
> Hi again Shubham

Good.  Now: what directory are you trying to make?

Kind regards,
Jonathan.
dir name:"hello"

---

### Post by Jonathan L on 2011-11-22
> **shubham1 said:**
> dir name:"hello"

Yes shubham, and where are you trying to make it?

Kind regards,
Jonathan.

---

### Post by shubham1 on 2011-11-23
> **Jonathan L said:**
> Yes shubham, and where are you trying to make it?

Kind regards,
Jonathan.
in /var/www/lamp/

---

### Post by shubham1 on 2011-11-23
> **shubham1 said:**
> in /var/www/lamp/
i jsut did this
set /var/www/ chmod to 777 -R
and chown // change the user name
to shubham and i was able to create a dir "hi" in /var/www/resource/projects/dir/dir.php

---

### Post by shubham1 on 2011-11-23
i jsut did this
set /var/www/ chmod to 777 -R
and chown // change the user name
to shubham and i was able to create a dir "hi" in /var/www/resource/projects/dir/dir.php

---

