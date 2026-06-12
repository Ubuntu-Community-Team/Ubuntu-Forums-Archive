---
title: "open_basedir error after PHP update"
date: 2011-01-12
forum: Server Platforms
---

### Post by DerSeppel on 2011-01-12
Hi there, 

I just ran apt-get update today to update all available packets.
Here's the history:
```

Start-Date: 2011-01-12  19:36:31
Upgrade: libc-bin (2.11.1-0ubuntu7.6, 2.11.1-0ubuntu7.7), php5 (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), nscd (2.11.1-0ubuntu7.6, 2.11.1-0ubuntu7.7), libapache2-mod-php5 (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php5-gd (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php-pear (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php5-curl (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php5-xmlrpc (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), libc6-dev (2.11.1-0ubuntu7.6, 2.11.1-0ubuntu7.7), php5-mysql (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), linux-libc-dev (2.6.32-27.49, 2.6.32-28.55), php5-cgi (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php5-cli (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), php5-dev (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6), libc-dev-bin (2.11.1-0ubuntu7.6, 2.11.1-0ubuntu7.7), libc6 (2.11.1-0ubuntu7.6, 2.11.1-0ubuntu7.7), php5-common (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.6)
End-Date: 2011-01-12  19:36:48

```Now I'm getting a strange error. I'm running PHP as mod_fcgi. No problems so far.
But after the update I noticed that my websites werent showing. (500 Internal Server Error)

Here's the error log: (example of a vhost running wordpress)

```

[Wed Jan 12 20:23:54 2011] [warn] [client xx.xx.xx.xx] mod_fcgid: stderr: PHP Warning:  require(): open_basedir restriction in effect. File(/var/kunden/webs/web1/wp-blog-header.php) is not within the allowed path(s): (/var/kunden/webs/web1/:/var/kunden/tmp/web1/:/usr/share/php/:/usr/share/php5/:/tmp/) in /var/kunden/webs/web1/index.php on line 17
[Wed Jan 12 20:23:54 2011] [warn] [clientxx.xx.xx.xx] mod_fcgid: stderr: PHP Warning:  require(/var/kunden/webs/web1/wp-blog-header.php): failed to open stream: Operation not permitted in /var/kunden/webs/web1/index.php on line 17
[Wed Jan 12 20:23:54 2011] [warn] [client xx.xx.xx.xx] mod_fcgid: stderr: PHP Fatal error:  require(): Failed opening required './wp-blog-header.php' (include_path='.:/usr/share/php/:/usr/share/php5/') in /var/kunden/webs/web1/index.php on line 17
[Wed Jan 12 20:23:54 2011] [debug] mod_deflate.c(615): [client xx.xx.xx.xx] Zlib: Compressed 0 to 2 : URL /index.php


```As you can see, the path IS allowed in the open_basedir, since its the root of the website.
suexec.log does not show any errors.

Disabling open_basedir solves the problem for now. But I dont intent to keep it that way.

Any ideas?

---

### Post by bsntech on 2011-01-12
I had this same problem when I upgraded this morning.  It only affected one VirtualHost - which was my VirtualHost.  This was set in the config:

php_admin_value open_basedir /

I simply removed this line from the config and the site works.  Apparently the default open_basedir is the entire structure of the system so it isn't needed.

In regards to your trouble - that is quite baffling.  I have this in all other VirtualHosts:

php_admin_value open_basedir /home/<domain-tld>/www:/tmp

Works without any problems for those hosts.

Maybe try to have this in your config and see if it works:

/var/kunden:/tmp

Not sure why you have the /usr/share/php and /usr/share/php5 in your open_basedir settings - but would there be any reason you don't want the open_basedir to just be set to your webroot (/var/kunden in this case)?  You need the /tmp in there as well since sometimes php/websites try to write temp files to that folder.

Brian S.

---

### Post by rmccarri on 2011-01-12
Great!  I was having this problem and this thread helped me figure it out.

open_basedir /var/www/

gives 500 error.

open_basedir /var/www

does not.  It seems to be a problem with a trailing slash.  Thanks!
Rob

---

### Post by bsntech on 2011-01-12
Yep, remove those trailing slashes.

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

### Post by James78 on 2011-01-12
Removing those trailing slashes is a security risk. It is NOT a fix but merely a workaround. This is a bug in PHP, and I reported it to Launchpad the instance it appeared. It is being worked on right now. ;)
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/701765](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/701765)

Note: Please read the "open_basedir string" section at [http://php.net/manual/en/ini.core.php](http://php.net/manual/en/ini.core.php) . Using slashes at the end of the open_basedir paths is perfectly valid. Using no slashes causes a regex wildcard type matching, where /etc/phpmyadmin would also match /etc/phpmyadminasdf, but /etc/phpmyadmin/ matches ONLY that directory. This is why using no slash at the end of the path is a security risk.

---

### Post by James78 on 2011-01-13
A new update fixing the issue has been rolled out. You should add the trailing slashes back to prevent a security hole. :)

---

### Post by DerSeppel on 2011-01-13
Thank you guys!
That was fast!

I already figured this might be a bug. I'm glad it seems to be fixed. I'll the update now....

---

