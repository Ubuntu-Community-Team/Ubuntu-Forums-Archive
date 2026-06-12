---
title: "Lighttpd with PHP5 [___autoload] not working"
date: 2008-08-03
forum: Server Platforms
---

### Post by ftp1110 on 2008-08-03
Hello,

I have installed Ubuntu Server (8.04 LTS) for my home server.

------------------
Webserver: Lighttpd 1.4.19 (ssl)
PHP: 5.2.4-2
Mysql: 5.0.51a
------------------

I have created a php script that's automaticly includes classes by the __autoload function.

```
function __autoload($class_name)
{
    require_once 'includes/class.'.strtolower($class_name).'.php';
}
```

But when I load the script it crash.

> Warning: require_once(includes/class.registry.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/common.php on line 42

Fatal error: require_once() [function.require]: Failed opening required 'includes/class.registry.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/common.php on line 42

I have searched on Google, and found a solution: Install the snapshot build. (php5.3)

I followed [this]("http://codeblog.palos.ro/2008/05/06/ubuntu-packages-for-latest-php-snapshots/"), but I can't make it work with Lighttpd. I have installed it, but can't find any php.ini file and no way to get it work under Lighttpd.

Can someone please help me?

Thanks!

---

### Post by ftp1110 on 2008-08-04
Or just tell me howto install Lighttpd with the latest PHP snapshot? (PHP v5.3)

---

