---
title: "Apache server not accesible from external computers"
date: 2010-12-08
forum: Server Platforms
---

### Post by abillionwishes on 2010-12-08
Hello,

A week ago I purchased an VPS. The first few days I was having trouble to set up an outgoing connection on the VPS. Eventually it turned out to be some misconfiguration of the server where the VPS is hosted on.

Since then I have installed the apache server, but I'm still not able to access the apache server from an external computer. I already have contacted the provider, but they haven't replied yet. To speed things up I was hoping someone could check my configuration to be sure nothing is wrong with it.

To be sure I posted all configuration and information that I think would be important. Please contact me if you need more information.

Server:
```

Ubunut server 10.04 (updated after clean install)

```

Apache server:
```

Server version: Apache/2.2.14 (Ubuntu)
Server built:   Nov 18 2010 21:19:34
**(still running with default configuration, only the loglevel has been set to debug to find any possible problems)**

```

iptables configuration:
```

root@localhost:/# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

netstat:
```

root@localhost:/# netstat -anp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      20321/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      15849/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      32300/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      32300/sshd
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     1796988  1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     1861603  20323/apache2       /var/run/apache2/cgisock.20321

```

ifconfig:
```

root@localhost:/# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8139 (8.1 KB)  TX bytes:8139 (8.1 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:18245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25088355 (25.0 MB)  TX bytes:657932 (657.9 KB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
**(where xxx.xxx.xxx.xxx stands for the IP address of the VPS)**

```

So now I've listed all the generic information, here comes all the configuration related to apache. (I have omitted the comment to keep it as small as possible ;)) (also note that I did not change any configuration after installing apache server, I only have set the loglevel to debug)

/etc/apache2/apache.conf
```

ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
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
LogLevel debug
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

```

/etc/apache2/ports.conf
```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

/etc/apache2/sites-available/default
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
        ErrorLog /var/log/apache2/error.log
        LogLevel debug
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

The *ls* of the */var/www* directory, to ensure nothings wrong with it.
```

root@localhost:/# ls /var/www -l
total 4
-rw-r--r-- 1 root root 177 Dec  7 11:58 index.html

```

Now, so far the configuration. Maybe some more info of interest. If I browse to the VPS from my local computer. The browser displayed an '*503 Service unavailable*' message. I tried to browse the VPS this morning again, but now I'm getting an '*504 Gateway Time-out*'.

If you spot any misconfiguration or other problem, please post an reply. Thanks in advance!

---

### Post by abillionwishes on 2010-12-08
I solved my issue! It was due to an misconfiguration of the site's domain name.

(how can I close this post?)

---

### Post by CharlesA on 2010-12-08
Just mark it as solved from thread tools.

---

