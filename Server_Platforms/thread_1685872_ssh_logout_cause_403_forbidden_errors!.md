---
title: "ssh logout cause 403 forbidden errors!"
date: 2011-02-11
forum: Server Platforms
---

### Post by intomb on 2011-02-11
i have strange problem on my wordpress-powered blog.
while i'm connecting to server by ssh or physical console, everything works fine.
 
however, when i tries to logout almost immediately 403 forbidden error pops up on every pages of my website.
if there are two or more connections (like physical console and ssh terminal), terminate one of them does not cause 403 forbidden. 
but it shows 403 forbidden error page right after i terminated all connections.
 
i can find two types of error in apache error.log while it shows 403 forbidden page.
 
```
 
(13)Permission denied: access to / denied

```
 
```
 
(13)Permission denied: /home/user/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

```
(one strange part is my DocumentRoot is /home/user/www not /home/user)
 
i gave 755 permission to all files and directories in DocumentRoot(which is /home/user/www), but still apache show me the forbidden error page right after logout.
i use ubuntu 10.04 lts and i use apt-get command to install all package that i'm using now (apache,mysql,php,mrtg,snmpd,vsftpd,ssh,etc).
 
any suggestion would be great.
these are my virtual host config file and apache2.conf. (httpd.conf is empty)
 
```
 
<VirtualHost *:80>
DocumentRoot /home/user/www/
<Directory /home/user/www/>
Options FollowSymLinks Includes ExecCGI IncludesNoEXEC MultiViews
AllowOverride all
Order allow,deny
Allow from all
</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
ErrorLog /var/log/apache2/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog /var/log/apache2/access.log combined
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>

```
 
apache2.conf
```
 
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
<IfModule mpm_prefork_module>
StartServers 5
MinSpareServers 5
MaxSpareServers 10
MaxClients 150
MaxRequestsPerChild 0
</IfModule>
<IfModule mpm_worker_module>
StartServers 2
MinSpareThreads 25
MaxSpareThreads 75
ThreadLimit 64
ThreadsPerChild 25
MaxClients 150
MaxRequestsPerChild 0
</IfModule>
<IfModule mpm_event_module>
StartServers 2
MaxClients 150
MinSpareThreads 25
MaxSpareThreads 75
ThreadLimit 64
ThreadsPerChild 25
MaxRequestsPerChild 0
</IfModule>
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
Order allow,deny
Deny from all
Satisfy all
</Files>
DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/
ServerName grand

```
 
thanks
 
 
ps. everytime i restarted apache, i got this error in error.log 
PHP Deprecated: Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
i don't think it's relevant with my problem. but just in case...

---

### Post by elico on 2011-02-11
i dont understand yet.
i think i do but im not sure.

you have apache..
you are using a remote machine to access your apache server machine.
so if you turn on the apache machine without humen touch everything works fine?
then you login remotely and still it works fine.
and then whenever you do logout when you are trying to access the apache server from remote computer you are getting 403 error?

so try to do two things.
one is to change the  /home/user/www to other  directory and make sure that all the files in /home/user/www are owned by www-data or whatever user your apache is using.
and the other option is to make permissions for the files there to 777 just to make sure it's really a permission stuff.

---

### Post by intomb on 2011-02-11
after i change my DocumentRoot from /home/user/www to /var/www, it magically worked!
THANK YOU SO MUCH!
 
but i'd like to make it work from /home/user/www. 
could you give me a little advice?
 
i wrote some details down for clarification.
 
A. turn on apache server machine or reboot -> forbidden error page
B. booting sequence completed but not logged in -> forbidden error page
 
C.1 logged into server machine from another computer by ssh -> everything works fine
C.2 logged into server machine from physical console directly -> everything works fine
C.3 logged into server machine both from physical console and another computer(ssh) -> everything works fine
 
D.1 terminate ssh terminal log-in session -> forbidden error page immediately
D.2 terminate physical console log-in session -> forbidden error page immediately
D.3.A terminate one of log-in session and another session stay logged in -> everything works fine
D.3.B terminate every(or last remaining) log-in session -> forbidden error page immidiately
 
and file permissions are
/home - owned by user(both owner/group) - 755 [chown root:root for /home doesn't solve my problem]
/home/user - owned by user(both owner/group) - 755
/home/user/www - owned by user(both owner/group) - 755
every files and directories in /home/user/www except mrtg related - owned by user(both owner/group) - 755
 
/var - owned by root(both owner/group) - 755
/var/www - owned by user(both owner/group) - 755

---

### Post by psarasp on 2012-11-28
I have the same problem. In my case i have encrypt my home folder during Ubuntu installation so when i logout Apache can't read my home folder.

---

