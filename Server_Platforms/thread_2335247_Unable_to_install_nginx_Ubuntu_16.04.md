---
title: "Unable to install nginx Ubuntu 16.04"
date: 2016-08-26
forum: Server Platforms
---

### Post by deepakdeshp on 2016-08-26
Hello, I tried to install nginx on Ubuntu 16.04 server 32 bit but failed . Please advise.

```
apt list --installed |grep nginx

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


nginx-common/xenial-updates,xenial-security,now 1.10.0-0ubuntu0.16.04.2 all [installed,auto-removable]
uma@ubuntu-i386:~$ **sudo apt-get purge nginx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nginx' is not installed, so not removed
The following package was automatically installed and is no longer required:
  nginx-common
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
uma@ubuntu-i386:~$ **sudo apt autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nginx-common
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 167 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 141539 files and directories currently installed.)
Removing nginx-common (1.10.0-0ubuntu0.16.04.2) ...
uma@ubuntu-i386:~$ **apt list --installed |grep nginx**


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


(reverse-i-search)`': apt list --installed |grep nginx^C
uma@ubuntu-i386:~$ **sudo apt-get update**
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease                  
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                 
Fetched 94.5 kB in 1s (55.4 kB/s)                              
Reading package lists... Done
(failed reverse-i-search)`grAD': apt list --installed |^Cep nginx
(failed reverse-i-search)`GRADE': Partition: ID-1: / size: 87G used: 56^C(68%) fs: ext4 dev: /dev/sda12
uma@ubuntu-i386:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic ubuntu-core-launcher
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
uma@ubuntu-i386:~$ **sudo apt-get update**
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease                  
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                 
Fetched 94.5 kB in 1s (65.8 kB/s)                  
Reading package lists... Done
uma@ubuntu-i386:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic ubuntu-core-launcher
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
uma@ubuntu-i386:~$ **sudo apt-get -f**
E: Command line option 'f' [from -f] is not understood in combination with the other options.
uma@ubuntu-i386:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
uma@ubuntu-i386:~$ **apt list --installed |grep nginx**


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


uma@ubuntu-i386:~$** sudo apt-get purge nginx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nginx' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
uma@ubuntu-i386:~$ **sudo apt-get install nginx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  nginx-common nginx-core
Suggested packages:
  fcgiwrap nginx-doc
