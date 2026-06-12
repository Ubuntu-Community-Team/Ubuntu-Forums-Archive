---
title: "&quot;Phantom&quot; PHP/Apache2 configuration on 20.04 LTS"
date: 2020-07-22
forum: Server Platforms
---

### Post by jayz99 on 2020-07-22
Hi All,

I'm running on LTS 20.04 with the latest Apache, PHP 7.4.3 and Nextcloud. I'm fine-tuning the installation and struggling with finding where the config files are held... Specifically I want to (1) disable Apache PHP headers, (2) fine-tune PHP (think memory limits, opcache, etc.) Just a heads up - I've migrated from a BSD + Nginx setup which might be contributing to my ignorance... 

I've been modifying files in /etc/php/* but the settings seem to have no effect. E.g. mem limit reported by php_info() is 128M and I've changed it in every php.ini file in found. Expose_php is also set to 0 and the same issue persists. Key question: where is the MASTER configuration for php? Php_info() reports /etc/php/7.4/fpm/* but I've modified those files, and others and getting nowhere...

Similar issues with Apache 2. Enables HTTP2 and wanted to disable HTTP1.1 - protocol setting of h2 and h2c (HTTP2/TLS and HTTP2/TCP) does not yield a HTTP2 header always. I see HTTP1.1 and upgrade to HTTP2 via curl or Firefox. Also tried adjusting ciphers used - copied a string from NGINX config to apache2.conf and it didn't work. Set ciphers to HIGH, excluded NULL and weak and likewise this did not have any impact. Weak ciphers were still available. 

Onwards to the setup:

**1. /etc/apache2/mods-enabled# ls -l**
```
lrwxrwxrwx 1 root root 36 Jul 19 20:31 access_compat.load -> ../mods-available/access_compat.load
lrwxrwxrwx 1 root root 28 Jul 19 20:31 alias.conf -> ../mods-available/alias.conf
lrwxrwxrwx 1 root root 28 Jul 19 20:31 alias.load -> ../mods-available/alias.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 auth_basic.load -> ../mods-available/auth_basic.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 authn_core.load -> ../mods-available/authn_core.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 authn_file.load -> ../mods-available/authn_file.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 authz_core.load -> ../mods-available/authz_core.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 authz_host.load -> ../mods-available/authz_host.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 authz_user.load -> ../mods-available/authz_user.load
lrwxrwxrwx 1 root root 32 Jul 19 20:31 autoindex.conf -> ../mods-available/autoindex.conf
lrwxrwxrwx 1 root root 32 Jul 19 20:31 autoindex.load -> ../mods-available/autoindex.load
lrwxrwxrwx 1 root root 30 Jul 19 20:31 deflate.conf -> ../mods-available/deflate.conf
lrwxrwxrwx 1 root root 30 Jul 19 20:31 deflate.load -> ../mods-available/deflate.load
lrwxrwxrwx 1 root root 26 Jul 19 20:31 dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root 26 Jul 19 20:31 dir.load -> ../mods-available/dir.load
lrwxrwxrwx 1 root root 26 Jul 19 20:31 env.load -> ../mods-available/env.load
lrwxrwxrwx 1 root root 29 Jul 19 20:31 filter.load -> ../mods-available/filter.load
lrwxrwxrwx 1 root root 30 Jul 19 21:05 headers.load -> ../mods-available/headers.load
lrwxrwxrwx 1 root root 28 Jul 21 21:13 http2.conf -> ../mods-available/http2.conf
lrwxrwxrwx 1 root root 28 Jul 21 21:13 http2.load -> ../mods-available/http2.load
lrwxrwxrwx 1 root root 27 Jul 19 20:31 mime.conf -> ../mods-available/mime.conf
lrwxrwxrwx 1 root root 27 Jul 19 20:31 mime.load -> ../mods-available/mime.load
lrwxrwxrwx 1 root root 32 Jul 22 09:56 mpm_event.conf -> ../mods-available/mpm_event.conf
lrwxrwxrwx 1 root root 32 Jul 22 09:56 mpm_event.load -> ../mods-available/mpm_event.load
lrwxrwxrwx 1 root root 34 Jul 19 20:31 negotiation.conf -> ../mods-available/negotiation.conf
lrwxrwxrwx 1 root root 34 Jul 19 20:31 negotiation.load -> ../mods-available/negotiation.load
lrwxrwxrwx 1 root root 28 Jul 22 09:56 proxy.conf -> ../mods-available/proxy.conf
lrwxrwxrwx 1 root root 28 Jul 22 09:56 proxy.load -> ../mods-available/proxy.load
lrwxrwxrwx 1 root root 33 Jul 22 09:56 proxy_fcgi.load -> ../mods-available/proxy_fcgi.load
lrwxrwxrwx 1 root root 33 Jul 19 20:31 reqtimeout.conf -> ../mods-available/reqtimeout.conf
lrwxrwxrwx 1 root root 33 Jul 19 20:31 reqtimeout.load -> ../mods-available/reqtimeout.load
lrwxrwxrwx 1 root root 30 Jul 19 21:05 rewrite.load -> ../mods-available/rewrite.load
lrwxrwxrwx 1 root root 31 Jul 19 20:31 setenvif.conf -> ../mods-available/setenvif.conf
lrwxrwxrwx 1 root root 31 Jul 19 20:31 setenvif.load -> ../mods-available/setenvif.load
lrwxrwxrwx 1 root root 36 Jul 21 16:33 socache_shmcb.load -> ../mods-available/socache_shmcb.load
lrwxrwxrwx 1 root root 26 Jul 21 16:33 ssl.conf -> ../mods-available/ssl.conf
lrwxrwxrwx 1 root root 26 Jul 21 16:33 ssl.load -> ../mods-available/ssl.load
lrwxrwxrwx 1 root root 29 Jul 19 20:31 status.conf -> ../mods-available/status.conf
lrwxrwxrwx 1 root root 29 Jul 19 20:31 status.load -> ../mods-available/status.load
```

**2. /etc/apache2/conf-enabled# ls -l**
```
lrwxrwxrwx 1 root root 30 Jul 19 20:31 charset.conf -> ../conf-available/charset.conf
lrwxrwxrwx 1 root root 44 Jul 19 20:31 localized-error-pages.conf -> ../conf-available/localized-error-pages.conf
lrwxrwxrwx 1 root root 46 Jul 19 20:31 other-vhosts-access-log.conf -> ../conf-available/other-vhosts-access-log.conf
lrwxrwxrwx 1 root root 33 Jul 19 21:23 php7.4-fpm.conf -> ../conf-available/php7.4-fpm.conf
lrwxrwxrwx 1 root root 31 Jul 19 20:31 security.conf -> ../conf-available/security.conf
lrwxrwxrwx 1 root root 36 Jul 19 20:31 serve-cgi-bin.conf -> ../conf-available/serve-cgi-bin.conf
```

**3. /etc/php/7.4# ls -l**
```
drwxr-xr-x 3 root root 4096 Jul 22 14:38 apache2
drwxr-xr-x 3 root root 4096 Jul 21 21:00 cli
drwxr-xr-x 4 root root 4096 Jul 22 14:52 fpm
drwxr-xr-x 2 root root 4096 Jul 22 14:46 mods-available
```

**4. php_info()**
  [TABLE]
[TR]
[TD="class: e"]Configuration File (php.ini) Path[/TD]
[TD="class: v"]/etc/php/7.4/fpm[/TD]
[/TR]
[TR]
[TD="class: e"]Loaded Configuration File[/TD]
[TD="class: v"]/etc/php/7.4/fpm/php.ini[/TD]
[/TR]
[TR]
[TD="class: e"]Scan this dir for additional .ini files[/TD]
[TD="class: v"]/etc/php/7.4/fpm/conf.d[/TD]
[/TR]
[TR]
[TD="class: e"]Additional .ini files parsed[/TD]
[TD="class: v"]/etc/php/7.4/fpm/conf.d/...[/TD]
[/TR]
[/TABLE]

Thanks in advance! :)
Janusz

---

