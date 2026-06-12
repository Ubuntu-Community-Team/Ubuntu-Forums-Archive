---
title: "Web sites (apache2?) timing out/lagging randomly"
date: 2012-12-14
forum: Server Platforms
---

### Post by jwright8 on 2012-12-14
Hello everyone!

My friend and I recently consolidated our two setups into one.  He moved from a dedicated box, and I moved from a Linode (512 mb ram).  We are hosting about 5 WordPress 3.5 sites total, and the box specs are more than enough to handle it.  They are as follows:

Ubuntu 12.04 LTS x64
16 gb ram
1 tb drive
1 gbps port
2x quad core cpu

We have CloudFlare as the DNS. Sometimes, when this lag happens, it redirects to the CloudFlare page asking if they want to access a cached copy of the website, saying that the website itself is down. I don't believe it's the connection, as the FTP doesn't have this kind of inconsistency.  It's fast on the FTP side of things. 

The problem seems to be with Apache2.  There is nothing in the logs really to indicate problems (other than missing fav.ico's).  Sometimes, when you go to the site, it pulls it up almost instantly.  Other times, it displays half the page or just doesn't show anything at all.  It's also worth noting, I think, that they didn't have this problem on the other two setups.

When I restart apache, the only thing in the error logs (or even at all, really) is this:
```

[Fri Dec 14 21:55:36 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations

```

I did, however, find some of these in the logs, not sure if it has to do with anything:
```

[Fri Dec 14 21:40:21 2012] [error] [client 37.1.207.22] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary.

```

This was also an oddity in the access log:
```

108.162.237.39 - - [14/Dec/2012:20:30:12 -0500] "-" 408 0 "-" "-"

```

Example URLS:
iravelon.com
fatalclan.com

When I do "apache2 -l" it shows:
```

Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```

The apache2.conf is as follows:

```

ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
KeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild  7000
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   7000
</IfModule>

# For "pretty" permalinks:
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>
DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

```

An example of the sites-enabled themselves are:
```

<VirtualHost *:80>
	ServerName www.iravelon.com
	ServerAlias iravelon.com
	ServerAdmin admin@emailhere.com
	DocumentRoot /home/web/iravelon
	DirectoryIndex index.php index.html index.htm index.phtml index.phtm
	<Directory />
		Options -Indexes FollowSymLinks
		AllowOverride All
	</Directory>
	ErrorLog /var/log/apache2/iravelon-error_log
	LogLevel warn
	CustomLog /var/log/apache2/iravelon-access_log combined
</VirtualHost>

```

Here is a look at the mods-enabled:
[IMG]http://i48.tinypic.com/ezej4.png[/IMG]

As for system load:
```

root@odysseus:/etc/apache2/mods-enabled# uptime
 21:51:07 up  8:01,  4 users,  load average: 0.00, 0.01, 0.05

```
```


root@odysseus:/var/log/apache2# ps aux |grep apache2
root     17687  0.0  0.0 246012 10192 ?        Ss   21:55   0:00 /usr/sbin/apache2 -k start
www-data 17692  0.1  0.3 298572 60432 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17693  0.0  0.1 262132 25352 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17694  0.0  0.0 246308  7276 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17695  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17696  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17698  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
root     17704  0.0  0.0   9384   928 pts/1    S+   21:59   0:00 grep --color=auto apache2

```

I've also tried checking for MySQL slow queries ([http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html](http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html)) and nothing shows up there.

When I ping any of the sites from my home PC with ping <sitename> -n 100, the ping doesnt really seem to change that much (I don't see any significant spikes at all).  In fact, even when I ping it WHILE the site is lagging, it still doesn't show any spikes (9-20ms).

Any help is much appreciated!

EDIT:

A final note that I wanted to make here is that I cleared all the logs from apache2 and restarted apache.  I then spammed ls -l to check file sizes while i went to each site.  3 sites in, it was pretty normal, really fast speed, and the only errors about the favicon.ico.  The 4th site, however, started lagging before it came up.  I kept spamming ls -l still, and as it was lagging that sites's access and error log was still at 0 bytes with no data whatsoever.  When it started loading, it wrote some data into the access log and put the favicon.ico into the error log, but other than that there was nothing.  Perhaps that will explain things better to someone that knows more than I do about it.

---

### Post by sandyd on 2012-12-15
> **jwright8 said:**
> Hello everyone!

My friend and I recently consolidated our two setups into one.  He moved from a dedicated box, and I moved from a Linode (512 mb ram).  We are hosting about 5 WordPress 3.5 sites total, and the box specs are more than enough to handle it.  They are as follows:

Ubuntu 12.04 LTS x64
16 gb ram
1 tb drive
1 gbps port
2x quad core cpu

We have CloudFlare as the DNS. Sometimes, when this lag happens, it redirects to the CloudFlare page asking if they want to access a cached copy of the website, saying that the website itself is down. I don't believe it's the connection, as the FTP doesn't have this kind of inconsistency.  It's fast on the FTP side of things. 

The problem seems to be with Apache2.  There is nothing in the logs really to indicate problems (other than missing fav.ico's).  Sometimes, when you go to the site, it pulls it up almost instantly.  Other times, it displays half the page or just doesn't show anything at all.  It's also worth noting, I think, that they didn't have this problem on the other two setups.

When I restart apache, the only thing in the error logs (or even at all, really) is this:
```

[Fri Dec 14 21:55:36 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations

```

I did, however, find some of these in the logs, not sure if it has to do with anything:
```

[Fri Dec 14 21:40:21 2012] [error] [client 37.1.207.22] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary.

```

This was also an oddity in the access log:
```

108.162.237.39 - - [14/Dec/2012:20:30:12 -0500] "-" 408 0 "-" "-"

```

Example URLS:
iravelon.com
fatalclan.com

When I do "apache2 -l" it shows:
```

Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```

The apache2.conf is as follows:

```

ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
KeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild  7000
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   7000
</IfModule>

# For "pretty" permalinks:
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>
DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

```

An example of the sites-enabled themselves are:
```

<VirtualHost *:80>
	ServerName www.iravelon.com
	ServerAlias iravelon.com
	ServerAdmin admin@emailhere.com
	DocumentRoot /home/web/iravelon
	DirectoryIndex index.php index.html index.htm index.phtml index.phtm
	<Directory />
		Options -Indexes FollowSymLinks
		AllowOverride All
	</Directory>
	ErrorLog /var/log/apache2/iravelon-error_log
	LogLevel warn
	CustomLog /var/log/apache2/iravelon-access_log combined
</VirtualHost>

```

Here is a look at the mods-enabled:
[IMG]http://i48.tinypic.com/ezej4.png[/IMG]

As for system load:
```

root@odysseus:/etc/apache2/mods-enabled# uptime
 21:51:07 up  8:01,  4 users,  load average: 0.00, 0.01, 0.05

```
```


root@odysseus:/var/log/apache2# ps aux |grep apache2
root     17687  0.0  0.0 246012 10192 ?        Ss   21:55   0:00 /usr/sbin/apache2 -k start
www-data 17692  0.1  0.3 298572 60432 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17693  0.0  0.1 262132 25352 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17694  0.0  0.0 246308  7276 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17695  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17696  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
www-data 17698  0.0  0.0 246044  6120 ?        S    21:55   0:00 /usr/sbin/apache2 -k start
root     17704  0.0  0.0   9384   928 pts/1    S+   21:59   0:00 grep --color=auto apache2

```

I've also tried checking for MySQL slow queries ([http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html](http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html)) and nothing shows up there.

When I ping any of the sites from my home PC with ping <sitename> -n 100, the ping doesnt really seem to change that much (I don't see any significant spikes at all).  In fact, even when I ping it WHILE the site is lagging, it still doesn't show any spikes (9-20ms).

Any help is much appreciated!

EDIT:

A final note that I wanted to make here is that I cleared all the logs from apache2 and restarted apache.  I then spammed ls -l to check file sizes while i went to each site.  3 sites in, it was pretty normal, really fast speed, and the only errors about the favicon.ico.  The 4th site, however, started lagging before it came up.  I kept spamming ls -l still, and as it was lagging that sites's access and error log was still at 0 bytes with no data whatsoever.  When it started loading, it wrote some data into the access log and put the favicon.ico into the error log, but other than that there was nothing.  Perhaps that will explain things better to someone that knows more than I do about it.
firstly, increase 

```

MaxClients

```
in prefork to 500 or something. You are limiting the number of people viewing the sites to 150 clients, and any others will be backlogged

Secondly, that sounds like some of your rewrite rules have gone bad, probably because of the different paths used in the new server. check the .htaccesses in each wordpress install.

Thirdly, if you want to be more secure, you should use Suexec with apache2 worker. It will be less resource hungry (prefork is resource hungry). 

Fourth, there are ways to benchmark performance. Check out loadimpact, tools.pingdom.com and webpagetest.org

---

### Post by jwright8 on 2012-12-15
> **sandyd said:**
> firstly, increase 

```

MaxClients

```
in prefork to 500 or something. You are limiting the number of people viewing the sites to 150 clients, and any others will be backlogged

Secondly, that sounds like some of your rewrite rules have gone bad, probably because of the different paths used in the new server. check the .htaccesses in each wordpress install.

Thirdly, if you want to be more secure, you should use Suexec with apache2 worker. It will be less resource hungry (prefork is resource hungry). 

Fourth, there are ways to benchmark performance. Check out loadimpact, tools.pingdom.com and webpagetest.org


Thank you for your reply. 

We've changed the MaxClients to no avail.

As for the rewrite rule, we kept the exact same file structure as the old servers.  However, the .htaccess from one of the sites looks like this:

```

RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]

# add a trailing slash to /wp-admin
RewriteRule ^wp-admin$ wp-admin/ [R=301,L]

RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^ - [L]
RewriteRule ^(wp-(content|admin|includes).*) $1 [L]
RewriteRule ^(.*\.php)$ $1 [L]
RewriteRule . index.php [L]

```

This site uses the "pretty" permalink structure for WP.  The other sites, however, just use the default ?page_id=248 style.  These sites don't have an .htaccess file in the general WP install dir at all.  Should I change that? 

I tried with suexec and it doesnt seem to have corrected the problem, either.  Since there's literally nothing else running on the box atm other than the FTP server, I don't think resources available are the issue.  However, since we installed it the sites (when they actually decide they want to load) load a lot faster.  

As for the benchmarking sites, it can be as quick as 800 ms, then sometimes it will go up to 41.6s and then just say offline other times.

EDIT:

I will be reinstalling all of the wordpress sites and taking over minimal stuff (manually moving data from db's instead of just importing).  I will let everyone know how it went hopefully a little later on today, if no one else has any suggestions in the meantime.

---

### Post by jwright8 on 2012-12-15
Sorry for the double post, but just wanted to update.  

After reinstalling ALL of the sites, the problem still presents itself with a completely fresh WP install.  

Does anyone else have any ideas?  I'm at wit's end here, none of this makes any sense since all of these configurations worked perfectly before :(

EDIT:

We just got an error on the client side (trying to access using Chrome) when one of the sites showed as down:

```

HTTP Error 502 (Bad Gateway): The gateway or proxy server received an invalid response from an upstream server.

```

Anyone have any idea?

---

### Post by jwright8 on 2012-12-15
Okay, last post.  

I was apparently mistaken.  After redoing the wordpress sites completely, then redoing apache/mysql completely, it still didn't work.  

On a hunch, I switched from CloudFlare to NameCheap on one of the sites for the DNS servers, and it immediately started working (after they switched over, of course).  I tired disabling all the CloudFlare settings on another site, just to see if I had some settings wrong.  The problem still persisted on the second site.  Once I ported the nameservers for the second site over to NameCheap as well, the problem corrected itself on there, too.  I have one site that I host for a friend on the same box left that hasn't been ported over (he isn't home to authorize, etc.), and that is the ONLY site that is still barely loading, if at all.  If you want to see for yourself, his site is pizzaguns.com.  The other two sites I posted as examples above are hosted on the same exact box, with the same chowns/chmods/structure/WP versions/wp plugins/apache configs/etc.  It's ridiculous how different they are.  

In short, CloudFlare is apparently a load of crap for the free users (I can't say in regards to people with paid subscriptions), and isn't even close to being worth the trouble that comes with it for the minimal benefits it supposedly offers.  

Hopefully this helps someone else.  Thank you for the help!

---

