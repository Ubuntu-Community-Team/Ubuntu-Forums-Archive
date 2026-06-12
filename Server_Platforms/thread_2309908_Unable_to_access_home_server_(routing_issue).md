---
title: "Unable to access home server (routing issue)"
date: 2016-01-14
forum: Server Platforms
---

### Post by mbnoimi on 2016-01-14
Hi,

I'm unable to access my home server remotely although it works fine in LAN. When I try to access it remotely using [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) I get router control panel page and when I browse [http://xxx.xxx.xxx.xxx:8081/](http://xxx.xxx.xxx.xxx:8081/) the browser gives timeout error (I'm unable to access MySQL DB too)

May you please help me?

Installed LAMP configurations:

[list]
[*]Linux ubuntu 14.04 x64
[*]nmap output (I already get static IP from my ISP):
```
nmap -sS -O -PI -PT xxx.xxx.xxx.xxx

Starting Nmap 6.40 ( http://nmap.org ) at 2016-01-14 16:00 EET
Nmap scan report for xxx.xxx.xxx.xxx
Host is up (0.0024s latency).
Not shown: 993 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
631/tcp  open  ipp
3306/tcp open  mysql
8081/tcp open  blackice-icecap
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.19, Linux 2.6.9 - 2.6.30

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.58 seconds

```
[*]Apache 2.4.7
[*]/etc/apache2/apache2.conf
```
Mutex file:${APACHE_LOCK_DIR} default
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 5
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
HostnameLookups Off
ErrorLog ${APACHE_LOG_DIR}/error.log
LogLevel warn
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf
Include ports.conf
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>

<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>

<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

AccessFileName .htaccess

<FilesMatch "^\.ht">
	Require all denied
</FilesMatch>

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

IncludeOptional conf-enabled/*.conf

IncludeOptional sites-enabled/*.conf
```
[*]/etc/apache2/ports.conf
```
Listen 8010

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>

```
[*]/etc/apache2/sites-enabled/000-default.conf
```
<VirtualHost *:8010>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
[*]MySQL 5.5.46
[*]/etc/mysql/my.cnf
```
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
lc-messages-dir	= /usr/share/mysql
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
query_cache_limit	= 1M
query_cache_size        = 16M
log_error = /var/log/mysql/error.log
expire_logs_days	= 10
max_binlog_size         = 100M

[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]

[isamchk]
key_buffer		= 16M

!includedir /etc/mysql/conf.d/
```
[*]Home server
```
IP Address: 192.168.1.2
Broadcast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.1
Primary DNS: 192.168.1.1
```
[*]Router control panel IP: 192.168.1.1
[*]Port Forwarding configurations (see the attachment plz)
[ATTACH=CONFIG]266749[/ATTACH]
[*]netstat output
```
mbnoimi-home mbnoimi-home # sudo netstat -napW | grep apache
tcp6       0      0 :::8010                 :::*                    LISTEN      21958/apache2
mbnoimi-home mbnoimi-home # sudo netstat -napW | grep mysql
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      4746/mysqld     
unix  2      [ ACC ]     STREAM     LISTENING     1401737  4746/mysqld         /var/run/mysqld/mysqld.sock
mbnoimi-home mbnoimi-home #
```
[*]Firewall status (disables in both firewall and the server)
```
mbnoimi-home mbnoimi-home # ufw status
Status: inactive
mbnoimi-home mbnoimi-home # 

```
[/list]

---

### Post by Doug S on 2016-01-14
Your apache web server appears to only be listening for IPV6 traffic.

---

### Post by mbnoimi on 2016-01-14
I found out what's the problem.

As soon as I input DMZ to 192.168.1.2 the problem solved.

Thank you guys for help

---

### Post by nerdtron on 2016-01-14
DMZ to the local server means all outside requests/probes (any port) to the router will be forwarded to the internal server.
Be careful with that. Be sure to setup your firewall correctly. The public internet is a scary place.

---

