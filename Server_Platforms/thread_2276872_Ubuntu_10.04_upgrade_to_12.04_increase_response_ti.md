---
title: "Ubuntu 10.04 upgrade to 12.04 increase response time in app"
date: 2015-05-05
forum: Server Platforms
---

### Post by jas5 on 2015-05-05
Hello community,

First time poster here, go easy on me :P Been working with Ubuntu for the last year or so and in quite the pickle right now with my web stack.

Breakdown:

We upgraded our ubuntu 10.04 servers to 12.04 hosted in the cloud and now have roughly 100ms increase in response time. I'm at wits end as all our code is the same, packages the same etc.

Running Nginx frontend with apache in the back. package details:

Nginx------
nginx                                         1.6.3-1~precise

Apache------
apache2                                     2.2.22-1ubuntu1.8
apache2-mpm-prefork                  2.2.22-1ubuntu1.8
apache2-utils                              2.2.22-1ubuntu1.8
apache2.2-bin                             2.2.22-1ubuntu1.8
apache2.2-common                      2.2.22-1ubuntu1.8

PHP------
libapache2-mod-php5                  5.4.39-1+deb.sury.org~precise+2
newrelic-php5                            4.20.2.95
newrelic-php5-common               4.20.2.95
php5                                        5.4.39-1+deb.sury.org~precise+2
php5-cli                                    5.4.39-1+deb.sury.org~precise+2
php5-common                           5.4.39-1+deb.sury.org~precise+2
php5-curl                                 5.4.39-1+deb.sury.org~precise+2
php5-dev                                 5.4.39-1+deb.sury.org~precise+2
php5-gd                                   5.4.39-1+deb.sury.org~precise+2
php5-mcrypt                            5.4.39-1+deb.sury.org~precise+2
php5-memcache                        3.0.8-1~precise+1
php5-memcached                       2.1.0-3~precise+1
php5-mysql                              5.4.39-1+deb.sury.org~precise+2
php5-readline                           5.4.39-1+deb.sury.org~precise+2

What I have thus far identified/tried

We have a serious amount of TCP connections in TIME_WAIT roughly 30k-40k in peak times.

I have modified some these settings being able to bring down the TIME_WAIT connections to about 10k

