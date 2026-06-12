---
title: "Munin Installation giving me -nan"
date: 2014-11-19
forum: Server Platforms
---

### Post by BeachSamurai on 2014-11-19
Hi 

I am new to ubuntu and linux in general and I followed the directions for installation of munin from this website: [http://munin.readthedocs.org/en/latest/installation/install.html](http://munin.readthedocs.org/en/latest/installation/install.html)

:
 [h=3]Debian/Ubuntu[/h] Munin is distributed with both Debian and Ubuntu.
 In order to get Munin up and running type
 sudo apt-get install munin-node

 
 on all nodes, and
 sudo apt-get install munin

 
 on the master.
 Please note that this might not be the latest version of Munin. On Debian you have the option of enabling “backports”, which may give access to later versions of Munin.
 "


But my graphs for /dev/sda give -nan. 

I was wondering if there was a problem with permissions so in apache I followed this users advice : 

[http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se](http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se)

vim /etc/munin/apache.conf
  change the the following lines:
  Order allow,deny
Allow from localhost 127.0.0.0/8 ::1
Options None
  like so:
  Order allow,deny
Allow from all
Options FollowSymLinks SymLinksIfOwnerMatch
  Like @hamish noted in Apache 2.4 it need to be
  Require all granted
Options FollowSymLinks SymLinksIfOwnerMatch


but still nothing. 

can someone help me? 

thanks

---

### Post by BeachSamurai on 2014-11-20
Bump

---

### Post by coldraven on 2014-11-21
I don't have a clue but maybe if you say what exactly you installed Munin on you may get an answer. I would be interested to know what constitutes "Node" and "Master".
Anyway have a free bump while you wait :)

---

### Post by Elfy on 2014-11-21
*Thread moved to **Server Platforms**.*

likely to be more who can help looking here

---

### Post by Jonathan L on 2014-11-21
Hi Beach Samurai

I'm afraid I have but scant experience with Munin, but I understand it caches the graphs, and if the data is unavailable when the graphs are made you can end up with '[Not A Number]("http://en.wikipedia.org/wiki/NaN")'.  At least some people find they can remove NaNs by restarting rrdcached, perhaps that approach will help.  

There are at least a couple bugs with similar symptoms: you might consider checking versions and see if later Munin helps.  ([http://munin-monitoring.org/ticket/1467](http://munin-monitoring.org/ticket/1467)
[http://munin-monitoring.org/ticket/1459](http://munin-monitoring.org/ticket/1459) )

Hope that's of some use.  Let us know how you get on.

Kind regards,
Jonathan

---

### Post by Jonathan L on 2014-11-21
... some further reading made me think:

* Telnet debugging is the best place to start, as described [http://munin-monitoring.org/wiki/MuninTroubleshooting](http://munin-monitoring.org/wiki/MuninTroubleshooting)
* If it's a caching problem, you might consider just-in-time output: [http://munin-monitoring.org/wiki/MuninConfigurationMasterCGI](http://munin-monitoring.org/wiki/MuninConfigurationMasterCGI)

Kind regards
Jonathan

---

### Post by BeachSamurai on 2014-11-24
ok thank you for the answers guys, 

@coldraven I installed it on my computer. Using Ubuntu Gnome.

---

