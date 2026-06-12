---
title: "Installing mod_cache in Lighttpd"
date: 2009-01-29
forum: Server Platforms
---

### Post by adam35413 on 2009-01-29
I am extremely new to lighttpd, and wanted to use mod_cache.  I downloaded the patch file from the Docs page on the lighttpd site, but I can not figure out how to install it.  Since aptitude did all of the installing, I do not know if I even have access to the source to get it patched.

Do I have to build lighttpd from scratch to get mod_cache in there for ubuntu?

---

### Post by fujikofujio on 2009-04-16
Ubuntu 9.04: Installing Lighttpd 1.5 from source with PHP + mod_cache

[http://sitegeisha.blogspot.com/2009/04/ubuntu-904-installing-lighttpd-15-from.html](http://sitegeisha.blogspot.com/2009/04/ubuntu-904-installing-lighttpd-15-from.html)

To install PHP:
sudo apt-get install php5-cgi

Installing Lighttpd 1.5
The latest version I could find on their site:
[http://redmine.lighttpd.net/wiki/lighttpd/Docs:ModCache](http://redmine.lighttpd.net/wiki/lighttpd/Docs:ModCache)
[http://opensu.se/~darix/lighttpd/](http://opensu.se/~darix/lighttpd/)
[http://blog.lighttpd.net/articles/tag/1.5.0](http://blog.lighttpd.net/articles/tag/1.5.0)

    wget [http://www.linux.com.cn/modcache/lighttpd-1.5.0.r2294.modcache.v.1.6.1.tar.gz](http://www.linux.com.cn/modcache/lighttpd-1.5.0.r2294.modcache.v.1.6.1.tar.gz)

This is the patched version of lighttpd with mod_cache, extract this to a folder

    tar zxvf lighttpd-1.5.#######.gz
    cd lighttpd-1.5.0.cache

We need to install some required libraries first

    sudo apt-get install libssl-dev zlib1g-dev libbz2-dev libattr1-dev libpcre3-dev libmysqlclient15-dev libfam-dev libldap2-dev libfcgi-dev libgdbm-dev libmemcache-dev liblua5.1-0-dev pkg-config uuid-dev libsqlite3-dev libxml2-dev libkrb5-dev libglib2.0-dev libaio-dev libfam0 memcached

type ./configure --help to see configuration options

This is what I used

    ./configure --program-prefix= --prefix=/usr --exec-prefix=/usr --bindir=/usr/bin --sbindir=/usr/sbin --sysconfdir=/etc --datadir=/usr/share --includedir=/usr/include --libdir=/usr/lib --libexecdir=/usr/libexec --localstatedir=/var --sharedstatedir=/usr/com --mandir=/usr/share/man --infodir=/usr/share/info --with-openssl --with-memcache --with-gdbm

    make

    sudo make install

after installing you should be able to type

    lighttpd -V

and see some nice output from lighttpd

you can also type spawn-fcgi to make sure that installed as well

type sudo su

copy the sample config file

    mkdir /etc/lighttpd
    cp doc/lighttpd.conf /etc/lighttpd/

log folder

    mkdir /var/log/lighttpd

we need to create a startup file in the /etc/init.d folder
Go here to download the startup script [http://redmine.lighttpd.net/projects/lighttpd/wiki/ScriptsUbuntu](http://redmine.lighttpd.net/projects/lighttpd/wiki/ScriptsUbuntu)
create a file called lighttpd in the /etc/init.d/ folder and then

    chmod a+x /etc/init.d/lighttpd

Create a user to run lighttpd: if you have installed lighttpd 1.4 from apt or apache you can just use the www-data user again

    adduser -m -d /var/www -s /sbin/nologin lighttpd

Modify the lighttpd file from /etc/init.d/ to match the user you want to run it as

    chown www-data:www-data /var/log/lighttpd

then type

    update-rc.d lighttpd defaults

Edit the lighttpd.conf file to enable php fastcgi

Make sure following modules are loaded:

    server.modules += ( "mod_cache" "mod_proxy_core", "mod_proxy_backend_fastcgi" )

You can also enable other modules that you need, mod_cache has to be enable first!
cache.bases = ("/var/cache/lighttpd")
cache.enable = "enable"
cache.support-queries = "enable"
cache.debug = "enable"
cache.dynamic-mode = "enable"
cache.refresh-pattern = (
	"/$" => "5 update-on-refresh no-expire-header", # update homepage every 5 minutes and on refresh requests without setting expire headers
	"\.(?i)(flv)$" => "0 fetchall-for-range-request flv-streaming", # to work with mod_flv_streaming for flv files
	"\.(?i)(js|css|xml)$" => "240", # update js/css/xml every 4 hours and on refresh requests
	"\.(?i)(htm|html|shtml)$" => "30", # update html/htm/shtml every 30 minutes and on refresh requests
	"\.(?i)(jpg|bmp|jpeg|gif|png)$" => "2880", # update graphics files every 2 days
	"\.(?i)(rar|zip|wmv|avi|mp3|ape|rm|mpeg|mpg|wma|asf|rmvb|flv)$" => "0 fetchall-for-range-request", # cache media file forever
	".(?i)php$" => "5", # update php request every 5 minutes
	"." => "30 update-on-refresh" # default to update every 30 minutes and on refresh requests
)


Change

    server.document-root = "/var/www/"
    server.errorlog = "/var/log/lighttpd/error.log"
    server.event-handler = "linux-sysepoll"
    server.network-backend = "gthread-aio"
    accesslog.filename = "/var/log/lighttpd/access.log"
    compress.cache-dir = "/tmp/lighttpd/cache/compress/"
    compress.filetype = ("text/plain", "text/html")
    #### status module
    status.status-url = "/server-status"
    status.statistics-url = "/server-statistics"

    cache.bases = ("/var/cache/lighttpd")
    cache.enable = "enable"
    cache.support-queries = "enable"
    cache.debug = "enable"
    cache.dynamic-mode = "enable"

Make sure /var/cache/lighttpd is writeable by lighttpd and it exists.

Configure fastcgi PGP module by appending following configuration directives:

    $HTTP["url"] =~ "\.php$" {
    proxy-core.balancer = "round-robin"
    proxy-core.allow-x-sendfile = "enable"
    # proxy-core.check-local = "enable"
    proxy-core.protocol = "fastcgi"
    proxy-core.backends = ( "unix:/tmp/php-fastcgi.sock" )
    proxy-core.max-pool-size = 16
    proxy-core.worked-with-modcache = "enable"
    }

Make sure to leave the # in front of proxy-core.check-local = "enable" otherwise lighttpd won't start, don't know why.

Also don't forget to add proxy-core.worked-with-modcache = "enable" otherwise mod_cache won't do anything.

Save the config file and start lighttpd

    sudo /etc/init.d/lighttpd start


If everything goes well you should see something like this
* Starting lighttpd [ OK ]
* Starting spawn-fcgi spawn-fcgi.c.206: child spawned successfully: PID: 15245
[ OK ]

inside the /var/www folder create index.php file and add something to it

test by browsing [http://localhost/index.php](http://localhost/index.php)
You should see php configuration options here


How to uninstall
go back to the lighttpd source

    sudo make uninstall

References:
[http://redmine.lighttpd.net/projects/lighttpd/wiki/InstallFromSource](http://redmine.lighttpd.net/projects/lighttpd/wiki/InstallFromSource)
[http://www.cyberciti.biz/tips/rhel-lighttpd-15-installation-configuration-howto.html](http://www.cyberciti.biz/tips/rhel-lighttpd-15-installation-configuration-howto.html)
[http://www.cyberciti.biz/tips/howto-increase-lighttpd-performance-with-linux-aio.html](http://www.cyberciti.biz/tips/howto-increase-lighttpd-performance-with-linux-aio.html)
[http://www.cyberciti.biz/tips/freebsd-linux-lighttpd-1-5-fastcgi-configuration.html](http://www.cyberciti.biz/tips/freebsd-linux-lighttpd-1-5-fastcgi-configuration.html)
[http://www.linux.com.cn/modcache/](http://www.linux.com.cn/modcache/)
[http://redmine.lighttpd.net/wiki/lighttpd/Docs:ModCache#Installation](http://redmine.lighttpd.net/wiki/lighttpd/Docs:ModCache#Installation)

---

### Post by tapas_mishra on 2010-08-04
> **fujikofujio said:**
> 

We need to install some required libraries first

    sudo apt-get install libssl-dev zlib1g-dev libbz2-dev libattr1-dev libpcre3-dev libmysqlclient15-dev libfam-dev libldap2-dev libfcgi-dev libgdbm-dev libmemcache-dev liblua5.1-0-dev pkg-config uuid-dev libsqlite3-dev libxml2-dev libkrb5-dev libglib2.0-dev libaio-dev libfam0 memcached

Output on my system
```

Preconfiguring packages ...
dpkg: libgamin0: dependency problems, but removing anyway as you request:
 libgnomevfs2-0 depends on libgamin0 | libfam0; however:
  Package libgamin0 is to be removed.
  Package libfam0 is not installed.
  Package libgamin0 which provides libfam0 is to be removed.
 libgnomevfs2-0 depends on libgamin0 | libfam0; however:
  Package libgamin0 is to be removed.
  Package libfam0 is not installed.
  Package libgamin0 which provides libfam0 is to be removed.
(Reading database ... 155274 files and directories currently installed.)
Removing libgamin0 ...
Removing gamin ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 155260 files and directories currently installed.)
Preparing to replace libattr1 1:2.4.43-1 (using .../libattr1_1%3a2.4.43-2_i386.deb) ...
Unpacking replacement libattr1 ...
Setting up libattr1 (1:2.4.43-2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 155260 files and directories currently installed.)
Preparing to replace libssl0.9.8 0.9.8g-15ubuntu3 (using .../libssl0.9.8_0.9.8g-15+lenny7_i386.deb) ...
Unpacking replacement libssl0.9.8 ...
Selecting previously deselected package portmap.
Unpacking portmap (from .../portmap_6.0-9ubuntu1_i386.deb) ...
Selecting previously deselected package fam.
Unpacking fam (from .../fam_2.7.0-13.3+lenny1_i386.deb) ...
Selecting previously deselected package libaio1.
Unpacking libaio1 (from .../libaio1_0.3.107-3ubuntu1_i386.deb) ...
Selecting previously deselected package libaio-dev.
Unpacking libaio-dev (from .../libaio-dev_0.3.107-3ubuntu1_i386.deb) ...
Selecting previously deselected package libevent1.
Unpacking libevent1 (from .../libevent1_1.3e-3_i386.deb) ...
Selecting previously deselected package libfam0.
Unpacking libfam0 (from .../libfam0_2.7.0-13.3+lenny1_i386.deb) ...
Selecting previously deselected package libfam-dev.
Unpacking libfam-dev (from .../libfam-dev_2.7.0-13.3+lenny1_i386.deb) ...
Selecting previously deselected package libfcgi0ldbl.
Unpacking libfcgi0ldbl (from .../libfcgi0ldbl_2.4.0-7_i386.deb) ...
Selecting previously deselected package libfcgi-dev.
Unpacking libfcgi-dev (from .../libfcgi-dev_2.4.0-7_i386.deb) ...
Selecting previously deselected package libgdbm-dev.
Unpacking libgdbm-dev (from .../libgdbm-dev_1.8.3-4_i386.deb) ...
Selecting previously deselected package liblua5.1-0-dev.
Unpacking liblua5.1-0-dev (from .../liblua5.1-0-dev_5.1.4-2_i386.deb) ...
Selecting previously deselected package libmemcache0.
Unpacking libmemcache0 (from .../libmemcache0_1.4.0.rc2-1_i386.deb) ...
Selecting previously deselected package libmemcache-dev.
Unpacking libmemcache-dev (from .../libmemcache-dev_1.4.0.rc2-1_i386.deb) ...
Selecting previously deselected package libmysqlclient15-dev.
Unpacking libmysqlclient15-dev (from .../libmysqlclient15-dev_5.1.30really5.0.75-0ubuntu10_i386.deb) ...
Selecting previously deselected package libsqlite3-dev.
Unpacking libsqlite3-dev (from .../libsqlite3-dev_3.6.10-1_i386.deb) ...
Selecting previously deselected package libssl-dev.
Unpacking libssl-dev (from .../libssl-dev_0.9.8g-15+lenny7_i386.deb) ...
Selecting previously deselected package memcached.
Unpacking memcached (from .../memcached_1.2.2-1+lenny1_i386.deb) ...
Selecting previously deselected package libattr1-dev.
Unpacking libattr1-dev (from .../libattr1-dev_1%3a2.4.43-2_i386.deb) ...
Selecting previously deselected package libldap2-dev.
Unpacking libldap2-dev (from .../libldap2-dev_2.4.15-1ubuntu3_i386.deb) ...
Selecting previously deselected package uuid-dev.
Unpacking uuid-dev (from .../uuid-dev_1.2-1.41.4-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libssl0.9.8 (0.9.8g-15+lenny7) ...

Setting up portmap (6.0-9ubuntu1) ...
 * Starting portmap daemon...                                                                                                                                   [ OK ] 

Setting up fam (2.7.0-13.3+lenny1) ...
 * Starting file alteration monitor FAM                                                                                                                         [ OK ] 

Setting up libaio1 (0.3.107-3ubuntu1) ...

Setting up libaio-dev (0.3.107-3ubuntu1) ...
Setting up libevent1 (1.3e-3) ...

Setting up libfam0 (2.7.0-13.3+lenny1) ...

Setting up libfam-dev (2.7.0-13.3+lenny1) ...
Setting up libfcgi0ldbl (2.4.0-7) ...

Setting up libfcgi-dev (2.4.0-7) ...
Setting up libgdbm-dev (1.8.3-4) ...

Setting up liblua5.1-0-dev (5.1.4-2) ...
Setting up libmemcache0 (1.4.0.rc2-1) ...

Setting up libmemcache-dev (1.4.0.rc2-1) ...
Setting up libmysqlclient15-dev (5.1.30really5.0.75-0ubuntu10) ...

Setting up libsqlite3-dev (3.6.10-1) ...
Setting up libssl-dev (0.9.8g-15+lenny7) ...
Setting up memcached (1.2.2-1+lenny1) ...
Starting memcached: memcached.

Setting up libattr1-dev (1:2.4.43-2) ...
Setting up libldap2-dev (2.4.15-1ubuntu3) ...
Setting up uuid-dev (1.2-1.41.4-1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


```Then I did 
```

  ./configure 
make
sudo make install

```> **fujikofujio said:**
> 

after installing you should be able to type

    lighttpd -V

and see some nice output from lighttpd

Here is my output
```

lighttpd/1.4.27-devel-2744M - a light and fast webserver
Build-Date: Aug  4 2010 12:16:15

Event Handlers:

    + select (generic)
    + poll (Unix)
    + rt-signals (Linux 2.4+)
    + epoll (Linux 2.6)
    - /dev/poll (Solaris)
    - kqueue (FreeBSD)

Network handler:

    + sendfile

Features:

    + IPv6 support
    + zlib support
    + bzip2 support
    + crypt support
    - SSL Support
    + PCRE support
    - mySQL support
    - LDAP support
    - memcached support
    - FAM support
    - LUA support
    - xml support
    - SQLite support
    - GDBM support



```> **fujikofujio said:**
> 

you can also type spawn-fcgi to make sure that installed as well

I typed on terminal as root
spawn-fcgi got following error
```

root@tapas-laptop:/usr/src/lighttpd-1.4.x# spawn-fcgi
The program 'spawn-fcgi' can be found in the following packages:
 * cherokee
 * lighttpd
Try: apt-get install <selected package>
-su: spawn-fcgi: command not found


```> **fujikofujio said:**
> 
 
type sudo su

copy the sample config file

Where is the sample config file to copy ?
I checked 
```

root@tapas-laptop:/usr/src/lighttpd-1.4.x# find / -name lighttpd.conf
/usr/src/lighttpd-1.4.x/doc/config/lighttpd.conf
/usr/src/lighttpd-1.4.x/tests/lighttpd.conf

```which one are you referring ?

In fact I tried what you mentioned below 
> **fujikofujio said:**
> 
  
    mkdir /etc/lighttpd

    cp doc/lighttpd.conf /etc/lighttpd/

but above step was not correct
I had to do 
```

cp doc/config/lighttpd.conf /etc/lighttpd/

```> **fujikofujio said:**
> 
   
log folder

    mkdir /var/log/lighttpd


Done

> **fujikofujio said:**
> 
   
we need to create a startup file in the /etc/init.d folder
Go here to download the startup script [http://redmine.lighttpd.net/projects/lighttpd/wiki/ScriptsUbuntu](http://redmine.lighttpd.net/projects/lighttpd/wiki/ScriptsUbuntu)
create a file called lighttpd in the /etc/init.d/ folder and then

    chmod a+x /etc/init.d/lighttpd

Done
Then
> **fujikofujio said:**
> 
    
Create a user to run lighttpd: if you have installed lighttpd 1.4 from apt or apache you can just use the www-data user again

    adduser -m -d /var/www -s /sbin/nologin lighttpd

got following errors

```

root@tapas-laptop:/etc/init.d# adduser -m -d /var/lighttpd/ -s /sbin/nologin lighttpd
Unknown option: m
Option d is ambiguous (debug, disabled-login, disabled-password)
Option s is ambiguous (shell, system)
adduser [--home DIR] [--shell SHELL] [--no-create-home] [--uid ID]
[--firstuid ID] [--lastuid ID] [--gecos GECOS] [--ingroup GROUP | --gid ID]
[--disabled-password] [--disabled-login] [--encrypt-home] USER
   Add a normal user

adduser --system [--home DIR] [--shell SHELL] [--no-create-home] [--uid ID]
[--gecos GECOS] [--group | --ingroup GROUP | --gid ID] [--disabled-password]
[--disabled-login] USER
   Add a system user

adduser --group [--gid ID] GROUP
addgroup [--gid ID] GROUP
   Add a user group

addgroup --system [--gid ID] GROUP
   Add a system group

adduser USER GROUP
   Add an existing user to an existing group

general options:
  --quiet | -q      don't give process information to stdout
  --force-badname   allow usernames which do not match the
                    NAME_REGEX[_SYSTEM] configuration variable
  --help | -h       usage message
  --version | -v    version number and copyright
  --conf | -c FILE  use FILE as configuration file



```> **fujikofujio said:**
> 
    
Modify the lighttpd file from /etc/init.d/ to match the user you want to run it as

    chown www-data:www-data /var/log/lighttpd

then type

Did above
Could not proceed any where.

---

