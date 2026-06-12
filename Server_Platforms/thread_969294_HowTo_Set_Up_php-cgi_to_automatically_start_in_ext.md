---
title: "HowTo Set Up php-cgi to automatically start in external FASTCGI Mode"
date: 2008-11-03
forum: Server Platforms
---

### Post by docplastic on 2008-11-03
How To enable Nginx or Lighttpd Web Servers to serve php code/scripts.

The procedure described here does not need any other resources besides the php-cgi (php5-cgi) package present in current Ubuntu repositories.
As process superviser spawner it uses Upstart, the Ubuntu's native event-based sysvinit daemon replacement.
 
The php5-cgi package in the Ubuntu repositories (until 5.2.4), does not include a script to automatically start it in external FASTCGI Mode (Daemon mode).

As there seems to be a great deal of confusion in the Internet on how to properly set up PHP script execution using php-cgi in external FASTCGI Mode,

Note:
# 20081106: To use Unix domain sockets substitute, in the exec line:
# from: exec /usr/bin/sudo -u www-data PHP_FCGI_CHILDREN=5 PHP_FCGI_MAX_REQUESTS=125 /usr/bin/php-cgi -q -b 127.0.0.1:9000
#     to: exec /usr/bin/sudo -u www-data PHP_FCGI_CHILDREN=5 PHP_FCGI_MAX_REQUESTS=125 /tmp/php-fastcgi.socket
# Take care to also change the relevant line(s) in nginx config file(s):
#  from: fastcgi_pass 127.0.0.1:9000;
#      to: fastcgi_pass unix:/tmp/php-fastcgi.socket;
# to learn why to use Unix domain sockets see: <http://lists.freebsd.org/pipermail/freebsd-performance/2005-February/001143.html>


I am attaching the procedure that we use to enable the Nginx Web Servers to reliably serve PHP code at our UBUNTU servers:

sudo tee /etc/event.d/php-fastcgi <<-\EOA
# /etc/event.d/php-fastcgi
# php-fastcgi - starts php-cgi as an external FASTCGI process
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
stop on runlevel 0
stop on runlevel 1
stop on runlevel 6
exec /usr/bin/sudo -u www-data PHP_FCGI_CHILDREN=5 PHP_FCGI_MAX_REQUESTS=125 /usr/bin/php-cgi -q -b 127.0.0.1:9000
respawn
EOA

sudo chmod u+x /etc/event.d/php-fastcgi
sudo initctl start php-fastcgi # start php-fastcgi
sudo /etc/init.d/nginx restart

# To test the setup
sudo initctl status php-fastcgi # check if upstart is supervising
ps aux | grep cgi # check the php-cgi running processes
echo -e '<?php\nphpinfo();\n?>' | sudo tee /var/www/nginx-default/phpinfo.php
# browse to: <http://localhost/phpinfo.php> to check if it works

# To stop php-fastcgi and all its childs.
sudo initctl stop php-fastcgi

---

### Post by rjha94 on 2011-12-25
I would like to know how upstart would honor "PHP_FCGI_MAX_REQUESTS" variable here? I thought that upstart will activate at boot time, check appropriate run level and spawn a php-cgi exe (via exec) 

Can some one please elaborate on how upstart will know that PHP_FCGI_MAX_REQUESTS limit has been reached and does it actually kill the old process and start a new one?

---

