---
title: "Apache2 Site Configuration"
date: 2015-04-14
forum: Server Platforms
---

### Post by FishCreekAndy on 2015-04-14
[COLOR=#000000][FONT=Arial]I'm attempting to configure a Nagios server on Ubuntu 14.04 Server.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Using apt-get I installed the packages nagios3 and phpmyadmin, however I do not see any content under /var/www and /etc/apache2/sites-available only contains 000-default.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I would like to manually install a few additional virtual hosts for NConf and a few other sites, and am unsure if I can simply create /var/www/nconf, provide a virtual host defitinition in sites-available and enable site using a2ensite.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I’m used to installing sites manually into /var/www and using a2ensite and the config files of /sites-available so by using apt-get to install nagios3 and phpmyadmin I’m unsure if my old method will work on this box that has had sites installed & configured using apt-get.[/FONT][/COLOR]

Thank you in advance.

---

### Post by dino99 on 2015-04-14
[https://www.digitalocean.com/community/tutorials/how-to-install-nagios-4-and-monitor-your-servers-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-nagios-4-and-monitor-your-servers-on-ubuntu-14-04)
[https://help.ubuntu.com/10.04/serverguide/httpd.html](https://help.ubuntu.com/10.04/serverguide/httpd.html)

---

### Post by Holger_Gehrke on 2015-04-14
I don't know about Nagios, but phpmyadmin puts a file into '/etc/apache2/conf.d/' that aliases '/usr/share/phpmyadmin' to '/phpmyadmin' in the webserver.

---

### Post by Habitual on 2015-04-14
[http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194#p281](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194#p281)

---

### Post by FishCreekAndy on 2015-04-14
I tried creating a symbolic link from /home/me/foo to /var/www and could not pull up anything pointed at [http://localhost/foo](http://localhost/foo). Am I missing anything?

---

### Post by FishCreekAndy on 2015-04-14
Thank you for the nagios4 tutorial link. Changed the Makefile before installing Nagios to point at apache2.conf instead of httpd.conf.

---