The following NEW packages will be installed:
  nginx nginx-common nginx-core
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/499 kB of archives.
After this operation, 1,512 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package nginx-common.
(Reading database ... 141521 files and directories currently installed.)
Preparing to unpack .../nginx-common_1.10.0-0ubuntu0.16.04.2_all.deb ...
Unpacking nginx-common (1.10.0-0ubuntu0.16.04.2) ...
Selecting previously unselected package nginx-core.
Preparing to unpack .../nginx-core_1.10.0-0ubuntu0.16.04.2_i386.deb ...
Unpacking nginx-core (1.10.0-0ubuntu0.16.04.2) ...
Selecting previously unselected package nginx.
Preparing to unpack .../nginx_1.10.0-0ubuntu0.16.04.2_all.deb ...
Unpacking nginx (1.10.0-0ubuntu0.16.04.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Processing triggers for systemd (229-4ubuntu7) ...
Setting up nginx-common (1.10.0-0ubuntu0.16.04.2) ...
insserv: warning: script 'K01noip2' missing LSB tags and overrides
insserv: warning: script 'noip2' missing LSB tags and overrides
Setting up nginx-core (1.10.0-0ubuntu0.16.04.2) ...
Job for nginx.service failed because the control process exited with error code. See "systemctl status nginx.service" and "journalctl -xe" for details.
invoke-rc.d: initscript nginx, action "start" failed.
dpkg: error processing package nginx-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on nginx-core (>= 1.10.0-0ubuntu0.16.04.2) | nginx-full (>= 1.10.0-0ubuntu0.16.04.2) | nginx-light (>= 1.10.0-0ubuntu0.16.04.2) | nginx-extras (>= 1.10.0-0ubuntu0.16.04.2); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.
 nginx depends on nginx-core (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-full (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-light (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-extras (<< 1.10.0-0ubuntu0.16.04.2.1~); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.


dpkg: error processing package nginx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nginx-core
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)
uma@ubuntu-i386:~$ 



```

---

### Post by cariboo on 2016-08-26
The error message tells you what the problem is:

```
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on nginx-core (>= 1.10.0-0ubuntu0.16.04.2) | nginx-full (>= 1.10.0-0ubuntu0.16.04.2) | nginx-light (>= 1.10.0-0ubuntu0.16.04.2) | nginx-extras (>= 1.10.0-0ubuntu0.16.04.2); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.
 nginx depends on nginx-core (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-full (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-light (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-extras (<< 1.10.0-0ubuntu0.16.04.2.1~); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.
```

you need to also install the following packages:

[LIST]
[*]nginx-full
[*]nginx-light
[*]nginx-extras
[/LIST]

---

### Post by deepakdeshp on 2016-08-26
Thank you .I had tried installing the packages listed by you but it gave error. Even purging the packages also gave error. I used ```
sudo apt-get install package name

sudo apt-get purge package name
and also apt-get install -f
 

```
The packages on which I ran the install and purge commands are

[LIST]
[*]nginx-full
[*]nginx-light
[*]nginx-extras
[*]nginx
[/LIST]

---

### Post by cariboo on 2016-08-26
I'd suggest using:

```
locate nginx
```

to see if there are any left over files after running:

```
sudo apt purge <package name>
```

**Note:** you no longer need to use apt-get in version 16.04+, a simple apt works the same way, even giving you a progress bar at the bottom of the screen.

---

### Post by deepakdeshp on 2016-08-27
THank you nginx is successfully installed. Even after installation I cannnot locate nginx. That is ok

```
ps -e |grep ngi 8387 ?        00:00:00 nginx
 8388 ?        00:00:00 nginx
root@ubuntu-i386:/home/uma# locate nginx
root@ubuntu-i386:/home/uma# 



```

I am migrating from Apache to nginx hence was following this tutorial [https://www.digitalocean.com/community/tutorials/how-to-migrate-from-an-apache-web-server-to-nginx-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-migrate-from-an-apache-web-server-to-nginx-on-an-ubuntu-vps)


 I wasnt able to find any specific tutorial for Ubuntu 16 too migrate from apache to nginx.

---

### Post by deepakdeshp on 2016-08-27
I went back to earlier snapshot of the VM on which ubuntu server is running which didnt have nginx. I tried all the commands byt ran into the same error.

```
apt purge nginx*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nginx-full-dbg' for glob 'nginx*'
Note, selecting 'nginx-core' for glob 'nginx*'
Note, selecting 'nginx-core-dbg' for glob 'nginx*'
Note, selecting 'nginx-common' for glob 'nginx*'
Note, selecting 'nginx-doc' for glob 'nginx*'
Note, selecting 'nginx-full' for glob 'nginx*'
Note, selecting 'nginx-extras' for glob 'nginx*'
Note, selecting 'nginx-light-dbg' for glob 'nginx*'
Note, selecting 'nginx-extras-dbg' for glob 'nginx*'
Note, selecting 'nginx-light' for glob 'nginx*'
Note, selecting 'nginx' for glob 'nginx*'
Package 'nginx' is not installed, so not removed
Package 'nginx-common' is not installed, so not removed
Package 'nginx-core' is not installed, so not removed
Package 'nginx-core-dbg' is not installed, so not removed
Package 'nginx-doc' is not installed, so not removed
Package 'nginx-extras' is not installed, so not removed
Package 'nginx-extras-dbg' is not installed, so not removed
Package 'nginx-full' is not installed, so not removed
Package 'nginx-full-dbg' is not installed, so not removed
Package 'nginx-light' is not installed, so not removed
Package 'nginx-light-dbg' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apt-xapian-index aptitude-common g++-4.8 libboost-iostreams1.54.0 libclamav6 libclass-accessor-perl libcolord1 libcolorhug1 libcwidget3 libept1.4.12 libgcrypt11-dev
  libgnutlsxx27 libgphoto2-port10 libgtop2-7 libilmbase6 libio-string-perl libisl10 libjasper1 libjs-codemirror libjs-jquery-cookie libjs-jquery-event-drag
  libjs-jquery-metadata libjs-jquery-mousewheel libjs-jquery-tablesorter libjs-jquery-ui libmagickcore5 libmagickcore5-extra libmagickwand5 libmemcached10 libopenexr6
  libparse-debianchangelog-perl libsigc++-2.0-0c2a libstdc++-4.8-dev libsub-name-perl libv4l-0 libv4lconvert0 libvpx1 libxcb-util0 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic php5-mcrypt python-xapian rlwrap ruby-hike ruby-journey ruby-mail
  ruby-mime-types ruby-polyglot ruby-rack-cache ruby-rack-ssl ruby-rack-test ruby-rack1.4 ruby-sprockets ruby-tilt ruby-treetop ruby-yajl
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


```


```
root@ubuntu-i386:/home/uma# apt install nginxReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-xapian-index aptitude-common g++-4.8 libboost-iostreams1.54.0 libclamav6 libclass-accessor-perl libcolord1 libcolorhug1 libcwidget3 libept1.4.12 libgcrypt11-dev
  libgnutlsxx27 libgphoto2-port10 libgtop2-7 libilmbase6 libio-string-perl libisl10 libjasper1 libjs-codemirror libjs-jquery-cookie libjs-jquery-event-drag
  libjs-jquery-metadata libjs-jquery-mousewheel libjs-jquery-tablesorter libjs-jquery-ui libmagickcore5 libmagickcore5-extra libmagickwand5 libmemcached10 libopenexr6
  libparse-debianchangelog-perl libsigc++-2.0-0c2a libstdc++-4.8-dev libsub-name-perl libv4l-0 libv4lconvert0 libvpx1 libxcb-util0 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic php5-mcrypt python-xapian rlwrap ruby-hike ruby-journey ruby-mail
  ruby-mime-types ruby-polyglot ruby-rack-cache ruby-rack-ssl ruby-rack-test ruby-rack1.4 ruby-sprockets ruby-tilt ruby-treetop ruby-yajl
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  nginx-common nginx-core
Suggested packages:
  fcgiwrap nginx-doc
The following NEW packages will be installed:
  nginx nginx-common nginx-core
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/499 kB of archives.
After this operation, 1,512 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package nginx-common.
(Reading database ... 176729 files and directories currently installed.)
Preparing to unpack .../nginx-common_1.10.0-0ubuntu0.16.04.2_all.deb ...
Unpacking nginx-common (1.10.0-0ubuntu0.16.04.2) ...
Selecting previously unselected package nginx-core.
Preparing to unpack .../nginx-core_1.10.0-0ubuntu0.16.04.2_i386.deb ...
Unpacking nginx-core (1.10.0-0ubuntu0.16.04.2) ...
Selecting previously unselected package nginx.
Preparing to unpack .../nginx_1.10.0-0ubuntu0.16.04.2_all.deb ...
Unpacking nginx (1.10.0-0ubuntu0.16.04.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Processing triggers for systemd (229-4ubuntu7) ...
Setting up nginx-common (1.10.0-0ubuntu0.16.04.2) ...
insserv: warning: script 'K01noip2' missing LSB tags and overrides
insserv: warning: script 'noip2' missing LSB tags and overrides
Setting up nginx-core (1.10.0-0ubuntu0.16.04.2) ...
Job for nginx.service failed because the control process exited with error code. See "systemctl status nginx.service" and "journalctl -xe" for details.
invoke-rc.d: initscript nginx, action "start" failed.
dpkg: error processing package nginx-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on nginx-core (>= 1.10.0-0ubuntu0.16.04.2) | nginx-full (>= 1.10.0-0ubuntu0.16.04.2) | nginx-light (>= 1.10.0-0ubuntu0.16.04.2) | nginx-extras (>= 1.10.0-0ubuntu0.16.04.2); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.
 nginx depends on nginx-core (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-full (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-light (<< 1.10.0-0ubuntu0.16.04.2.1~) | nginx-extras (<< 1.10.0-0ubuntu0.16.04.2.1~); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.


dpkg: error processing packagNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                       e nginx (--configure):
 dependency problems - leaving unconfigured
Processing triggers for systemd (229-4ubuntu7) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Errors were encountered while processing:
 nginx-core
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu-i386:/home/uma
```

---

### Post by cariboo on 2016-08-28
I tried installing nginx on a server with the lamp stack already installed, and ran into the same problem as you.

I created a new server install in a vm, without installing anything extra, I installed nginx, with zero problems and it works as it should

---

### Post by deepakdeshp on 2016-08-28
Thank you for your reply. There must be a way to install nginx along with Apache. I have seen articles using apache and nginx together. I wanted to try this too.

[https://www.howtoforge.com/tutorial/how-to-install-nginx-as-reverse-proxy-for-apache-on-ubuntu-16-04/](https://www.howtoforge.com/tutorial/how-to-install-nginx-as-reverse-proxy-for-apache-on-ubuntu-16-04/)

---

### Post by cariboo on 2016-08-28
> **deepakdeshp said:**
> Thank you for your reply. There must be a way to install nginx along with Apache. I have seen articles using apache and nginx together. I wanted to try this too.

[https://www.howtoforge.com/tutorial/how-to-install-nginx-as-reverse-proxy-for-apache-on-ubuntu-16-04/](https://www.howtoforge.com/tutorial/how-to-install-nginx-as-reverse-proxy-for-apache-on-ubuntu-16-04/)

To install nginx make sure apache2 isn't running, but it won't do a lot of good as they won't run at the same time if they are listening on the same port. If you plan on trying the tutorial you linked to, follow it from the start, and don't skip any steps. I followed it on a vm, and after a bit of troubleshooting I got it to work. The big problem was extra directives in /etc/nginx/sites-available/default, this is a corrected version:

```

##
# You should look at the following URL's in order to grasp a solid understanding
# of Nginx configuration files in order to fully unleash the power of Nginx.
# http://wiki.nginx.org/Pitfalls
# http://wiki.nginx.org/QuickStart
# http://wiki.nginx.org/Configuration
#
# Generally, you will want to move this file somewhere, and start with a clean
# file but keep this around for reference. Or just disable in sites-enabled.
#
# Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
##

# Default server configuration
#
server {
	listen 80 default_server;
	listen [::]:80 default_server;

	root /var/www/html;

	#add index.php to the list if you are using php
	index indes.html indes.htm index.nginx-debian.html index.php;


	location / {
		proxy_pass http://localhost:8000;
		include /etc/nginx/proxy_params;
	}
}

	# SSL configuration
	#
	# listen 443 ssl default_server;
	# listen [::]:443 ssl default_server;
	#
	# Note: You should disable gzip for SSL traffic.
	# See: https://bugs.debian.org/773332
	#
	# Read up on ssl_ciphers to ensure a secure configuration.
	# See: https://bugs.debian.org/765782
	#
	# Self signed certs generated by the ssl-cert package
	# Don't use them in a production server!
	#
	# include snippets/snakeoil.conf;

	#server_name _;

	#location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		#try_files $uri $uri/ =404;
	#}

	# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
	#
	#location ~ \.php$ {
	#	include snippets/fastcgi-php.conf;
	#
	#	# With php7.0-cgi alone:
	#	fastcgi_pass 127.0.0.1:9000;
	#	# With php7.0-fpm:
	#	fastcgi_pass unix:/run/php/php7.0-fpm.sock;
	#}

	# deny access to .htaccess files, if Apache's document root
	# concurs with nginx's one
	#
	#location ~ /\.ht {
	#	deny all;
	#}
#}


# Virtual Host configuration for example.com
#
# You can move that to a different file under sites-available/ and symlink that
# to sites-enabled/ to enable it.
#
#server {
#	listen 80;
#	listen [::]:80;
#
#	server_name example.com;
#
#	root /var/www/example.com;
#	index index.html;
#
#	location / {
#		try_files $uri $uri/ =404;
#	}
#}
```

---

