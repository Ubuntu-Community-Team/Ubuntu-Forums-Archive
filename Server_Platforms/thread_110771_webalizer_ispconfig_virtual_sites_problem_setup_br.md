---
title: "webalizer ispconfig virtual sites problem setup breezy badger 5.10"
date: 2005-12-31
forum: Server Platforms
---

### Post by yellowjelly on 2005-12-31
Hi,

I'm faily new to Linux.  I searched for a webalizer solution to my problem but couldn't find it.  I'm posting this as a last resort.

I used the perfect setup instructions for ISP-Server Setup - Ubuntu 5.10 "Breezy Badger". and it works for the most part, except for webalizer.

I have a static IP with my ISP, and hosting about 5 virtual personal sites on my new server.

Webalizer is not working however, in ISPConfig the stats for each site remain 0's.  

After the installation I waited approx. 30+ hours to see it it would produce stats for any of the sites.  

At [http://www.zzxx.com/stats/](http://www.zzxx.com/stats/)  I just get a the error page 404 error - file not found.

I searched and made some changes as described in [http://j4cques.blogspot.com/](http://j4cques.blogspot.com/)

Enable the apache2 hostname resolution: went into /etc/apache2/apache2.conf: and changed HostnameLookups Off to HostnameLookups On

Edited /etc/webalizer.conf: and changed 
LogFile /var/log/apache2/access.log.1 to  /var/log/apache2/access.log

Edited the root cronjobs: sudo crontab -e and added the line to read: 0 1 * * * webalizer 

There was already a line for webalizer above I left it alone 0 4 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/webalizer.php &> /dev/null

When I run webalizer it returns

Webalizer V2.01-10 (Linux 2.6.12-9-k7) locale: en_US.UTF-8
Using logfile /var/log/apache2/access.log (clf)
Creating output in /var/www/webalizer
Hostname for reports is 'server1.zzxx.com'
Reading history file... webalizer.hist
Reading previous run data... webalizer.current
1 records ( 1 ignored) in 0.00 seconds

Below is what is contained in /var/www/webalizer/

ctry_usalge_200511.png
daily_usage_200511.png
hourly_usage_200511.png
usage.png
index.html
usage_200511.html
webalizer.current
webalizer.hist


So no stats for any of the sites.  Either in [www.xxzz.com/stats/](www.xxzz.com/stats/) or within ISPConfig

If anyone can please give any help, it would greatly be appreciated.

Thanks  ](*,)

---

### Post by yellowjelly on 2006-01-03
Well, the server has been running for several days now and it is working now.  There was another 

One other edit I did was edit the /etc/apache2/apache2.conf file.  I change the HostnameLookups from off to on.

TC :mrgreen: :mrgreen:

---

