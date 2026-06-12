---
title: "Apache mod_cache/cache_disk not working on Apache CGI-FPM Server anymore"
date: 2014-04-23
forum: Server Platforms
---

### Post by halbsodoppelt on 2014-04-23
Hi everyone,

my Apache 2.4 is not caching on the following setup:

Ubuntu 14.04 LTS (Server Edition)

I installed:

*apache2-mpm-worker libapache2-mod-fastcgi php5-**fpm* (and the resulting dependencies...)

I activated the following modules:
*a2enmod actions alias fastcgi cache cache_disk*

Setup the fcgi-fpm like that:

[I]mkdir /var/www/cgi-bin
touch /var/www/cgi-bin/php5.fcgi
[/I]*chown -R www-data:www-data /var/www/cgi-bin*

edited /etc/apache2/mods-enabled/fastcgi.conf:


[INDENT]<IfModule mod_fastcgi.c>
[/INDENT]
[INDENT]  AddHandler fastcgi-script .fcgi[/INDENT]
[INDENT]  #FastCgiWrapper /usr/lib/apache2/suexec[/INDENT]
[INDENT]  FastCgiIpcDir /var/lib/apache2/fastcgi[/INDENT]
[INDENT] [/INDENT]
[INDENT]  Alias /php5.fcgi /var/www/cgi-bin/php5.fcgi[/INDENT]
[INDENT]  AddType application/x-httpd-fastphp5 .php[/INDENT]
[INDENT]  Action application/x-httpd-fastphp5 /php5.fcgi[/INDENT]
[INDENT] [/INDENT]
[INDENT]  FastCGIExternalServer /var/www/cgi-bin/php5.fcgi -socket /var/run/php5-fpm.sock[/INDENT]
[INDENT] [/INDENT]
[INDENT]  <Directory "/var/www/cgi-bin">[/INDENT]
[INDENT]  Order allow,deny[/INDENT]
[INDENT]    <Files "php5.fcgi">[/INDENT]
[INDENT]      Order deny,allow[/INDENT]
[INDENT]    </Files>[/INDENT]
[INDENT]  </Directory>
[/INDENT]
[INDENT] [/INDENT]
[INDENT]</IfModule>
[/INDENT]



No big changes on the default virtual host settings.

I changed the vi /etc/apache2/mods-available/disk_cache.conf to the following:


<IfModule mod_cache_disk.c>

        # cache cleaning is done by htcacheclean, which can be configured in
        # /etc/default/apache2
        #
        # For further information, see the comments in that file,
        # /usr/share/doc/apache2/README.Debian, and the htcacheclean(8)
        # man page.

        # This path must be the same as the one in /etc/default/apache2
        CacheRoot /var/cache/apache2/mod_cache_disk

        # This will also cache local documents. It usually makes more sense to
        # put this into the configuration for just one virtual host.
        CacheEnable disk /


    # The result of CacheDirLevels * CacheDirLength must not be higher than
    # 20. Moreover, pay attention on file system limits. Some file systems
    # do not support more than a certain number of inodes and
    # subdirectories (e.g. 32000 for ext3)
#    CacheDirLevels 2
    CacheDirLevels 5
#    CacheDirLength 1
    CacheDirLength 3

</IfModule>



For testing i created a php file:
[I]
vi /var/www/test/cachetest.php[/I]


<?php
header("Cache-Control: must-revalidate, max-age=300");
header("Vary: Accept-Encoding");
echo time()."<br>";
?>This is printing the timestamp.

Now I call that file in a browser - it displays the current time stamp. 
While testing this on a Ubuntu 12.04 LTS and clicking in the browers adress bar and pressing ENTER so that the page gets loaded (wont work with F5! - cause this will fetch a fresh copy from the server instead of the cache) - i still see the old, cached timestamp.
On Ubuntu 14.04 LTS this just wont work.


Can anyone help me?
How can i use mod_cache in Ubuntu 14.04 LTS?

I am aware the mem_cache is removed from 14.04 LTS.

---

### Post by halbsodoppelt on 2014-05-20
No suggestions/solutions? :(

---

