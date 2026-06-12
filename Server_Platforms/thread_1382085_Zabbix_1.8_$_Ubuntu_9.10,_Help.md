---
title: "Zabbix 1.8 $ Ubuntu 9.10, Help?"
date: 2010-01-15
forum: Server Platforms
---

### Post by quietas on 2010-01-15
Has anyone managed to get Zabbix 1.8 working with Ubuntu Server 9.10 and how? THe .debs in the repo are out of date, 1.64 rather than 1.8, and a manual build has had issues so far.

I finally worked out the dependency issues while using the install instructions from the Zabbix documentation. After running ./configure .... and then make install it seems to have worked.

Where to I access it from? They seem to have failed to mention that. It's not anywhere that I can find easily.

---

### Post by ICEB3AR on 2010-01-15
There is a Webinterface for administrative actions:
[http://www.debianhelp.co.uk/zabbix.htm]("http://www.debianhelp.co.uk/zabbix.htm")

The URL Of the webinterface should be [http://yourserver/zabbix/](http://yourserver/zabbix/)

---

### Post by quietas on 2010-01-15
That page on debianhelp refers to the .deb installation and using a repo site which does not exist. As I mentioned in the previous post, the current repo is still behind with 1.6.4 rather than the newest 1.8.

Thanks for trying though.

---

### Post by ICEB3AR on 2010-01-15
In the source-package of Zabbix 1.8 there is a folder 'frontends'. I would try to copy the folder to the apache home and enter the address in your Webbrowser where you copied it to e.g.: http://<IP>/frontends/php
In that folder is also the file queue.php Which you can see on the first pic of the install documentation. [http://www.zabbix.com/documentation/1.8/manual/installation/installation_from_source#zabbix_web_interface]("http://www.zabbix.com/documentation/1.8/manual/installation/installation_from_source#zabbix_web_interface")

Hope that helps :)

Best Regards
ICEB3AR

---

### Post by HighCommander540 on 2010-01-15
That's not the point dude. All versions of Zabbix will use that web interface. At the same URL. Just try it.

---

### Post by quietas on 2010-01-15
> **HighCommander540 said:**
> That's not the point dude. All versions of Zabbix will use that web interface. At the same URL. Just try it.

The problem like I stated before is that Zabbix does not have complete instructions. I dug into zabbix-1.8/frontends/php and copied all that to /var/www/zabbix/, did the appropriate chmod/chown, and opened the index.php in Firfox. Some PHP.INI settings needed to be adjusted, did so, and the front end worked.

Again, Zabbix has incomplete and incorrect instructions. The /etc/init.d/zabbix-agent and zabbix-server files were never created. Those are buried in the zabbix-1.8/misc/init.d folder. I copied them and set permissions.

Still no luck.

---

### Post by quietas on 2010-01-15
Location of the bin files:
```
quietas@helpdesk:~$ sudo find / -name zabbix_agent
/home/quietas/zabbix-1.8/src/zabbix_agent
/home/quietas/zabbix-1.8/src/zabbix_agent/zabbix_agent
/home/quietas/zabbix-1.8/sbin/zabbix_agent
/usr/local/sbin/zabbix_agent
```

Paths /etc/init.d/zabbix-agent looks into:
```
NAME=zabbix_server
PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/zabbix/bin
DAEMON=/home/zabbix/bin/${NAME}
DESC="Zabbix server daemon"
PID=/var/tmp/$NAME.pid

```

That seems to be half the problem. Editing that now.

---

### Post by quietas on 2010-01-15
```
quietas@helpdesk:~$ sudo /etc/init.d/zabbix-server start
Starting Zabbix server daemon: zabbix_server
/usr/local/sbin/zabbix_server [11500]: Cannot open config file [/etc/zabbix/zabbix_server.conf] [No such file or directory].

```

More files which were not copied with the "make install" command. These are located in zabbix-1.8/misc/conf

I made a /etc/zabbix folder, then copied the files.
```
quietas@helpdesk:~/zabbix-1.8/misc/conf$ sudo /etc/init.d/zabbix-server start
Starting Zabbix server daemon: zabbix_server
```

I did the same for agent as well.
```
culleym@helpdesk:~/zabbix-1.8/misc/conf$ sudo /etc/init.d/zabbix-agent start
Starting Zabbix agent daemon: zabbix_agentd
```

---

### Post by quietas on 2010-01-15
Bah. Agent is working, but not the server.

```
quietas@helpdesk:~/zabbix-1.8/misc/conf$ ps aux |grep zabbix
zabbix   11562  0.0  0.0   3224   548 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
zabbix   11563  0.2  0.0   3224   788 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
zabbix   11564  0.0  0.0   3224   420 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
zabbix   11565  0.0  0.0   3224   420 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
zabbix   11566  0.0  0.0   3224   420 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
zabbix   11567  0.0  0.0   3224   584 ?        SN   15:24   0:00 /usr/local/sbin/zabbix_agentd
quietas  11580  0.0  0.0   3040   796 pts/0    R+   15:25   0:00 grep --color=auto zabbix

```

---

### Post by quietas on 2010-01-15
Working. I had to edit a couple lines.

/etc/zabbix/zabbix_agentd.conf
```
Server=127.0.0.1 change to xxx.xxx.xxx.xxx
ListenIP=xxx.xxx.xxx.xxx
```

/etc/zabbix/zabbix_server.conf
```
DBUser=zabbix
DBPassword=password123
ListenIP=xxx.xxx.xxx.xxx
```

I set xxx.xxx.xxx.xxx to 127.0.0.1 since both server and agent are on the same system in this case.

quietas@helpdesk:~$ ps aux
```
....
zabbix   12113  0.3  0.0  47832  1872 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12114  0.0  0.0  47832  1300 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12115  2.6  0.0  48604  2468 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12116  3.0  0.0  48604  2468 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12117  2.6  0.0  48604  2468 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12118  2.6  0.0  48604  2468 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12119  2.6  0.0  48604  2468 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12120  0.0  0.0  47832  1232 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12121  0.0  0.0  47832  1232 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12122  0.0  0.0  47832  1232 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12123  0.0  0.0  47832  1232 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12124  0.0  0.0  47832  1232 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12125  0.0  0.0  48384  1264 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12126  0.0  0.0  47832  1252 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12127 20.3  0.0  48104  1560 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12128  0.0  0.0  47832  1264 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12129  3.0  0.0  48604  2472 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12136  0.0  0.0  47832  1240 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12138  0.0  0.0  47832  1260 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12139  2.6  0.0  48368  2472 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12140  0.0  0.0  47832  1240 ?        SN   15:41   0:00 /bin/zabbix_server
zabbix   12141  0.0  0.0  47832  1256 ?        SN   15:41   0:00 /bin/zabbix_server
quietas  12148  0.0  0.0   2644  1012 pts/0    R+   15:41   0:00 ps aux
```

An the web GUI shows it working now.

---

### Post by quietas on 2010-01-15
Damnit, now that I got it working I found a better walkthrough which seems to detail the post make config better.

[http://www.ubuntugeek.com/how-to-setup-zabbix-monitoring-application-in-ubuntu-9-04-jaunty-server.html](http://www.ubuntugeek.com/how-to-setup-zabbix-monitoring-application-in-ubuntu-9-04-jaunty-server.html)

---

