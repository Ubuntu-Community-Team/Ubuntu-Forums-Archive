---
title: "LAMP with SuPHP - SuPHP won't work"
date: 2013-10-08
forum: Server Platforms
---

### Post by rani2 on 2013-10-08
Sorry before,
I'm new in Ubuntu Server and I'm Noob

Here my problem:
I've already install LAMP (Linux-Apache-MySQL-PHP)
Linux work properly >test: my linux can execute normal command<
Apache2, yeah it's work too >test: I can call my web server, and it's work<
MySQL work properly with phpmyadmin >test: I can call phpmyadmin and I can make database<
PHP, same with Apache >test: I can call test php in /var/www/<

I want to execute command from php, so I make simple command:
<?php 
echo 'whoim = '.exec('/usr/bin/whoami');
?>
and I save in /var/www/test.php
when i call "mylinuxaddress/test.php" that give me 500 internal error

I modify /etc/apache2/apache2.conf
SuPHPsuPHP_Engine on
suPHP_AddHandler application/x-httpd-php .php

I modify /etc/suphp/suphp.conf
Handler for CGI-scriptsx-suphp-cgi="execute:!self"x-httpd-suphp="php:/usr/bin/php-cgi"

I've already try from root
> find /var/www/ -type f -exec chmod 644 {} \; >>I try 755 too<<
> find /var/www/ -type d -exec chmod 755 {} \;
> chown www-data:root -R /var/www/

I call again and it give me same error
500 internal error

please help me
>.<

---

### Post by Lars Noodén on 2013-10-08
We unless you have a specific reason for giving write access to your web server, I would suggest fixing the directory permissions

```

sudo chown root:root -R /var/www/

```

If you are the only user on that machine, you could take ownership instead of root and it would work just as well.

About the [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html), you can look at Apache2's error logs for clues.  But in all likelihood there is something wrong with your script.  Open a terminal and follow the error log live, real-time as you access your script.  You should then see the relevant error message in more detail.  

```

tail -f /var/log/apache2/error.log

```

You could set PHP so that errors are sent to the browser, but that has to be turned off later when your service goes public.  Don't forget that or it can give clues on how to break into your system.

---

### Post by SeijiSensei on 2013-10-08
You shouldn't need suexec to run the script you posted.  I'd take a look in /var/log/apache2/error.log and see what error it reports.  I'd disable suPHP because it can pose security issues unless you are careful.

I ran your script on my web server, which has no suPHP enabled, and it runs fine.  My guess is the 500 error comes from some syntax problem created while editing apache2.conf.

---

### Post by rani2 on 2013-10-10
Sorry for take long to reply
and Thank for hear my problem

Lars Nooden
I try to change owner of /var/www/ to root
but still give me 500 internal error
here message from tail:
> [Thu Oct 10 12:33:13 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.9-4ubuntu2.3
configured -- resuming normal operations
[Thu Oct 10 12:33:20 2013] [error] [client 192.168.168.1] SoftException in Application.cpp:350: UID of script "/var/www/test.php" is smaller than min_uid
[Thu Oct 10 12:33:20 2013] [error] [client 192.168.168.1] Premature end of script headers: test.php
I've already installl CGI version of suPHP too, like in suPHP-FAQ

SeijiSensei
I want to execute "exec" and "shell_exec" later to write some configuration in linux server,
without suPHP I can't reach my goal, so I wan't to fix suPHP,
I try to disable suPHP
> a2dismod suPHP
after that "exec" or "shell_exec" won't run

---

### Post by SeijiSensei on 2013-10-10
Well, you don't need suPHP to run either exec() or shell_exec() so the problem lies elsewhere.

I suspect you're encountering a permissions problem, since the web server will write files as the "www-data" user.  I solve this problem by creating a directory that is owned by that user into which it can write files.  If you want to let the server write into some arbitrary location, you can assign the www-data group to that directory and give it group-writable privileges.  However you need to be very careful about giving the server write privileges as it can create a major security hole.  suPHP obviously has security issues as well.  I recommend figuring out how to work within the limited privileges that the server possesses.  If you must use suPHP, do a Google search for "suphp security" before you start so you can get some idea of the security issues involved and how to minimize them.

---

### Post by rani2 on 2013-10-11
Thank You Sensei Seiji,
yeah it's permissions problem, I wrong at:
> chown www-data:root -R /var/www/
It should be
> chown www-data:www-data -R /var/www/
Thank You Very Much

And thanks too,
for the solution the writable file everywhere I want, 
^.^

and I know that I will create a major security hole,
I will improve the security with securing the website,
I don't know this will work or not
^.^

---

