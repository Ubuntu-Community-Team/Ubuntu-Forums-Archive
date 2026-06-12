---
title: "Apache is running multiple processes and it's eating RAM"
date: 2008-10-12
forum: Server Platforms
---

### Post by lelizondob on 2008-10-12
Hi, I'm running a Hardy Server on an old laptop with WIFI and 256 MB on RAM, mainly for a LAMP server and File sharing. 

I haven't had problems at all since I installed it about 3 months ago. But suddenly, after an upgrade I started to have a huge problem with Hardy.

Apache is running multiple Processes, about 10-13 all the time, if I kill a process Apache will just open another one.

The problem with this is that apache is just eating about 210MB, of RAM, even the swap partition is always 50+% used. If I kill every Apache's process or restart, I use only like 128 MB and no swap. But after 30 minutes everything gets really slow again.

I just don't know what to do. A Drupal site hosted on my server it just too slow, every page load takes about 30-45 seconds, when usually I took about 1-3 seconds.

What can I do to fix this? I am sure that the slow problem is related to the amount of memory used.

Here is the table of processes running:

```

ID 	Owner 	Size 	Command
5593 	mysql 	135556 kB 	/usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file ...
7198 	www-data 	51040 kB 	/usr/sbin/apache2 -k start
7200 	www-data 	50652 kB 	/usr/sbin/apache2 -k start
6100 	www-data 	49500 kB 	/usr/sbin/apache2 -k start
6997 	www-data 	49260 kB 	/usr/sbin/apache2 -k start
7026 	www-data 	49236 kB 	/usr/sbin/apache2 -k start
7281 	www-data 	48488 kB 	/usr/sbin/apache2 -k start
7197 	www-data 	47896 kB 	/usr/sbin/apache2 -k start
7051 	www-data 	47456 kB 	/usr/sbin/apache2 -k start
7280 	www-data 	44436 kB 	/usr/sbin/apache2 -k start
5250 	root 	24836 kB 	/usr/sbin/apache2 -k start
7279 	www-data 	24836 kB 	/usr/sbin/apache2 -k start
7414 	root 	14888 kB 	/usr/share/webmin/proc/index_size.cgi
6676 	root 	11484 kB 	/usr/sbin/smbd -D
5668 	root 	10396 kB 	/usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
5119 	root 	10124 kB 	/usr/sbin/smbd -D
5235 	root 	10124 kB 	/usr/sbin/smbd -D
5173 	root 	8208 kB 	/usr/sbin/winbindd
5205 	root 	8092 kB 	/usr/sbin/winbindd
5136 	root 	8084 kB 	/usr/sbin/winbindd
5220 	root 	8084 kB 	/usr/sbin/winbindd
7077 	root 	7720 kB 	/usr/sbin/console-kit-daemon
5117 	root 	6532 kB 	/usr/sbin/nmbd -D
4998 	root 	5920 kB 	/usr/sbin/cupsd
5097 	postfix 	5444 kB 	qmgr -l -t fifo -u
7413 	postfix 	5404 kB 	pickup -l -t fifo -u -c
5077 	root 	5396 kB 	/usr/lib/postfix/master
4693 	root 	5316 kB 	/usr/sbin/sshd
4661 	root 	4112 kB 	/usr/bin/system-tools-backends
4625 	klog 	3272 kB 	/sbin/klogd -P /var/run/klogd/kmsg
1 	root 	2844 kB 	/sbin/init
4647 	messagebus 	2564 kB 	/usr/bin/dbus-daemon --system
5517 	dhcp 	2440 kB 	dhclient wlan0
2614 	root 	2404 kB 	/sbin/udevd --daemon
5221 	root 	2104 kB 	/usr/sbin/cron
5206 	daemon 	1984 kB 	/usr/sbin/atd
7399 	syslog 	1936 kB 	/sbin/syslogd -u syslog
4459 	root 	1928 kB 	/usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
4623 	root 	1872 kB 	/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
5554 	root 	1772 kB 	/bin/sh /usr/bin/mysqld_safe
4315 	root 	1716 kB 	/sbin/getty 38400 tty4
4316 	root 	1716 kB 	/sbin/getty 38400 tty5
4320 	root 	1716 kB 	/sbin/getty 38400 tty2
4321 	root 	1716 kB 	/sbin/getty 38400 tty3
4323 	root 	1716 kB 	/sbin/getty 38400 tty6
5682 	root 	1716 kB 	/sbin/getty 38400 tty1
5595 	root 	1700 kB 	logger -p daemon.err -t mysqld_safe -i -t mysqld
2 	root 	0 kB 	[kthreadd]
3 	root 	0 kB 	[migration/0]
4 	root 	0 kB 	[ksoftirqd/0]
5 	root 	0 kB 	[watchdog/0]
6 	root 	0 kB 	[events/0]
7 	root 	0 kB 	[khelper]
41 	root 	0 kB 	[kblockd/0]
44 	root 	0 kB 	[kacpid]
45 	root 	0 kB 	[kacpi_notify]
112 	root 	0 kB 	[kseriod]
145 	root 	0 kB 	[kswapd0]
187 	root 	0 kB 	[aio/0]
1410 	root 	0 kB 	[ksuspend_usbd]
1414 	root 	0 kB 	[khubd]
1480 	root 	0 kB 	[ata/0]
1487 	root 	0 kB 	[ata_aux]
1507 	root 	0 kB 	[scsi_eh_0]
1510 	root 	0 kB 	[scsi_eh_1]
2447 	root 	0 kB 	[kjournald]
2783 	root 	0 kB 	[kpsmoused]
2927 	root 	0 kB 	[pccardd]
2931 	root 	0 kB 	[pccardd]
3724 	root 	0 kB 	[ntos_wq]
3726 	root 	0 kB 	[ndis_wq]
3728 	root 	0 kB 	[wrapndis_wq]
4494 	root 	0 kB 	[kondemand/0]
7272 	root 	0 kB 	[pdflush]
7295 	root 	0 kB 	[pdflush]

```