[FONT=arial]---- Old ---------------[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Nginx -[/FONT]
[FONT=arial]timeout = 5[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]System changes -[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]tcp_fin_timeout = 30[/FONT]
[FONT=arial]tcp_tw_recycle = 0[/FONT]
[FONT=arial]tcp_tw_reuse = 0[/FONT]
[FONT=arial]net.netfilter.nf_conntrack_tcp_timeout_established = 432000[/FONT]
[FONT=arial]net.netfilter.nf_conntrack_max = 65536[/FONT]
[FONT=arial]/sys/module/nf_conntrack/parameters/hashsize = 16384[/FONT]
[FONT=arial]ulimit -n = 63674[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]---- New -------------------[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Nginx - [/FONT]
[FONT=arial]timeout = 0[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]System changes -[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]tcp_fin_timeout = 15[/FONT]
[FONT=arial]tcp_tw_recycle = 1[/FONT]
[FONT=arial]tcp_tw_reuse = 1[/FONT]
[FONT=arial]net.netfilter.nf_conntrack_tcp_timeout_established = 300[/FONT]
[FONT=arial]net.netfilter.nf_conntrack_max = 6553600[/FONT]
[FONT=arial]/sys/module/nf_conntrack/parameters/hashsize = 524288
unlimit- -n = ulimited



Any help/tips appreciated. Please let me know if anyone needs any more information.

Thanks[/FONT]

---

### Post by jas5 on 2015-05-05
Just noticed I posted in the wrong forum, sorry. Moving thread

---

### Post by jas5 on 2015-05-05
[COLOR=#000000]Hello community,[/COLOR]

[COLOR=#000000]First time poster here, go easy on me [/COLOR]:razz:[COLOR=#000000] Been working with Ubuntu for the last year or so and in quite the pickle right now with my web stack.[/COLOR]

[COLOR=#000000]Breakdown:[/COLOR]

[COLOR=#000000]We upgraded our ubuntu 10.04 servers to 12.04 hosted in the cloud and now have roughly 100ms increase in response time. I'm at wits end as all our code is the same, packages the same etc.[/COLOR]

[COLOR=#000000]Running Nginx frontend with apache in the back. package details:[/COLOR]

[COLOR=#000000]Nginx------[/COLOR]
[COLOR=#000000]nginx 1.6.3-1~precise[/COLOR]

[COLOR=#000000]Apache------[/COLOR]
[COLOR=#000000]apache2 2.2.22-1ubuntu1.8[/COLOR]
[COLOR=#000000]apache2-mpm-prefork 2.2.22-1ubuntu1.8[/COLOR]
[COLOR=#000000]apache2-utils 2.2.22-1ubuntu1.8[/COLOR]
[COLOR=#000000]apache2.2-bin 2.2.22-1ubuntu1.8[/COLOR]
[COLOR=#000000]apache2.2-common 2.2.22-1ubuntu1.8[/COLOR]

[COLOR=#000000]PHP------[/COLOR]
[COLOR=#000000]libapache2-mod-php5 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]newrelic-php5 4.20.2.95[/COLOR]
[COLOR=#000000]newrelic-php5-common 4.20.2.95[/COLOR]
[COLOR=#000000]php5 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-cli 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-common 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-curl 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-dev 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-gd 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-mcrypt 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-memcache 3.0.8-1~precise+1[/COLOR]
[COLOR=#000000]php5-memcached 2.1.0-3~precise+1[/COLOR]
[COLOR=#000000]php5-mysql 5.4.39-1+deb.sury.org~precise+2[/COLOR]
[COLOR=#000000]php5-readline 5.4.39-1+deb.sury.org~precise+2[/COLOR]

[COLOR=#000000]What I have thus far identified/tried[/COLOR]

[COLOR=#000000]We have a serious amount of TCP connections in TIME_WAIT roughly 30k-40k in peak times.[/COLOR]

[COLOR=#000000]I have modified some these settings being able to bring down the TIME_WAIT connections to about 10k[/COLOR]

[COLOR=#000000][FONT=arial]---- Old ---------------[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Nginx -[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]timeout = 5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]System changes -[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_fin_timeout = 30[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_tw_recycle = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_tw_reuse = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]net.netfilter.nf_conntrack_tcp_timeout_established = 432000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]net.netfilter.nf_conntrack_max = 65536[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]/sys/module/nf_conntrack/parameters/hashsize = 16384[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]ulimit -n = 63674[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]---- New -------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Nginx - [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]timeout = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]System changes -[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_fin_timeout = 15[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_tw_recycle = 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tcp_tw_reuse = 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]net.netfilter.nf_conntrack_tcp_timeout_established = 300[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]net.netfilter.nf_conntrack_max = 6553600[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]/sys/module/nf_conntrack/parameters/hashsize = 524288
unlimit- -n = ulimited



Any help/tips appreciated. Please let me know if anyone needs any more information.

Thanks[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-05-05
Did you perform an in-place upgrade or was this a clean install of 12.04?  Also, consider upgrading to 14.04 as there have been significant performance improvements between 12.04 and 14.04.

---

### Post by cariboo on 2015-05-06
Merged threads, please don't create multiple threads on the same subject. If you think you have created a thread in the wrong sub-forum, please click the Report Post button, and ask the moderation staff to move the thread to the correct sub-forum.

---

### Post by jas5 on 2015-05-19
Hey tgalati4,

This was a clean install of 12.04, I am beginning to work on moving to 14. I do have a server with better specs and putting it on 12.04 works perfectly. Makes me think its something with the hardware and 12.04

---

