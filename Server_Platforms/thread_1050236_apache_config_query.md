---
title: "apache config query"
date: 2009-01-25
forum: Server Platforms
---

### Post by pdc124 on 2009-01-25
i want to move a load of stuff to my (new! ) ubuntu server 
currently the config is aranged as 


<virtualHost *:80>
Servername server1.org
DocumentRoot "/var/www/server1.org/htdocs"
ScriptAlias /cgi-bin/ /var/www/server1.org/cgi-bin/

<Directory "/var/www/server1.org/cgi-bin/">
options +ExecCGI
        AllowOverride None
        Order allow,deny
        Allow from all
</Directory>
</virtualHost>


so ive added this to my ubuntu apache config  and have a perl printenv file in cgi-bin/

server@aa1:/etc/apache2$ cat   /etc/apache2/sites-enabled/www.server1.org.conf
<VirtualHost *>
DocumentRoot "/var/www/server1.org/htdocs/"
ServerName [www.server1.org](www.server1.org)
<Directory "/var/www/server1.org/htdocs/">
allow from all
Options +Indexes
</Directory>
ScriptAlias cgi-bin "/var/www/server1.org/cgi-bin"
LogLevel debug
</VirtualHost>
server@aa1:/etc/apache2$                  

adn i get this in the log files 
[Sun Jan 25 17:26:05 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch configured -- resuming normal operations
[Sun Jan 25 17:26:53 2009] [error] [client 192.168.0.203] File does not exist: /var/server1.org/htdocs/cgi-bin
server@aa1:/etc/apache2$                                                   

so its trying to  serve the file from /var/www/ser..../htdocs/cgi-bin 

and not 
/var/www/ser..../cgi-bin/

why ? 


server@aa1:/etc/apache2$ grep ^[A-Za-z\ ] /etc/apache2/apache2.conf
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
    Order allow,deny
    Deny from all
DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
ServerTokens Full
ServerSignature On
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/
ScriptLog /var/log/apache/cgi-log
ScriptLogLength 1000
server@aa1:/etc/apache2$

---

### Post by bapoumba on 2009-01-25
Moved to Servers.

---

