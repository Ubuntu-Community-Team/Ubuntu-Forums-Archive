---
title: "Ubuntu Server 20.04 LTS - Apache / Port 80 Issue [Solved]"
date: 2020-07-07
forum: Server Platforms
---

### Post by xtcaox on 2020-07-07
Stressed Ubuntu newbie here, I got brave and decided to try some PHP updates and got this error after. Some searching and I found a temp fix, but I'm looking for a solution. Any help would be greatly appreciated.

Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-40-generic x86_64)
Last login: Tue Jul  7 00:18:39 2020


@sb-mainserver:~$ sudo /opt/bitnami/ctlscript.sh start
/opt/bitnami/mysql/scripts/ctl.sh : mysql  started at port 3306
Syntax OK
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:8                                    0
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.                                    0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
/opt/bitnami/apache2/scripts/ctl.sh : httpd could not be started
@sb-mainserver:~$ sudo netstat -lnp | grep 80
tcp6       0      0 :::80                   :::*                    LISTEN      878/apache2
udp6       0      0 fe80::3ed9:2bff:fe0:546 :::*                                762/systemd-network
@sb-mainserver:~$ sudo kill 878
@sb-mainserver:~$ sudo /opt/bitnami/ctlscript.sh start
/opt/bitnami/mysql/scripts/ctl.sh : mysql  (pid 1444) already running
Syntax OK
/opt/bitnami/apache2/scripts/ctl.sh : httpd started at port 80
@sb-mainserver:~$ sudo netstat -lnp | grep 80
tcp6       0      0 :::80                   :::*                    LISTEN      1615/httpd.bin
udp6       0      0 fe80::3ed9:2bff:fe0:546 :::*                                762/systemd-network
@sb-mainserver:~$

---

### Post by LHammonds on 2020-07-07
You say PHP updates, but for Ubuntu, those come in the form of:
```
sudo apt upgrade
```

Is that what you did and you are describing what happened after regarding a bitnami stack of some kind?

You mention Ubuntu Server 20.04 so I assume you have the default Apache version 2.4.41 and PHP 7.4.3

If you upgraded Apache, did you tell the upgrade to overwrite default settings?  Are your website config files stuck inside the config files provided by a default instance or did you put them in your own configuration file (which is recommended)?

The "could not bind to address" message sounds like you have configuration issues.

Maybe you deleted the default "/etc/apache2/sites-available/000-default.conf" configuration file when you setup the server but an upgrade put it back.  No idea really since there are 1,000 commands you could have issued to setup your server and speculation on my part gets us nowhere fast.

Look at the sites-enabled folder to see what active configuration files (which are linked to config files in the sites-available folder).

Use the a2dissite to disable any config files you do not want active (which deletes the link in the sites-enabled folder).

LHammonds

---

### Post by xtcaox on 2020-07-07
This command seemed to fix it..


sudo systemctl disable --now apache2

---

### Post by dyoms on 2020-07-10
why not try nginx instead of apache?

---

### Post by LHammonds on 2020-07-11
> **dyoms said:**
> why not try nginx instead of apache?The OP is using bitnami and I assume it is a packaged deal.  Apache probably came bundled with whatever bitnami package was installed which conflicted with the base Apache that can be installed with Ubuntu...thus disabling Apache that came with ubuntu fixing the conflicting port usage.

---

