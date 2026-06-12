---
title: "Apache WebMin Virtual Host Failure"
date: 2011-04-28
forum: Server Platforms
---

### Post by eelo on 2011-04-28
I needed to create a virtual host for a php project I'm working on.
Rather than using command line and text editors, I installed webmin to accomplish this and hopefully perform other server configuration in the future.

When I created the virtual host and tried applying the changes Apache wouldn't re-start, and still doesn't restart after complete re-boot.

It's getting hung up at the end of apache2.conf, which is trying to include /etc/apache2/sites-enabled/000-default

When I look at 000-default from a File Browser, it's a linked file to etc/apache2/sites-available/default  I can open both the linked file and actual file in a text editor, and it looks fine.

When I view the directory, /etc/apache2/sites-available from shell, the default file isn't visible.  It seems this "invisibility" is probably related to the error, which is preventing start-up.

Can anyone explain why the file would be visible from the Ubuntu File Browser GUI but not from the terminal, and how I can fix so apache can recognize this on start-up?

---

### Post by volkswagner on 2011-04-28
What is the output for the following command?

```
ls -alt /etc/apache2/sites-available
```

Check your apache2 error log.

```
less /var/log/apache2/error.log
```

With less you can use arrow/page up/down to navigate and hit q to exit.

---

### Post by eelo on 2011-05-13
Sorry for the incredible delay in response.
Sites Available and Error Log, resp.:

total 16
drwxr-xr-x 7 root root 4096 2011-04-28 17:52 ..
drwxr-xr-x 2 root root 4096 2011-04-28 12:34 .
-rw-r--r-- 1 root root 7467 2010-08-18 22:19 default-ssl

PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Apr 25 07:58:19 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Mon Apr 25 07:58:19 2011] [notice] mod_python: using mutex_directory /tmp 
[Mon Apr 25 07:58:20 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch mod_python/3.3.1 Python/2.6.5 configured -- resuming normal operations
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
[Tue Apr 26 07:46:37 2011] [notice] Graceful restart requested, doing restart
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Tue Apr 26 07:47:09 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Tue Apr 26 07:47:09 2011] [notice] mod_python: using mutex_directory /tmp 
[Tue Apr 26 07:47:10 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch mod_python/3.3.1 Python/2.6.5 configured -- resuming normal operations
[Tue Apr 26 22:55:09 2011] [warn] child process 6183 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:09 2011] [warn] child process 6184 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:09 2011] [warn] child process 6185 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:09 2011] [warn] child process 6186 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:09 2011] [warn] child process 6187 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:11 2011] [warn] child process 6183 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:11 2011] [warn] child process 6184 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:11 2011] [warn] child process 6185 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:11 2011] [warn] child process 6186 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:11 2011] [warn] child process 6187 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:13 2011] [warn] child process 6183 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:13 2011] [warn] child process 6184 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:13 2011] [warn] child process 6185 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:13 2011] [warn] child process 6186 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:13 2011] [warn] child process 6187 still did not exit, sending a SIGTERM
[Tue Apr 26 22:55:15 2011] [error] child process 6183 still did not exit, sending a SIGKILL
[Tue Apr 26 22:55:15 2011] [error] child process 6184 still did not exit, sending a SIGKILL
[Tue Apr 26 22:55:15 2011] [error] child process 6185 still did not exit, sending a SIGKILL
[Tue Apr 26 22:55:15 2011] [error] child process 6186 still did not exit, sending a SIGKILL
[Tue Apr 26 22:55:15 2011] [error] child process 6187 still did not exit, sending a SIGKILL
[Tue Apr 26 22:55:16 2011] [notice] caught SIGTERM, shutting down
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Wed Apr 27 06:28:41 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Wed Apr 27 06:28:41 2011] [notice] mod_python: using mutex_directory /tmp 
[Wed Apr 27 06:28:41 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch mod_python/3.3.1 Python/2.6.5 configured -- resuming normal operations
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
[Wed Apr 27 22:32:26 2011] [notice] caught SIGTERM, shutting down
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Apr 28 06:37:32 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Apr 28 06:37:32 2011] [notice] mod_python: using mutex_directory /tmp 
[Thu Apr 28 06:37:32 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch mod_python/3.3.1 Python/2.6.5 configured -- resuming normal operations
[Thu Apr 28 10:06:29 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/application/LaborTracker
[Thu Apr 28 10:06:30 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Apr 28 10:06:33 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Apr 28 10:07:02 2011] [error] [client 127.0.0.1] File does not exist: /var/www/dev.ESSERP.com
[Thu Apr 28 10:07:13 2011] [error] [client 127.0.0.1] File does not exist: /var/www/dev.ESSERP.com
[Thu Apr 28 10:16:20 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/public/labortracker
[Thu Apr 28 10:16:26 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/public/labortracker
[Thu Apr 28 10:19:53 2011] [error] [client 127.0.0.1] File does not exist: /var/www/cplogin
[Thu Apr 28 10:36:27 2011] [error] [client 127.0.0.1] File does not exist: /var/www/phpinfo
[Thu Apr 28 10:49:52 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/public/labortracker
[Thu Apr 28 10:50:42 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/public/LaborTracker
[Thu Apr 28 10:50:50 2011] [error] [client 127.0.0.1] File does not exist: /var/www/ESSERP/LaborTracker
[Thu Apr 28 12:04:32 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Apr 28 12:04:35 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Apr 28 12:04:46 2011] [error] [client 127.0.0.1] File does not exist: /var/www/esserp.com
[Thu Apr 28 12:05:26 2011] [error] [client 127.0.0.1] script '/var/www/index.php' not found or unable to stat
[Thu Apr 28 12:07:02 2011] [error] [client 127.0.0.1] script '/var/www/index.php' not found or unable to stat
[Thu Apr 28 12:10:32 2011] [notice] Graceful restart requested, doing restart
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:40 2011] [warn] VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80) overlaps with VirtualHost [www.dev.ESSERP.com:80](www.dev.ESSERP.com:80), the first has precedence, perhaps you need a NameVirtualHost directive
[Thu Apr 28 12:10:45 2011] [error] (EAI 2)Name or service not known: Failed to resolve server name for 208.68.143.55 (check DNS) -- or specify an explicit ServerName
(99)Cannot assign requested address: make_sock: could not bind to address 208.68.143.55:80
no listening sockets available, shutting down
Unable to open logs
Failed loading /usr/lib/php5/<DATE+lfs>/xdebug.so:  /usr/lib/php5/<DATE+lfs>/xdebug.so: cannot open shared object file: No such file or directory

---

### Post by volkswagner on 2011-05-13
Looks like you have more than one problem.

The most significant may be the vhost files not seen in the cli.

Can you use the file browser to to copy the contents of each file in /etc/apache2/sites-available (create backup)?

If you can make copy/backup of each file, you can try to delete entire directory contents via cli.

Also make a list of all files in /etc/apache2/sites-enabled.

```
ls /etc/apache2/sites-enabled
```

From the list of files above try disabling each and all sites and see if you can get apache2 to start.

```
sudo a2dissite default
```

and again for each additional sites enabled.

```
sudo a2dissite sitename
```


```
sudo /etc/init.d/apache2 start
```

---