Thanks.

Luis

---

### Post by windependence on 2008-10-12
This is how Apache is SUPPOSED to work. It spawns a new process for each server request.

I am not trying to be nasty here but you're hosting a website on an old laptop with only 256M of RAM and you're complaining because it's slow? What on earth do you expect? I suppose you are also running a GUI on it?

You can't make chicken salad out of chicken $ h i t.

-Tim

---

### Post by lelizondob on 2008-10-12
I was running Gnome and even then the server was really fast. 

The only thing I can't understand is why now it's slow, when before it was fast. Even after I removed gnome and upgraded.

Luis

---

### Post by lykwydchykyn on 2008-10-12
Do you have an idea of the traffic you're getting on this site?  Maybe you should run webalizer or somthing against the logs and see if you've gotten a traffic spike recently.

---

### Post by tomchuk on 2008-10-13
That memory usage per apache process looks about right for serving a Drupal site. A single Drupal page view can use more than 32MB. If you're running out of memory, you have 2 choices: add [more RAM](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010260381%201309121113&bop=And&Order=PRICE), or reduce the number of Apache processes hanging around and hope there are enough left to handle the traffic.

In /etc/apache2/apache2.conf, replace the values with something like this:
```

Timeout 10
KeepAlive On
MaxKeepAliveRequests 0
KeepAliveTimeout 3

<IfModule prefork.c>
StartServers       5
MinSpareServers    0
MaxSpareServers    2
MaxClients         20
MaxRequestsPerChild 100
</IfModule>

```

If you're generating pages in about 1s (on average between dynamic pages and images/css/etc.) that should leave you enough to handle 20 req/s which is a moderate amount of traffic when you're talking a drupal site on a small machine.

Mysql seems to be using more than 1/2 your memory, most of that is probably cache and it's not helping matters if that is getting swapped out. Drop your mysql caches significantly, you simply don't have the RAM to get away with it. Keep max_allowed_packet set to 8M or higher if you're using views. 8 or 16M should be fine for your query_cache, and if you have no bdb or innodb tables, make sure your skip-bsb and skip-innodb options are set.

If most of your drupal traffic is anonymous, turn on page caching (/admin/settings/performance) and you'll be generating pages in a couple queries rather than dozens. Also, turn on CSS aggregations (the more you can send in one response the better), and if your on D6 turn on JS aggregation or get the JS aggregation module for D5.

Another option is to reduce the amount of memory you're giving to mysql and apache, and run an 8MB memcached instance and use the [drupal memcache module](http://drupal.org/project/memcache). This should easily triple the speed at which you are generating dynamic pages for anonymous users which means more req/s.

Yet another option if you're on D5 is the [boost module](http://drupal.org/project/boost) which saves rendered pages to disk and apache serves them directly. This is extremely fast, though only works for anonymous users. You'll see the memory usage for your average apache process drop quite significantly as php will be involved in far fewer of your requests.

Also, double check that you don't have any modules enabled that you're not using - not loading a bunch of code is a great way to reduce your memory usage.

I run several Drupal sites off of a 160MB VPS server with no problem, I also run one Drupal site across 3 web servers, 1 memcached server, 1 monster DB server and a file server with Akamai sitting in front of all that. Traffic makes all the difference. As long as you're not ending up on the Digg homepage every day, 256MB should be fine, just be careful about what you're running and how much memory you're throwing at long-running processes.

---

### Post by lelizondob on 2008-10-13
Thanks a lot tomchuk, made the changes to apache conf and everything is back to normal, maybe after the upgrade it was replaced (I don't really know).

The server has less than 30 minutes running so I hope apache isn't fast because I just started it. But right now only 130.49 mb are being used, no swap.

The server is mainly for development so there's no one accessing the site but me, so I will be very worried if it gets to the Digg homepage :)

Thanks for the modules, didn't know about them and they will help me on some other Drupal sites.

Luis

---

### Post by iansane on 2011-06-02
Yeah it's an old thread but...
Problem still occurs 2 years later in natty. Tomchuk's solution fixes it.
Thanks Tomchuk

I use my home PC for a dev server with desktop and gnome to make coding locally quick and easy and then send a client to my url to see the test site. This really helped as a site would time out loading when the number of apache2 processes grew over night and slowed my server down. The client would call in the morning saying the site would not load. Makes me look bad to the client.

On a related note for anyone reading this, if you also have multiple mysql make sure your sites/web-apps close the mysql connection asap after finishing queries. This was also slowing me down until I figured out I had left that step out in a couple of scripts.

And as for using htop to view processes, I just learned that in many cases what I thought were multiple processes was actually misrepresented threads in a single process. Confusion resolved by using setup>display options and checking "show threads in a different color".

---

