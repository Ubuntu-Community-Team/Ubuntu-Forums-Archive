---
title: "Ubuntu VPS server"
date: 2009-12-03
forum: Server Platforms
---

### Post by daddysmonsters on 2009-12-03
So I'm taking a leap and have purchased a vps setup. The default install is ubuntu 8.04 now I'm fairly familiar with ubuntu and using apt from the command line etc. But I have a few questions that I hope someone can shed some light on.

1. Should I stick with 8.04?  (I know it's stable and this is a server environment but I can't apt-get anything as it's so bloody old and I'm not sure it seems like a good idea to find packages to install that may be out of date etc. So would it be wiser to update and be able to utilize the newer repos etc?

2. What would be a benenfit or downside of trying lamp? I can tell you my site will be a social networking script with anywhere from 50 - 100 users however we will need ffmpeg and red5 at some point and the scrip as it is right now is fairly heavy not familiar with lamp and how well it would handle things.

3. and lastly would anyone have recommendations for a site or two that have community driven support for budding web developers? I can make my way through php and can handle some ajax etc can query sql piece of cake but a site that is geared toward setting up the servers and the processes that run on them would be helpful. (and yes I can read the apache docs etc I mean more of a community) 

thanks for any input you may have it's appreciated.

---

### Post by daddysmonsters on 2009-12-05
bump?

---

### Post by munky99999 on 2009-12-05
> 1. Should I stick with 8.04? (I know it's stable and this is a server environment but I can't apt-get anything as it's so bloody old and I'm not sure it seems like a good idea to find packages to install that may be out of date etc. So would it be wiser to update and be able to utilize the newer repos etc?

IT is possible to add the newer repos without upgrading; though doing so will suggest you to upgrade.

> 2. What would be a benenfit or downside of trying lamp?
Time and energy?

> I can tell you my site will be a social networking script with anywhere from 50 - 100 users however we will need ffmpeg and red5 at some point and the scrip as it is right now is fairly heavy not familiar with lamp and how well it would handle things.

Well If you want a site. You sort of need lamp or something fairly similar.

> 3. and lastly would anyone have recommendations for a site or two that have community driven support for budding web developers? I can make my way through php and can handle some ajax etc can query sql piece of cake but a site that is geared toward setting up the servers and the processes that run on them would be helpful. (and yes I can read the apache docs etc I mean more of a community)

Here i guess? I like the ubuntu community wikis.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by brettg on 2009-12-05
The correct answer to the question "which os should I choose" has always been "well it depends on what apps you want to run"

So, what you need to do is decide what you are going to be running. Is it standard apache? With PHP? What PHP app will you run? 

Once you have answered these questions, you can then move on to the next question, which is what version of these apps are available on hardy versus the version available in the later releases? 

If there are significant version differences, then what does that mean in terms of functionality? Does the latest and greatest version offer any new functionality that you would actually use?

Personally, I run all my servers on hardy except for one, which is running Jaunty. (I steer clear of Karmic at the moment because I use a lot of vmware stuff which doesn't yet work on karmic)

Usually, there is very little reason to use a non LTS release. I only do that when a feature or app that I truly need is not available at a sufficient version number to run it on hardy without having to resort to manual building or mucking about with packages for different releases.

My advice is to stick with hardy. If you get to a point where you discover you need something that is only available in a later release then you can simply do a dist-upgrade from there.

P.S. as a final note, newer versions of apps are often available in hardy, but are distinguished by the version number. For example, in hardy, the web cache app "squid" is version 2.2 by default. However, squid version 3 is available too Simply apt-get install squid3 to get the newer version.

---

### Post by daddysmonsters on 2009-12-08
As far as what I am running the script I use requires php, and sql server for the db and of course your web servers core software apache.
 
I'm thinking php5
sql think it could be 4 or later.
Apache 2 should suffice as far as I know and at some point I will discover what mods need installed mod_ssl for example.
 
My issue is that hardy seems the way to go, but I'm concerned that apt-get is not configured is there a archived repo for it that is still active? I can edit the sources list but not sure with repo to go with. Also would you recommend lamp or xampp vs manually installing each individual service I need? Would lampp or xampp prohibit easy extension later on down the road? If anyone has any hands on with either of those two I would appreciate it.

---

### Post by ritm0o on 2010-01-01
[CENTER][B][COLOR=Red][SIZE=6]Hi guys,[/SIZE]
[/COLOR][/B]

**[SIZE=4][COLOR=Red]:KS----> How can Install a dedicated server or a VPS On  Ubuntu  Server 8.04 LTS[/COLOR][/SIZE]**

Now Look Carefully i will explain step by step .
how can u make [SIZE=5][COLOR=Red]vps[/COLOR][/SIZE] or [SIZE=3][COLOR=Red]dedicated server[/COLOR][/SIZE]
on [SIZE=5][COLOR=Red]ubuntu[/COLOR][/SIZE].
**:KS[COLOR=Red]---->[/COLOR][COLOR=Teal]Installing Ubuntu Server[/COLOR]**

 
 [B]Install Ubuntu normally using the Installation Instruction  on Ubuntu's web site.
[/B]
 **When you reach the stage of selecting a Package task, only select [B]OpenSSH server**. Do *not*  select **LAMP server** nor **Mail server**. We  will do those manually later, in order to control exactly what gets  installed.[/B]
 **[SIZE=4][COLOR=Red]<-----[/COLOR][/SIZE][COLOR=Teal]Configuring a Static IP address[/COLOR]****[SIZE=4][COLOR=Red]----->[/COLOR][/SIZE]**

 **[COLOR=Red]Note:[/COLOR] If you are on a VPS, skip this section. In fact, you can lose  access to your server inadvertently if you make a mistake here.**
 **When the system reboots, you need to assign a static address to it if  it is a live server.**
 **Edit the file */etc/network/interfaces* to be as follows.  Replace the IP address in the [B]address** and **gateway**  with the correct values.[/B]

 [COLOR=Red][B]auto eth0
iface eth0 inet static
  address 192.168.0.240
  netmask 255.255.255.0
  gateway 192.168.0.1
[/B][/COLOR][COLOR=Red]**Restart  the networking stack.**[/COLOR]
 [B][COLOR=Red]# /etc/init.d/networking restart[/COLOR]
[/B]**If this is a remote  server, with no console access, then it is best if you double check the  settings and reboot instead of restarting the network.**
 [SIZE=4]**[COLOR=Red]<---[/COLOR][COLOR=Teal]Update to the latest packages[/COLOR]****[COLOR=Red]---->[/COLOR]**[/SIZE]

  **If you are installing from a CD, then the repository would have  updated packages that are more recent than the ones on your CD. Before  we install any software, let us make sure that we have the latest  packages **
 [B][COLOR=Red]# aptitude update && aptitude dist-upgrade[/COLOR]
[/B]** If  the upgrade includes new kernel versions, we need to reboot now, so that  we don't have to do it later.**
 
 [COLOR=Red]# shutdown -r now[/COLOR]
**:KS[COLOR=Red]--->[/COLOR][COLOR=Teal]Install Apache, MySQL and PHP5[/COLOR]**

 **We now proceed with installing Apache, MySQL and PHP5 (the AMP part  of the LAMP software stack).**
 [B]For a mail server, we first install postfix as a personal preference.  Ubuntu provides exim4 by default. If you are more comfortable with  exim4 as a mail server, then skip this step. Ubuntu will install exim4  as part of the LAMP stack automatically.
[/B]
 [B][COLOR=Red]# aptitude install postfix[/COLOR]
[/B]**When prompted, select *"Internet  site".***
 **Then we install [COLOR=Red]Apache2:[/COLOR]**
 [COLOR=Red]**# aptitude install apache2 apache2-threaded-dev**[/COLOR]
[B]After  that we install the MySQL database server:
[/B]
 [B][COLOR=Red]# aptitude install mysql-server[/COLOR]
[/B]**When asked for a root  password for MySQL, just hit Enter.**
 **And then we follow that by PHP5, PHP5's image handling (gd) and its  connection to [COLOR=Red]MySQL:[/COLOR]**

 [B][COLOR=Red]# aptitude install php5 php5-gd php5-mysql[/COLOR]
[/B][B]Finally, we  install a few packages that would allow us to install things from PHP's  PECL and PEAR repositories. This would make installing apc and xdebug  far easier than doing that from source.
[/B]
 [COLOR=Red]**# aptitude install php5-dev php-pear make**[/COLOR]
[B][COLOR=Red]
Optional [SIZE=4]<----[/SIZE][/COLOR][SIZE=4][COLOR=Teal]Install APC[/COLOR][/SIZE][SIZE=4][COLOR=Red]---->[/COLOR][/SIZE][/B]

 [B]If this is a live server, it is recommended that you install APC to  boost PHP's performance.
[/B]
 [B][COLOR=Red]# pecl install apc[/COLOR]
[/B]** Create a config file for it named [COLOR=Red] /etc/php5/conf.d/apc.ini[/COLOR]**
 **Put the following lines in it:**
 [B]extension=apc.so
apc.shm_size=40[/B]
[B][COLOR=Red]
Optional [SIZE=4]<-----[/SIZE][/COLOR][SIZE=4][COLOR=Teal]Install X Cache[COLOR=Red]----->[/COLOR][/COLOR][/SIZE]
[/B]

 [B]Alternatively, you can use the XCache op-code cache.
[/B]
 [B]# aptitude install php5-xcache
[/B][B] [SIZE=4][COLOR=Red]<--If u don't know how can config xcache on ubuntu no pro after this article i will post xcache  config article.-->[/COLOR][/SIZE]
[/B]

**:KS[COLOR=Red]--->[/COLOR][COLOR=Teal][B]Optional: Install Xdebug**[/COLOR][/B]

 [B]If this is a development server, you may want to install Xdebug if  you are using a development environment that supports it.  It helps with  debugging and profiling PHP applications. 
[/B] 
**Different IDEs like Komodo, Eclipse and even vim have support for  Xdebug.**
 [B][COLOR=Red]# pecl install xdebug[/COLOR]
[/B]**[SIZE=4][COLOR=Red]<[/COLOR][/SIZE][COLOR=Red]---[/COLOR]We have an article on using [COLOR=Red]vim and Xdebug for debugging Drupal[/COLOR] that you may want to check after end this article.**---[SIZE=4]**[COLOR=Red]>[/COLOR]**[/SIZE]

 **:KS[COLOR=Red]--->[/COLOR][COLOR=Teal]Increase the memory for PHP[/COLOR]**

 [B]Ubuntu has changed the default for PHP's maximum memory size for  scripts often. It used to be 8MB, then was pushed to 128MB with 7.10,  and now with 8.04, it is back to 16MB. While this is adequate for  Drupal's core, installing several contributed modules will often exhaust  that. So start with 32MB by editing the file [COLOR=Red]*/etc/php5/apache2/php.ini**memory_limit*[/COLOR] line to:
[/B]  and change the 
 [COLOR=Red][B]memory_limit = 32M
[/B][/COLOR][B]
:KS[COLOR=Red]--->[/COLOR][COLOR=Teal]Configure Apache's mod_rewrite[/COLOR][/B]

 [B]Drupal's Clean URLs are a very useful feature. It requires the Apache  mod_rewrite.
[/B] 
 [B]First, enable the Apache module by executing this command:
[/B]
 [B][COLOR=Red]# a2enmod rewrite[/COLOR]
[/B]**Then, edit the file [COLOR=Red]*/etc/apache2/sites-enabled/000-default*[/COLOR],  and change this section:**
 [B][COLOR=Red]<Directory /var/www/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>[/COLOR]
[/B]**So  the line will be:**
 [COLOR=Red]**AllowOverride All**[/COLOR]
[B]
[SIZE=4][COLOR=Red]<-----[/COLOR][/SIZE][SIZE=4][COLOR=Teal]More Apache Configuration[/COLOR][/SIZE][SIZE=4][COLOR=Red]----->[/COLOR][/SIZE][SIZE=4]
[/SIZE][/B] 
 **There are a few Apache modules that are not really needed. We better  disable them to save some memory.**
 [B][COLOR=Red]# a2dismod cgi
# a2dismod autoindex[/COLOR]
[/B]**We may also get  better performance if we compress the HTML before we send it to the  browser. For this we enable the deflate module.**
 [COLOR=Red][B]# a2enmod deflate
[/B][/COLOR][COLOR=Teal]**Finally, restart Apache**[/COLOR]
 [COLOR=Red][B]# /etc/init.d/apache2 restart
[/B][/COLOR][B]
[SIZE=4][COLOR=Red]<-----[/COLOR][/SIZE][SIZE=4][COLOR=Teal]Download and Extract Drupal[/COLOR][/SIZE][/B][SIZE=4][COLOR=Red]----->[/COLOR][/SIZE]

 [B]First download Drupal by doing this:
[/B]
 [B][COLOR=Red]# cd /tmp/[/COLOR]
[COLOR=Red]# wget [http://ftp.osuosl.org/pub/drupal/files/projects/drupal-6.2.tar.gz](http://ftp.osuosl.org/pub/drupal/files/projects/drupal-6.2.tar.gz)[/COLOR]
[/B]**Then  extract the tarball**
 [B][COLOR=Red]# cd /var/www/
# tar xzvf /tmp/drupal-6.2.tar.gz[/COLOR]
[/B]**  Move the files to the web root of the server**
 [B][COLOR=Red]# mv drupal-6.2/* /var/www[/COLOR]
[/B]** And don't forget the hidden  file ...**
 [B][COLOR=Red]# mv drupal-6.2/.htaccess /var/www[/COLOR]
[/B]** Remove the file *index.html*,  so Drupal's *index.php* will be the one that is executed by  Apache**
 [B][COLOR=Red]# rm index.html[/COLOR]
[/B][B]Then change the permissions of the  directory to the user that Apache runs as: www-data
[/B]
 [COLOR=Red]**# chown -R www-data:www-data /var/www**[/COLOR]
[B]


[SIZE=4][COLOR=Red]<-----[/COLOR][/SIZE][SIZE=4][COLOR=Teal]Create the  Drupal database[/COLOR][/SIZE][/B][SIZE=4][COLOR=Red]----->[/COLOR][/SIZE]

 [B]The following command will create a database for Drupal:
[/B] 
 [B][COLOR=Red]# mysqladmin create db[/COLOR]
[/B]**Then grant privileges to it:**
 [COLOR=Red][B]# mysql
mysql> GRANT ALL PRIVILEGES ON db.* TO user@localhost IDENTIFIED BY 'something';
mysql> FLUSH PRIVILEGES;[/B][/COLOR]
[B]
:KS[COLOR=Red]--->[/COLOR][COLOR=Teal]Installing  Drupal[/COLOR][/B]

 **We are now ready to install Drupal.**
 **Point your browser to the server [COLOR=Red](e.g. *[http://example.com](http://example.com)*)[/COLOR]  and you should be greeted by Drupal's installer.**
 **You will need to use the following values:**
 [B] [COLOR=Red] Database name:[/COLOR] *db*
[/B]
 [B]  [COLOR=Red]Database user name:[/COLOR] *user*
[/B]
 [B][COLOR=Red]  Database password:[/COLOR] *something*
[/B]
 [COLOR=Red]**Enjoy ...**[/COLOR]  

[RIGHT][SIZE=4][COLOR=DarkRed]**ritm0o[SIZE=1]([COLOR=Red]Research on Linux,ubuntu[/COLOR])[/SIZE]**[/COLOR][/SIZE]
[COLOR=Teal]South Korea[/COLOR]
[COLOR=Red]tigerhost@gmail.com[/COLOR]
[/RIGHT]

[/CENTER]

---

### Post by ritm0o on 2010-01-01
[CENTER][B][COLOR=Red]:KS XCache Config:KS


[/COLOR][/B]** It is now time to update this benchmark and include XCache as well. **
 **[COLOR=Teal][B]Configuration**[/COLOR][/B]

 ** The tests were run on the following configuration: **
 **[B]Hardware**[/B]

 ** [COLOR=Red]AMD Athlon 64 X2 Dual Core Processor 4400+ @ 2.2GHz, 1MB cache and 2GB  RAM. 160GB SATA 7200RPM hard disk. [/COLOR]**
 **[B]Software**[/B]

 ** [COLOR=Red]GNU/Linux Ubuntu server Gutsy 7.10, Apache 2.2.4, MySQL 5.0.45 and PHP  5.2.3. [/COLOR]**
 **[B]Drupal**[/B]

 ** The tests were run on Drupal 6.3-dev, checked out from CVS. Views and  CCK are installed and enabled, but there are no views nor CCK types  defined. **
 ** Using the devel generate module, we created 2,000 users, 5 vocabularies,  and 50 terms. We then created 2,000 nodes of type page and story, with 5  comments each, and assigned terms to them.**
 **All Drupal caching is disabled. **
 **[COLOR=Teal][B]PHP op-code caches**[/COLOR][/B]

 ** We used the following versions of each op-code cache, we also note how  it was installed, and what the configuration details we used: **
 **[COLOR=Red][B]XCache**[/COLOR][/B]

 ** XCache is a spinoff of the [COLOR=Red]lighttpd[/COLOR] web server. It is currently maintained. **
 ** We used version: 1.2.1, which is available from the APT repositories for  Ubuntu Gutsy, as [B]php5-xcache**. [/B]
 ** Being available in the Ubuntu/Debian repositories means that installing  Xcache was the easiest of the bunch using aptitude. **
 ** Configuring XCache requires some parameters to change though if you want  the cache to be in memory though. We used the following configuration  to change the file which resides in[COLOR=Red] [B]/etc/php5/conf.d/xcache.ini**. [/COLOR][/B]
 [COLOR=Red][xcache]
xcache.shm_scheme =        "mmap"
xcache.size  =                48M
xcache.count =                 2
xcache.slots =                8K
xcache.ttl   =                 0
xcache.gc_interval =           0
xcache.readonly_protection = Off
xcache.mmap_path =           "/var/cache/xcache.mmap"
xcache.coredump_directory =  ""
xcache.cacher =              On
xcache.stat   =              On
xcache.optimizer =           Off
xcache.var_size  =            0M
xcache.var_count =             1
xcache.var_slots =            8K
xcache.var_ttl   =             0
xcache.var_maxttl   =          0
xcache.var_gc_interval =     300
xcache.test =                Off 
[/COLOR]**[COLOR=Red]eAccelerator[/COLOR]**

 [COLOR=Red] eAccelerator is a fork of an older op-code cache called Turck MMCache  that has been abandoned. eAccelerator development seems to have been  slow of late, and is not keeping up with the latest versions of PHP 5.  We found that eAccelerators can be unstable with newer versions of PHP  and Drupal, and Apache will die with segmentation faults often. We had  to use the [SIZE=4][COLOR=Teal]**logwatcher script **[/COLOR][/SIZE] for restarting Apache automatically when this  happens, but it was too frequent in some cases to be a real nuisance. [/COLOR]
 [COLOR=Red] We used version v0.9.5.2, which is the latest stable release. [/COLOR]
 [COLOR=Red] It was installed from source using the following commands: [/COLOR]
 [COLOR=Red]phpize
./configure
make
make install 
[/COLOR][COLOR=Red] We used the following configuration which resides in **/etc/php5/conf.d/eaccelerator.ini**. [/COLOR]
 [COLOR=Red]zend_extension                  = /usr/lib/php5/20060613/eaccelerator.so
eaccelerator.shm_size           = 48
eaccelerator.cache_dir          = /var/cache/eaccelerator
eaccelerator.enable             = 1
eaccelerator.optimizer          = 1
eaccelerator.check_mtime        = 0
eaccelerator.debug              = 0
eaccelerator.filter             = ""
eaccelerator.shm_max            = 0
eaccelerator.shm_ttl            = 0
eaccelerator.shm_prune_period   = 0
eaccelerator.shm_only           = 1
eaccelerator.compress           = 1
eaccelerator.compress_level     = 9  
[/COLOR]**[COLOR=Red]APC[/COLOR]**

 [COLOR=Red] APC is a PECL package that is maintained by the core PHP developers,  including Gopal and Rasmus. It has several advantages including a very  simple configuration, and close tracking of PHP versions. Being actively  maintained is a big plus for APC. [/COLOR]
 [COLOR=Red] We used version 3.0.16 of APC. It was installed using PECL, via the  following command: [/COLOR]
 [COLOR=Red]pecl install apc 
[/COLOR][COLOR=Red] The configuration for APC is very minimalistic. We used the following  configuration file in **/etc/php5/conf.d/apc.ini**. [/COLOR]
 [COLOR=Red]extension                 = apc.so
apc.shm_size              = 48
[/COLOR]**[COLOR=Red]Benchmarking methodology[/COLOR]**

 [COLOR=Red] We used the Apache Benchmark (ab) command, with a concurrency of 5, and  3,000 requests, like so: [/COLOR]
 [COLOR=Red]ab -c5 -n3000 [http://example.com/](http://example.com/) 
[/COLOR]**[COLOR=Red]Test 1: No PHP op-code cache[/COLOR]**

 [COLOR=Red] In this test, we established a baseline of how Drupal 6 would perform  without any op-code cache. [/COLOR]
 [COLOR=Red]Document Path:          /
Document Length:        21757 bytes
Concurrency Level:      5
Time taken for tests:   288.255212 seconds
Complete requests:      3000
Failed requests:        0
Write errors:           0
Total transferred:      66777000 bytes
HTML transferred:       65271000 bytes
Requests per second:    10.41 [#/sec] (mean)
Time per request:       480.425 [ms] (mean)
Time per request:       96.085 [ms] (mean, across all concurrent requests)
Transfer rate:          226.23 [Kbytes/sec] received
Connection Times (ms)
min  mean[+/-sd] median   max
Connect:        0    0   0.5      0      19
Processing:   181  479 186.0    444    1822
Waiting:      166  461 184.7    427    1708
Total:        181  479 186.0    444    1822
Percentage of the requests served within a certain time (ms)
50%    444
66%    525
75%    577
80%    619
90%    732
95%    819
98%    946
99%   1012
100%   1822 (longest request) [/COLOR][B] 
Using the devel module, we see that the page generation time for PHP is  around 200 ms. [/B]
 [B]Page execution time was 209.58 ms. Executed 101 queries in 9.6 milliseconds. 
[/B]** Memory utilization is consistent at 24MB per Apache process. Note that  the sixth colum (Resident Set Size) is what matters. **
 [COLOR=Red]                         Virt Res
13616 www-data  16   0  213M 24660  3744 S  0.0  1.2  0:51.37 /usr/sbin/apache2 -k start
13619 www-data  15   0  213M 24484  3824 S  0.0  1.2  0:51.37 /usr/sbin/apache2 -k start
13627 www-data  15   0  213M 24484  3824 S  0.0  1.2  0:50.95 /usr/sbin/apache2 -k start
13617 www-data  15   0  213M 24484  3824 S  0.0  1.2  0:50.14 /usr/sbin/apache2 -k start
13624 www-data  15   0  213M 24408  3748 S  0.0  1.2  0:48.99 /usr/sbin/apache2 -k start
13626 www-data  16   0  213M 24408  3748 S  0.0  1.2  0:50.07 /usr/sbin/apache2 -k start
13615 www-data  16   0  213M 24404  3744 S  0.0  1.2  0:51.03 /usr/sbin/apache2 -k start
13623 www-data  15   0  213M 24404  3744 S  0.0  1.2  0:49.39 /usr/sbin/apache2 -k start
13625 www-data  15   0  213M 24404  3744 S  0.0  1.2  0:52.95 /usr/sbin/apache2 -k start
13618 www-data  16   0  213M 24404  3744 S  0.0  1.2  0:49.93 /usr/sbin/apache2 -k start

 [/COLOR]**[COLOR=Teal][B]Test 2: eAccelerator**[/COLOR][/B]

 [COLOR=Red]Document Path:          /
Document Length:        21757 bytes
Concurrency Level:      5
Time taken for tests:   95.983986 seconds
Complete requests:      3000
Failed requests:        0
Write errors:           0
Total transferred:      66777000 bytes
HTML transferred:       65271000 bytes
Requests per second:    31.26 [#/sec] (mean)
Time per request:       159.973 [ms] (mean)
Time per request:       31.995 [ms] (mean, across all concurrent requests)
Transfer rate:          679.39 [Kbytes/sec] received
Connection Times (ms)
min  mean[+/-sd] median   max
Connect:        0    0   0.1      0       3
Processing:    57  159  91.3    148    3830
Waiting:       50  152  89.8    142    3704
Total:         57  159  91.3    148    3830
Percentage of the requests served within a certain time (ms)
50%    148
66%    174
75%    193
80%    205
90%    239
95%    263
98%    289
99%    309
100%   3830 (longest request)[/COLOR][B] 
Using devel, the PHP time is around 47 ms. A significant improvement  over not using an op-code cache. [/B]
 [B]Page execution time was 57.88 ms. Executed 101 queries in 9.01 milliseconds. 
[/B]** Memory utilization for Apache is as follows. The 30MB process size is  from the first run where the PHP scripts were loaded, parsed and  tokenized. The other processes are from the subsequent requests and they  range from 23MB to 18MB. **
 [COLOR=Red]                         Virt Res
9801 www-data  16   0  261M 30688 12644 S  0.0  1.5  0:14.96 /usr/sbin/apache2 -k start
9799 www-data  16   0  254M 23848 12588 S  0.0  1.2  0:15.89 /usr/sbin/apache2 -k start
9797 www-data  16   0  253M 22536 12272 S  0.0  1.1  0:15.74 /usr/sbin/apache2 -k start
9800 www-data  15   0  251M 20028 11832 S  0.0  1.0  0:14.08 /usr/sbin/apache2 -k start
9806 www-data  16   0  251M 18536 10396 S  0.0  0.9  0:14.74 /usr/sbin/apache2 -k start
9808 www-data  16   0  251M 18536 10396 S  0.0  0.9  0:14.83 /usr/sbin/apache2 -k start
9807 www-data  15   0  251M 18536 10396 S  0.0  0.9  0:14.67 /usr/sbin/apache2 -k start
9803 www-data  15   0  251M 18536 10396 S  0.0  0.9  0:15.62 /usr/sbin/apache2 -k start
9809 www-data  16   0  251M 18536 10396 S  0.0  0.9  0:14.07 /usr/sbin/apache2 -k start
9805 www-data  16   0  251M 18536 10396 S  0.0  0.9  0:14.16 /usr/sbin/apache2 -k start
[/COLOR]
 **[COLOR=Teal][B]Test 3: XCache  **[/COLOR][/B]

 [COLOR=Red]Document Path:          /
Document Length:        21757 bytes
Concurrency Level:      5
Time taken for tests:   99.76300 seconds
Complete requests:      3000
Failed requests:        0
Write errors:           0
Total transferred:      66777000 bytes
HTML transferred:       65271000 bytes
Requests per second:    30.28 [#/sec] (mean)
Time per request:       165.127 [ms] (mean)
Time per request:       33.025 [ms] (mean, across all concurrent requests)
Transfer rate:          658.19 [Kbytes/sec] received
Connection Times (ms)
min  mean[+/-sd] median   max
Connect:        0    0   0.0      0       2
Processing:    59  164  83.4    155    3367
Waiting:       52  156  66.4    148    1802
Total:         59  164  83.4    155    3367
Percentage of the requests served within a certain time (ms)
50%    155
66%    178
75%    196
80%    206
90%    237
95%    263
98%    287
99%    305
100%   3367 (longest request) 
[/COLOR]** Using devel, the page generation is around 50 ms. **
 [B] Page execution time was 59.37 ms. Executed 101 queries in 9.27 milliseconds.
[/B]** For memory utilization, you can see that it ranges from 29MB to 19MB, a  bit more than eAccelerator. **
 [COLOR=Red]  Virt Res
10316 www-data  16   0  263M 32316 11832 S  0.0  1.6  0:17.03 /usr/sbin/apache2 -k start
10319 www-data  15   0  259M 29976 13440 S  0.0  1.5  0:17.05 /usr/sbin/apache2 -k start
10318 www-data  15   0  261M 29724 11628 S  0.0  1.4  0:16.83 /usr/sbin/apache2 -k start
10317 www-data  16   0  254M 23576 12128 S  0.0  1.1  0:15.33 /usr/sbin/apache2 -k start
10322 www-data  15   0  251M 19624 11524 S  0.0  1.0  0:16.85 /usr/sbin/apache2 -k start
10328 www-data  15   0  251M 19624 11524 S  0.0  1.0  0:14.95 /usr/sbin/apache2 -k start
10324 www-data  15   0  251M 19624 11524 S  0.0  1.0  0:15.32 /usr/sbin/apache2 -k start
10325 www-data  15   0  251M 19624 11524 S  0.0  1.0  0:14.42 /usr/sbin/apache2 -k start
10327 www-data  16   0  251M 19624 11524 S  0.0  1.0  0:15.05 /usr/sbin/apache2 -k start[/COLOR][B][COLOR=Teal][B]

Test 4: APC[/B][/COLOR][/B]

 [COLOR=Red]Document Path:          /
Document Length:        21757 bytes
Concurrency Level:      5
Time taken for tests:   98.530068 seconds
Complete requests:      3000
Failed requests:        0
Write errors:           0
Total transferred:      66777000 bytes
HTML transferred:       65271000 bytes
Requests per second:    30.45 [#/sec] (mean)
Time per request:       164.217 [ms] (mean)
Time per request:       32.843 [ms] (mean, across all concurrent requests)
Transfer rate:          661.84 [Kbytes/sec] received
Connection Times (ms)
min  mean[+/-sd] median   max
Connect:        0    0   0.0      0       2
Processing:    58  163  71.2    155    2452
Waiting:       53  158  69.6    150    2329
Total:         58  163  71.2    155    2452
Percentage of the requests served within a certain time (ms)
50%    155
66%    178
75%    193
80%    204
90%    235
95%    258
98%    285
99%    302
100%   2452 (longest request) [/COLOR][B] 

Using devel, the page generation time is around 50 ms as well. [/B]
 [B]Page execution time was 59.8 ms. Executed 101 queries in 9.1 milliseconds. 
[/B]** Memory utilization is noticeably consistent at 21MB per process, more  than the other two op-caches, but suprisingly consistent. **
 [COLOR=Red] Virt Res
9263 www-data  16   0  263M 38172 18036 S  0.0  1.9  0:15.31 /usr/sbin/apache2 -k start
9266 www-data  15   0  252M 21704 13020 S  0.0  1.1  0:18.14 /usr/sbin/apache2 -k start
9270 www-data  15   0  252M 21604 12768 S  0.0  1.0  0:18.30 /usr/sbin/apache2 -k start
9274 www-data  15   0  252M 21604 12768 S  0.0  1.0  0:15.75 /usr/sbin/apache2 -k start
9264 www-data  16   0  252M 21520 12692 S  0.0  1.0  0:16.55 /usr/sbin/apache2 -k start
9267 www-data  15   0  252M 21520 12688 S  0.0  1.0  0:18.10 /usr/sbin/apache2 -k start
9268 www-data  16   0  252M 21520 12688 S  0.0  1.0  0:16.89 /usr/sbin/apache2 -k start
9269 www-data  15   0  252M 21520 12688 S  0.0  1.0  0:16.51 /usr/sbin/apache2 -k start
9273 www-data  16   0  252M 21520 12688 S  0.0  1.0  0:17.32 /usr/sbin/apache2 -k start
9275 www-data  16   0  252M 21520 12688 S  0.0  1.0  0:16.03 /usr/sbin/apache2 -k start
 [/COLOR]**[COLOR=Teal][B]:KSSummary:KS**[/COLOR][/B]

 ** [COLOR=Red]The following table summarizes the above results. [/COLOR]**
     




[LEFT]          [COLOR=DarkRed]Requests per  Sec[/COLOR]  [COLOR=DarkOrange]Single Request (millisec)[/COLOR]        [COLOR=Teal]Memory (Max, MB)[/COLOR]   [COLOR=Lime]Memory (Min, MB[/COLOR]) 
   [COLOR=Red]None :[/COLOR]    [COLOR=DarkRed]10.41[/COLOR]                [COLOR=DarkOrange]96.08   [/COLOR]                             [COLOR=Teal]   24  [/COLOR]                           [COLOR=Lime] 24    [/COLOR]
[COLOR=Red]eAccelerator[/COLOR]  [COLOR=DarkRed]31.26[/COLOR]          [COLOR=DarkOrange]31.99[/COLOR]                                 [COLOR=Teal]  23       [/COLOR]                     [COLOR=Lime] 18 [/COLOR]
   [COLOR=Red]XCache[/COLOR]       [COLOR=DarkRed] 30.28 [/COLOR]         [COLOR=DarkOrange] 33.02[/COLOR]                                [COLOR=Teal]  29 [/COLOR]                           [COLOR=Lime] 19[/COLOR]
[COLOR=Red] APC[/COLOR]             [COLOR=DarkRed]30.45 [/COLOR]          [COLOR=DarkOrange]32.84[/COLOR]                                 [COLOR=Teal] 21 [/COLOR]                         [COLOR=Lime]   21 [/COLOR]
[/LEFT]
 [B][COLOR=Teal][B]



Conclusions[/B][/COLOR][/B]

 ** From the above results, one can come to the following conclusions: **
 
[LIST]
[*]**All op-code caches provide a noticable improvement for Drupal over a  default PHP installation. **
[*]**The speed gain is about 3X.**
[*]**eAccelerator is marginally better than the XCache or APC both in  terms of speed and memory utilization.**
[*]**Installation of each op-code cache is different: one has a Debian  package, the other is installed from source and the third is via PECL.**
[*]**The configuration for each is also different. Some work well with a  default install, others require more tweaking.**
[/LIST]
 **[COLOR=Green][B]Update:**[/COLOR][/B]

 [B] We have noticed that in production, Xcache suffers from the same  instability that eAccelerator exhibits: segmentation fault after a day  or so. This happened with Xcache 1.2.1-3 which ships with Ubuntu 8.04.1,  and PHP 5.2.4. The latest stable release is 1.2.2 from Xcache's web  site. So, try compiling that from source, or install the
 [SIZE=4][COLOR=Red]logwatcher script
[/COLOR][/SIZE] if a minute of downtime is acceptable. 
[/B]


**[SIZE=4][COLOR=Red]Here is the :KSlogwatcher script:KS[/COLOR][/SIZE]**
[LEFT][COLOR=Red]<?php
// path to apache log file
//
define("DEFAULT_APACHE_LOG_PATH", "/var/log/apache2/error.log");

// command to use to restart apache
//
define("DEFAULT_APACHE_RESTART_COMMAND", "/etc/init.d/apache2 restart");

// defines the polling interval (in seconds)
//
define("DEFAULT_POLLING_INTERVAL", 45);

// defines the format for date outputted in log entries (RFC 2228 format date)
//
define("DATE_FORMAT", "[r]");

// where to log watcher status
//
define("LOG_OUTPUT_FILENAME", "/var/log/logwatcher.log");

// conditions to test for (action is top level array element key)
//
$array_action_checks = Array();
$array_action_checks['restart'] = Array('exit signal Segmentation fault');

// list of commands mapped to actions
//
$array_action_commands = Array('restart' => DEFAULT_APACHE_RESTART_COMMAND);

/************************************************************
 * [COLOR=Green]END CONFIGURATION, BEGIN IMPLEMENTATION [/COLOR]                 *
 ************************************************************/

$last_position = 0;
// main loop
//

if ($argc != 2) {
  log_message("Called with incorrect number of arguments");
  echo "Usage: php logwatcher.php [EMAIL="youremail@example.com"]youremail@example.com[/EMAIL]\n";
  exit(1);
}
else {
  $email = $argv[1];
}


log_message("logwatcher started");

while (true) {
  $last_position = check_file($last_position);
  sleep(DEFAULT_POLLING_INTERVAL);
}

function check_file($last_position) {
  $file_name = DEFAULT_APACHE_LOG_PATH;
  $fp = @fopen($file_name, "r");
  if ($fp == null) {
    die("unable to open file at $file_name\n");
  }
  if ($last_position == 0) {
    // first time through the file for this instance.. Skip to EOF
    //
    fseek($fp, 0, SEEK_END);
  } else {
    // seek to last known position to skip past already handled log entries
    //
    fseek($fp, $last_position, SEEK_SET);
  }

  // check for patterns on current line
  //
  $action_taken = false;
  while (($line = fgets($fp, 4096)) != null) {
    $action = check_line($line);
    if ($action != "") {
      // TODO: log that action is taken
      //
      // take action only once for a given seek, otherwise seek silently to EOF
      //
      if (!$action_taken) {
        log_message("Apache APC/eAccelerator caused a segmentation fault.");
        log_message("Executing: " . get_action_command($action));
        system(get_action_command($action));
        log_message("Executed: " . get_action_command($action));
        email_notify();
        log_message("Email notification sent");
        $action_taken = true;
      }
    }
  }
  // record end of file position for next pass through
  //
  $last_position = ftell($fp);

  // close the file pointer
  //
  fclose($fp);
  return $last_position;
}

function log_message($message) {
  error_log(date(DATE_FORMAT) . " " . $message . "\n", 3, LOG_OUTPUT_FILENAME);
}

function check_line($line) {
  global $array_action_checks;
  // walk through each action
  //
  foreach ($array_action_checks as $action => $array_checks) {
    foreach ($array_checks as $check) {
      // walk through each check and see if it matches the current line
      //
      if (preg_match("/" . $check . "/", $line)) {
        return $action;
      }
    }
  }
  return "";
}
function get_action_command($action) {
  global $array_action_commands;
  $command = @$array_action_commands[$action];
  if ($command == null) {
    log_message("Could not retrieve command for action: $action");
    return "";
  }
  return $command;
}


function email_notify() {
  $body = "The server has encountered an APC/eAccelerator segmentation fault error.
Apache has been automatically restarted.
The log file " .  LOG_OUTPUT_FILENAME . " should have the exact time and number 
that this happened.";

  mail($email, 'Apache has been restarted', $body);
} [/COLOR]
[COLOR=Red]And  here is the logwatcher.sh shell script that is used to start it. Change  the email addresses to fit your needs.[/COLOR]
 [COLOR=Red]#!/bin/sh

BASE_DIR=/root/bin
SCRIPT=$BASE_DIR/logwatcher.php
PID_FILE=/var/run/logwatcher.pid
EMAIL=someone@example.com,someoneelse@example.com

# If there is an old process, kill it
kill `cat $PID_FILE`
# Make sure the file is clean
rm -f $PID_FILE

cd $BASE_DIR
nohup php $SCRIPT $EMAIL> /dev/null &
PID=$!

echo $PID > $PID_FILE
[/COLOR][COLOR=Green]Now,  all you need to do is edit your **/etc/rc.local**, and add  a line to call the logwatcher.sh script upon booting[/COLOR][/LEFT]
[COLOR=Red]Enjoy...:guitar:[/COLOR]

[/CENTER]

---

### Post by ritm0o on 2010-01-01
[CENTER][SIZE=4][B][COLOR=Red]:KSvim and Xdebug for debugging Drupal:KS

Here is the Config

[/COLOR][/B][/SIZE]**[COLOR=Teal]Credits[/COLOR]**

 The xdebug interface for vim was written by Seung Woo Shin and is  available on [vim.org]("http://www.vim.org/scripts/script.php?script_id=1152"). A slightly modified version with a README  file is attached to this article.
 **[COLOR=Teal]Requirements[/COLOR] **

 To use this script, you have to get python 2.3 or higher, and []("http://xdebug.org/")[**xdebug 2.0**]("http://xdebug.org/") on your system  (we will cover the installation an configuration of xdebug in a future  article).
 **[COLOR=Teal]Installation[/COLOR]**

 Extract the debugger.py and debugger.vim files and place them in your  .vim/plugin directory (create it if it does not exist). 
 **[COLOR=Teal]Starting the debugger[/COLOR]**

 Start vim, and hit F5. A message will appear waiting for a debug  session to start and attach to your vim instance.
 Now, browse to the URL of the page causing you grief, and  add  XDEBUG_SESSION_START to the end of the URL.
 For clean URLs use: **[http://example.com/admin/feature?XDEBUG_SESSION_START=1](http://example.com/admin/feature?XDEBUG_SESSION_START=1)**  
 Otherwise use: **[http://example.com?q=admin/feature&XDEBUG_SESSION_START=1](http://example.com?q=admin/feature&XDEBUG_SESSION_START=1)**
  The debugger will start and several windows will appear in vim, with  Drupal's index.php showing.
 See a screen shot


[IMG]http://i795.photobucket.com/albums/yy240/ritm0o/vim-debug-start.png[/IMG]

 **[COLOR=Teal]Setting breakpoints[/COLOR]**

 Using the :e command in vim, open the file you are interested in  (e.g. feature.module in this case).
 Go to the function/line you suspect, and set a breakpoint using the  :Bp command.
 See a screenshot


[IMG]http://i795.photobucket.com/albums/yy240/ritm0o/vim-debug-set-breakpoint.png[/IMG]

 [B]
[/B]

**[COLOR=Teal]Debugging at a breakpoint[/COLOR]**

 Hit F4 to continue until the breakpoint is reached.
 See a screen shot



[IMG]http://i795.photobucket.com/albums/yy240/ritm0o/vim-debug-reaching-breakpoint.png[/IMG]
 []("http://2bits.com/sites/2bits.com/files/vim-debug-reaching-breakpoint.png")


 Once at the breakpoint, you can step through the program, display  variables, ...etc. 
 Use the function keys and commands on screen.
 **[COLOR=Teal]Displaying variables[/COLOR]**

 You can move the cursor to any variable, and hit F12 to see what is  in this variable.
 See a screenshot


[IMG]http://i795.photobucket.com/albums/yy240/ritm0o/vim-debug-displaying-variables.png[/IMG]

 **[COLOR=Teal]Evaluating an expression or variable[/COLOR]**

 Use the ,e command to evaluate an expression or print a variable.  This is handy in complex variables such as objects and arrays.
 See Screen shot


[IMG]http://i795.photobucket.com/albums/yy240/ritm0o/vim-debug-eval-variable.png[/IMG]



 Of course, there are many more uses for this, such as seeing how  Drupal handles things, and how elegant its internal architecture is. 
 **[COLOR=Teal]Desired functionality[/COLOR]**

 vim xdebug is very powerful yet simple. It is missing only one  feature, which is multi-user support. This requires the xdebug proxy to  be supported. This allows multiple sessions to connect to the proxy with  a different IDE Key (the argument for XDEBUG_SESSION_START).
 [COLOR=Red]**If someone adds that feature before I do, let me know. I have the  setup to test this if needed.**[/COLOR]




[LEFT][COLOR=Red]**Attachment:**[/COLOR]
[COLOR=Red][B][vim-xdebug.tar.gz]("http://2bits.com/sites/2bits.com/files/vim-xdebug.tar.gz")
[/B][/COLOR]
                                            
[/LEFT]
[CENTER]

**:( oh i'm so tired guys**.
[/CENTER]
[LEFT]
[/LEFT]
[COLOR=Red]**Enjoy...**[/COLOR]
[/CENTER]

---

### Post by daddysmonsters on 2010-01-21
Well it was nice of you to put all of that work in, but I'm not sure where a lot of it related to my original question. I decided to stick with the LTS release of ubuntu server so that was one, I've found a community to serve my needs as sadly ubuntu sever threads are flooded with questions and rarely get a decent response (not directed at you) And your installation instructions assume a lot of things I mean I am not installing drupal etc. 

You may want to create a tutorial with this though, as you could direct it at a specific demographic.

---

