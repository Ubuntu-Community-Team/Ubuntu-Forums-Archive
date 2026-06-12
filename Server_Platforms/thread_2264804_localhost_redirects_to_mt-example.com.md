---
title: "localhost redirects to mt-example.com"
date: 2015-02-10
forum: Server Platforms
---

### Post by jovan2 on 2015-02-10
Today I tried to enable mod rewrite and something weird happend. Now when i try to access localhost I get redirect to mt-example.com
Does anyone knows what is happening?

Also localhost/phpmyadmin works perfect.

Error log:

> [Mon Feb 09 11:14:09.336333 2015] [mpm_prefork:notice] [pid 1462] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Mon Feb 09 11:14:09.336359 2015] [core:notice] [pid 1462] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 13:50:01.833330 2015] [mpm_prefork:notice] [pid 1462] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 13:50:02.955321 2015] [mpm_prefork:notice] [pid 2023] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 13:50:02.955371 2015] [core:notice] [pid 2023] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 13:50:46.729488 2015] [core:alert] [pid 2028] [client 127.0.0.1:42261] /var/www/clients/.htaccess: <Directory not allowed here, referer: [http://localhost/clients/index.php](http://localhost/clients/index.php)
[Tue Feb 10 13:50:48.765776 2015] [core:alert] [pid 2029] [client 127.0.0.1:42262] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:50:52.533657 2015] [core:alert] [pid 2030] [client 127.0.0.1:42263] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:50:57.042955 2015] [core:alert] [pid 2031] [client 127.0.0.1:42264] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:00.963257 2015] [core:alert] [pid 2082] [client 127.0.0.1:42266] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:09.599749 2015] [core:alert] [pid 2027] [client 127.0.0.1:42268] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:10.811801 2015] [core:alert] [pid 2028] [client 127.0.0.1:42269] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:11.168206 2015] [core:alert] [pid 2029] [client 127.0.0.1:42270] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:11.367872 2015] [core:alert] [pid 2030] [client 127.0.0.1:42271] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:11.560820 2015] [core:alert] [pid 2031] [client 127.0.0.1:42272] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:12.146821 2015] [core:alert] [pid 2082] [client 127.0.0.1:42273] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:12.347637 2015] [core:alert] [pid 2027] [client 127.0.0.1:42274] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:12.530492 2015] [core:alert] [pid 2028] [client 127.0.0.1:42275] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:12.717154 2015] [core:alert] [pid 2029] [client 127.0.0.1:42276] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:12.911555 2015] [core:alert] [pid 2030] [client 127.0.0.1:42277] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:26.819934 2015] [mpm_prefork:notice] [pid 2023] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 13:51:27.920793 2015] [mpm_prefork:notice] [pid 2247] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 13:51:27.920842 2015] [core:notice] [pid 2247] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 13:51:30.745040 2015] [core:alert] [pid 2251] [client 127.0.0.1:42289] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:31.182389 2015] [core:alert] [pid 2252] [client 127.0.0.1:42290] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:31.414133 2015] [core:alert] [pid 2253] [client 127.0.0.1:42291] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:31.621799 2015] [core:alert] [pid 2254] [client 127.0.0.1:42292] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:33.826237 2015] [core:alert] [pid 2255] [client 127.0.0.1:42294] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:37.731765 2015] [core:alert] [pid 2251] [client 127.0.0.1:42295] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:51:41.768706 2015] [core:alert] [pid 2252] [client 127.0.0.1:42296] /var/www/clients/.htaccess: <Directory not allowed here
[Tue Feb 10 13:54:00.154970 2015] [mpm_prefork:notice] [pid 2247] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 13:54:01.262406 2015] [mpm_prefork:notice] [pid 2355] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 13:54:01.262473 2015] [core:notice] [pid 2355] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 13:57:24.189226 2015] [mpm_prefork:notice] [pid 2355] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 13:57:25.304960 2015] [mpm_prefork:notice] [pid 2571] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 13:57:25.305013 2015] [core:notice] [pid 2571] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 14:02:11.812055 2015] [mpm_prefork:notice] [pid 2571] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 14:02:12.908242 2015] [mpm_prefork:notice] [pid 2805] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 14:02:12.908302 2015] [core:notice] [pid 2805] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 14:21:33.429411 2015] [mpm_prefork:notice] [pid 2805] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 14:21:34.547420 2015] [mpm_prefork:notice] [pid 3205] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 14:21:34.547480 2015] [core:notice] [pid 3205] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 14:24:34.696834 2015] [mpm_prefork:notice] [pid 3205] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 14:24:35.803536 2015] [mpm_prefork:notice] [pid 3272] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 14:24:35.803596 2015] [core:notice] [pid 3272] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 14:26:00.064878 2015] [mpm_prefork:notice] [pid 3272] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 14:26:01.172505 2015] [mpm_prefork:notice] [pid 3444] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 14:26:01.172768 2015] [core:notice] [pid 3444] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 10 14:41:46.830926 2015] [mpm_prefork:notice] [pid 3444] AH00169: caught SIGTERM, shutting down
[Tue Feb 10 14:42:50.957594 2015] [mpm_prefork:notice] [pid 1613] AH00163: Apache/2.4.10 (Ubuntu) PHP/5.5.18-1+deb.sury.org~precise+1 configured -- resuming normal operations
[Tue Feb 10 14:42:50.970573 2015] [core:notice] [pid 1613] AH00094: Command line: '/usr/sbin/apache2'

Just for a note: /var/www/clients/.htaccess file does not exists any more, I've deleted it.

---

### Post by jovan2 on 2015-02-10
Update:

I've cleared my cache, and now localhost works. But for example localhost/clients is not working. And that clients folder exists in var/www

---

### Post by volkswagner on 2015-02-10
It's difficult to guess what "... is not working" means.

What error message do you get? Have you check logs after navigating to that address?

What do you have for vhost file contents?

If you are running Ubuntu 14.04, I believe they move the default webroot dir to /var/www/html.

If you want to access localhost/clients, you'll need to modify the default vhost in /etc/apache2/sites-available 
and change both the DocumentRoot and Directory stanzas. Again this is if you're running 14.04 or later.

---

### Post by darkapec on 2015-02-10
does your "*serveripaddress*/clients" work? You can find your sever ip by running 

```

ifconfig

```

it is likely 192.168.1.XXX

If the above works please give me the output of "/etc/apache2/apache2.conf"

According to your log, it looks like you have an .htaccess file or at least apache is expecting one in /var/www/clients

---

### Post by jovan2 on 2015-02-10
I don't get any error message when I try to access, I mean error logs are not updated. And on link it says 404 not found. 
It worked everything perfect until today when i tried to enable mod-rewrite. And sites-available files are changed for /var/www :(

Point about /var/www/html it's locked and I can not change anything there?

---

### Post by volkswagner on 2015-02-10
If you disable mod-rewrite does it work?
Please provide your rewrite rules and how you are implementing them.

---

