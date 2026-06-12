---
title: "multiple sits apache configuration"
date: 2016-04-30
forum: Server Platforms
---

### Post by rv65 on 2016-04-30
I have been having trouble with my Linode on Ubuntu 16.04, in regards to multiple websites on the same Apache2 host. I can setup one just fine, but if I set up another, it won't redirect to the other domain, or it takes down my main domain. I want to host a 2nd site, as my server is not running at full capacity. I have used the Linode tutorials, but I seem lost and it just does not work. Any help would be great.

---

### Post by darkod on 2016-04-30
I don't know which steps you already performed, but in theory it should be quite simple. Something like:
1. Become root and go to where the .conf files are:
```
sudo -i
cd /etc/apache2/sites-available
```

2. Make a copy of the default site (you can use that as a template):
```
cp 000-default.conf domain2.conf
```
You can call the file whatever you want, like domain2.conf or 001-domain2.conf, etc. But it has to end in .conf, that's a requirement of apache.

3. Edit the basic parameters you need to change with the domain info and the path where you will keep the files of the second site:
```
nano domain2.conf
(modify it like:)
ServerName   domain2.com
ServerAlias   www.domain2.com
DocumentRoot   /var/www/domain2
```

4. Enable the new site and restart apache2 service:
```
a2ensite domain2.conf
service apache2 restart
```

That should be it on the web server part.

But you also need actions in the DNS servers handling your domain(s). You need to create the A records pointing to the public IP of your webserver VM (in case you already haven't created these records). Of course, the DNS is what points clients to your server, it's not enough just to create the config files on the server.

---

### Post by rv65 on 2016-05-04
```

May 04 01:09:42 sandiegohdtv systemd[1]: Reloading LSB: Apache2 web server.
-- Subject: Unit apache2.service has begun reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit apache2.service has begun reloading its configuration
May 04 01:09:42 sandiegohdtv apache2[6943]:  * Reloading Apache httpd web server apache2
May 04 01:09:42 sandiegohdtv apache2[6943]:  *
May 04 01:09:42 sandiegohdtv apache2[6943]:  * The apache2 configtest failed. Not doing anything.
May 04 01:09:42 sandiegohdtv apache2[6943]: Output of config test was:
May 04 01:09:42 sandiegohdtv apache2[6943]: AH00526: Syntax error on line 2 of /etc/apache2/sites-enabled/sdhdtv.org.conf:
May 04 01:09:42 sandiegohdtv apache2[6943]: Unknown Authz provider: All
May 04 01:09:42 sandiegohdtv apache2[6943]: Action 'configtest' failed.
May 04 01:09:42 sandiegohdtv apache2[6943]: The Apache error log may have more information.
May 04 01:09:42 sandiegohdtv systemd[1]: apache2.service: Control process exited, code=exited status=1
May 04 01:09:42 sandiegohdtv systemd[1]: Reload failed for LSB: Apache2 web server.
-- Subject: Unit apache2.service has finished reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit apache2.service has finished reloading its configuration
--
-- The result is failed.
~

```

Getting this error when I try to fix the apache config for my main site. I am thinking this version of apache is borked. I did get it working once, but now I am borked again and only some parts of xenforo work and will give me error messages.

---

### Post by rv65 on 2016-05-04
```
-- Unit apache2.service has begun reloading its configuration
May 04 01:23:10 sandiegohdtv apache2[7059]:  * Reloading Apache httpd web server apache2
May 04 01:23:11 sandiegohdtv apache2[7059]:  *
May 04 01:23:11 sandiegohdtv systemd[1]: Reloaded LSB: Apache2 web server.
-- Subject: Unit apache2.service has finished reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit apache2.service has finished reloading its configuration
-- 
-- The result is done.
May 04 01:23:33 sandiegohdtv systemd[1]: Reloading LSB: Apache2 web server.
-- Subject: Unit apache2.service has begun reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit apache2.service has begun reloading its configuration
May 04 01:23:33 sandiegohdtv apache2[7099]:  * Reloading Apache httpd web server apache2
May 04 01:23:33 sandiegohdtv apache2[7099]:  *
May 04 01:23:33 sandiegohdtv apache2[7099]:  * The apache2 configtest failed. Not doing anything.
May 04 01:23:33 sandiegohdtv apache2[7099]: Output of config test was:
May 04 01:23:33 sandiegohdtv apache2[7099]: AH00526: Syntax error on line 8 of /etc/apache2/sites-enabled/sdhdtv.org.conf:
May 04 01:23:33 sandiegohdtv apache2[7099]: Invalid command 'Server', perhaps misspelled or defined by a module not included in the server configuration
May 04 01:23:33 sandiegohdtv apache2[7099]: Action 'configtest' failed.
May 04 01:23:33 sandiegohdtv apache2[7099]: The Apache error log may have more information.
May 04 01:23:33 sandiegohdtv systemd[1]: apache2.service: Control process exited, code=exited status=1
May 04 01:23:33 sandiegohdtv systemd[1]: Reload failed for LSB: Apache2 web server.
-- Subject: Unit apache2.service has finished reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit apache2.service has finished reloading its configuration
-- 
-- The result is failed.
May 04 01:24:40 sandiegohdtv postfix/qmgr[3750]: AAE712C037: from=<root@mail.sandiegohdtv.org>, size=701, nrcpt=1 (queue active)
May 04 01:24:40 sandiegohdtv postfix/proxymap[7117]: warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax 
May 04 01:24:40 sandiegohdtv postfix/trivial-rewrite[7116]: warning: virtual_mailbox_domains: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf: table lookup problem
May 04 01:24:40 sandiegohdtv postfix/trivial-rewrite[7116]: warning: virtual_mailbox_domains lookup failure
May 04 01:24:40 sandiegohdtv postfix/qmgr[3750]: 4D3D92C119: from=<root@mail.sandiegohdtv.org>, size=963, nrcpt=1 (queue active)
May 04 01:24:40 sandiegohdtv postfix/error[7118]: AAE712C037: to=<root@mail.sandiegohdtv.org>, orig_to=<root>, relay=none, delay=380739, delays=380739/0.02/0/0.02, dsn=4.3.0, status=deferred (address reso
May 04 01:24:40 sandiegohdtv postfix/error[7118]: using backwards-compatible default setting relay_domains=$mydestination to update fast-flush logfile for domain "mail.sandiegohdtv.org"
May 04 01:24:40 sandiegohdtv postfix/error[7119]: 4D3D92C119: to=<root@mail.sandiegohdtv.org>, orig_to=<root>, relay=none, delay=154775, delays=154775/0.01/0/0.03, dsn=4.3.0, status=deferred (address reso
May 04 01:24:40 sandiegohdtv postfix/error[7119]: using backwards-compatible default setting relay_domains=$mydestination to update fast-flush logfile for domain "mail.sandiegohdtv.org"
~
~
~
~
~
~
~
~
~
~

```

more errors

---

### Post by rv65 on 2016-05-04
I need rewrite capabilities, and I cannot for the life of me get this version to work.

---

### Post by rv65 on 2016-05-04
I think I got it to work, but have some other PHP error related to xenforo.

---

