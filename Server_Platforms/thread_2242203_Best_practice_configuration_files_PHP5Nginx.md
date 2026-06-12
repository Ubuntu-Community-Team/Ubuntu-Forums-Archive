---
title: "Best practice configuration files PHP5/Nginx?"
date: 2014-08-31
forum: Server Platforms
---

### Post by Eventum on 2014-08-31
I don't want to edit the default configuration files. Could you help me with some advice on where to best place my variables for easier management?

My setup: VPS with Ubuntu 14.04, PHP 5.6 (PHP5-FPM), Nginx 1.7 mainline, 1 domain/site

**PHP5: /etc/php5/fpm/php.ini**
I created /etc/php5/fpm/conf.d/site_php.ini and all my settings are accepted (opcache, memory etc). Is this OK? 

**Nginx: etc/nginx/nginx.conf** (i.e workers, output buffers, client timeouts etc.)

Can I just create "site_nginx.conf" and place it in /etc/nginx/conf.d for this to work? I will only be hosting a single site/domain on this server, so it doesn't matter if it applies to all sites/globally.

**PHP5-FPM: /etc/php5/fpm/pool.d/www.conf** (i.e requests, servers, children etc.)

Any ideas on this one?

---

### Post by TheFu on 2014-08-31
Don't know about php.

For nginx, place stuff into /etc/nginx/sites-available/
then symlink that to ../sites-enabled/ when ready to go live and restart/reload the nginx daemon.

These config files should be version controlled like software is.  There are many different ways to accomplish that - git, ansible, puppet and daily backups.

I suspect for the php stuff - it is similar.

---

### Post by sandyd on 2014-08-31
> **Eventum said:**
> I don't want to edit the default configuration files. Could you help me with some advice on where to best place my variables for easier management?

My setup: VPS with Ubuntu 14.04, PHP 5.6 (PHP5-FPM), Nginx 1.7 mainline, 1 domain/site

**PHP5: /etc/php5/fpm/php.ini**
I created /etc/php5/fpm/conf.d/site_php.ini and all my settings are accepted (opcache, memory etc). Is this OK? 

**Nginx: etc/nginx/nginx.conf** (i.e workers, output buffers, client timeouts etc.)

Can I just create "site_nginx.conf" and place it in /etc/nginx/conf.d for this to work? I will only be hosting a single site/domain on this server, so it doesn't matter if it applies to all sites/globally.

**PHP5-FPM: /etc/php5/fpm/pool.d/www.conf** (i.e requests, servers, children etc.)

Any ideas on this one?

Nginx will not start with duplicate configuration values (i.e. in conf.d). The best way to preserve the original file is to copy or back up nginx.conf somewhere.

A nice way to back up configuration is to back it up through a version management system such as Git.
Side Note:
By default, there should be a symlink for nginx's default site at /etc/nginx/sites-enabled/default - you should delete that, it wont delete the file but disable the default site. The original file will still be available at /etc/nginx/sites-available/default.

---

### Post by Eventum on 2014-08-31
> **sandyd said:**
> Nginx will not start with duplicate configuration values (i.e. in conf.d). The best way to preserve the original file is to copy or back up nginx.conf somewhere. A nice way to back up configuration is to back it up through a version management system such as Git.

Thanks! OK. I will go ahead and edit the nginx.conf for setting the appropriate number of workers and so forth. 

Does this also apply to the PHP5-FPM pool conf (/etc/php5/fpm/pool.d/www.conf)?

I need to add these settings to my pool configuration and would prefer to add them without editing [www.conf:](www.conf:) 
pm = dynamic
pm.max_children = 16
pm.start_servers = 6
pm.min_spare_servers = 4
pm.max_spare_servers = 10
pm.max_requests = 100

---

