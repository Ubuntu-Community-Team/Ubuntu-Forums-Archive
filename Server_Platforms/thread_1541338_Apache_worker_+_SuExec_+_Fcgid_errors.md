---
title: "Apache worker + SuExec + Fcgid errors"
date: 2010-07-29
forum: Server Platforms
---

### Post by alex88 on 2010-07-29
Hi guys, i'm building up a hosting server, i want to chroot each user to their dir containing www/ that consists the site dir, log/ that contains apache log and more later.

The structure is this:

/var/www/$username/www as virtualhost,

to secure the server i've tried to use apache chroot but with no luck, so i'm trying to use suexec and change php basepath to restrict each user to their home. For now i'm setting up only my site for test ([www.alexnetwork.it]("http://www.alexnetwork.it")) these are the config files:

/etc/apache/sites-enabled/www.alexnetwork.it

```
<VirtualHost *:80>
        ServerAdmin admin@alexnetwork.it
        ServerName www.alexnetwork.it
        SuexecUserGroup alexnetwork alexnetwork
        DocumentRoot /var/www/alexnetwork/www

        <Directory /var/www/alexnetwork/www>
                Options Indexes FollowSymLinks MultiViews ExecCgi
                AllowOverride None
                Order allow,deny
                allow from all

                AddHandler fcgid-script .php
                FCGIWrapper /usr/lib/cgi-bin/php5 .php
        </Directory>

        #SocketPath /var/lib/apache2/fcgid/sock
        DefaultInitEnv PHPRC=/etc/php5/cgi
        AddType application/x-httpd-php .php
        DefaultInitEnv PHP_FCGI_CHILDREN 3
        DefaultMaxClassProcessCount 1
        DefaultMinClassProcessCount 1
</VirtualHost>
```the apache.conf etc are at default, i've also enabled module suexec and fcgid.
This are the logs when restarting apache and trying to navigate to [www.alexnetwork.it]("http://www.alexnetwork.it")

```
[Thu Jul 29 07:32:56 2010] [info] removed PID file /var/run/apache2.pid (pid=30473)
[Thu Jul 29 07:32:56 2010] [notice] caught SIGTERM, shutting down
[Thu Jul 29 07:32:57 2010] [info] mod_fcgid: Process manager 30475 stopped
[Thu Jul 29 07:32:58 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Thu Jul 29 07:32:58 2010] [info] mod_fcgid: Process manager 1423 started
[Thu Jul 29 07:32:58 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 configured -- resuming normal operations
[Thu Jul 29 07:32:58 2010] [info] Server built: Apr 13 2010 19:29:28
[Thu Jul 29 07:32:58 2010] [debug] worker.c(1757): AcceptMutex: sysvsem (default: sysvsem)
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.html denied
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.cgi denied
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.pl denied
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.php denied
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.xhtml denied
[Thu Jul 29 07:33:58 2010] [error] [client 95.169.188.18] (13)Permission denied: access to /index.htm denied

```but the directory contains files:

```
/var/www/alexnetwork/www:
total 4
-rw-r--r-- 1 alexnetwork alexnetwork  0 Jul 28 22:37 index.html
-rwxr-xr-x 1 alexnetwork alexnetwork 31 Jul 28 21:29 index.php
```and are set to the username that suexec runs, also browser says 403 forbidden.

this is the passwd line for the user:

```
alexnetwork:x:1000:1000::/var/www/alexnetwork/:/bin/sh
```Any help with this?


---------------------------------------------------------

EDIT: I've also tried with this vhost setting:

```
FCGIWrapper /var/www/alexnetwork/php-cgi .php
```and this /var/www/alexnetwork/php-cgi script:

```
#!/bin/sh
# Set desired PHP_FCGI_* environment variables.
# Example:
# PHP FastCGI processes exit after 500 requests by default.
PHP_FCGI_MAX_REQUESTS=10000
export PHP_FCGI_MAX_REQUESTS

# Replace with the path to your FastCGI-enabled PHP executable
exec /usr/bin/php-cgi
```

---

### Post by alex88 on 2010-07-29
Solve following these tutorials:

[http://www.ruzee.com/blog/2009/01/apache-virtual-hosts-a-clean-setup-for-php-developers](http://www.ruzee.com/blog/2009/01/apache-virtual-hosts-a-clean-setup-for-php-developers)

[http://www.linode.com/forums/viewtopic.php?t=2982](http://www.linode.com/forums/viewtopic.php?t=2982)

---

