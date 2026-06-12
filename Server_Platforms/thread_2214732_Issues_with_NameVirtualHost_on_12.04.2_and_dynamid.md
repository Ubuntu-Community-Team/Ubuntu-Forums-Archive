---
title: "Issues with NameVirtualHost on 12.04.2 and dynamid DNS"
date: 2014-04-02
forum: Server Platforms
---

### Post by Cool Javelin on 2014-04-02
Hello Fellow Ubuntuoneans: I have implemented an apache2 server on my Ubuntu server (versions below,) and it seems to work, except that all sites I have pointing to my IP address get served up the default "it works" page.

For privacy, I will change the names to protect the innocent, but the details should be correct.

The web URL's include "businesone.com," and "personal.com" without the quotes, of course.

Since I have a dynamic IP address from my cable company, I have utilized a dynamic DNS service (dyn.com) to keep track of my IP address. The info in dyn.com is (for example) "mycomputer.dynalias.com." I have my router setup to keep it updated and it works.

I purchased my domain names from Lowest Domain Rates, and I can use their "domain forwarding" to point to mycomputer.dynalias.com.

Lowest Domain has something called "Masked." I don't know if that is interfering with this issue.
When not selected, and I go to businessone, the URL changes to mycomputer.dynalias.com and the title goes away (maybe because there is no title in the default index.html.)
When Masked IS enabled, the URL doesn't change, and also the title is what I enter into Lowest Domain settings.

In either case, masked or not, when I attempt to go to businessone.com, or personal.com (via Firefox) I get the default "It Works" page.

If I change the order of occurrence in sites-enabled, say from 000-default to 999-default, the next site is the one that gets served up for all attempts. In this case, 200-businessone.

Can someone please help me.

Thanks, Mark.



Software versions:

```
me@UbuntuServer:/etc/apache2$ apache2 -v
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Mar 19 2014 21:10:46
```

```
me@UbuntuServer:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise
```

Here is the result form apache2ctl -S
```
me@UbuntuServer:/etc/apache2$ sudo apache2ctl -S
[Wed Apr 02 17:07:25 2014] [warn] NameVirtualHost *:80 has no VirtualHosts
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server localhost (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost localhost (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost businessone.com (/etc/apache2/sites-enabled/200-businessone:1)
         port 80 namevhost personal.com (/etc/apache2/sites-enabled/600-personal:1)
Syntax OK
```

Here is my sites-enabled directory:
```
me@UbuntuServer:/etc/apache2/sites-enabled$ ls -l
total 0
lrwxrwxrwx 1 root root 26 Mar 28 01:40 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 38 Apr  2 13:31 200-businessone -> /etc/apache2/sites-available/businessone
lrwxrwxrwx 1 root root 35 Apr  2 13:24 600-personal -> /etc/apache2/sites-available/personal
```

Here is my sites-available directory:
```
me@UbuntuServer:/etc/apache2/sites-available$ d
total 28
-rw-r--r-- 1 root root  988 Apr  2 15:38 default
-rw-r--r-- 1 root root 7469 Feb  6  2012 default-ssl
-rw-r--r-- 1 root root 1051 Apr  2 13:12 personal
-rw-r--r-- 1 root root 1040 Apr  2 01:24 businesstwo
-rw-r--r-- 1 root root 1028 Apr  2 01:00 businessone
-rw-r--r-- 1 root root 1058 Apr  1 23:27 another-personal
```

Here is httpd.conf:
```
me@UbuntuServer:/etc/apache2$ cat httpd.conf
NameVirtualHost *:80
ServerName localhost
```

And apache2.conf:
```
me@UbuntuServer:/etc/apache2$ cat apache2.conf
#ServerRoot "/etc/apache2"
LockFile ${APACHE_LOCK_DIR}/accept.lock

PidFile ${APACHE_PID_FILE}

Timeout 300

KeepAlive On

MaxKeepAliveRequests 100

KeepAliveTimeout 5

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
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
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

DefaultType None

HostnameLookups Off

ErrorLog ${APACHE_LOG_DIR}/error.log

LogLevel warn

Include mods-enabled/*.load
Include mods-enabled/*.conf

Include httpd.conf

Include ports.conf

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

Include conf.d/

Include sites-enabled/

```

The contents of default:
```
me@UbuntuServer:/etc/apache2/sites-available$ cat default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/web-default-not-found
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/web-default-not-found/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

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

The contents of business one:
```
me@UbuntuServer:/etc/apache2/sites-available$ cat businessone
<VirtualHost *:80>
        ServerAdmin mark@businessone.com
        ServerName businessone.com
        ServerAlias *.businessone.com
        DocumentRoot /home/web-businessone

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/web-businessone/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

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

Here is the dyn setup page (wildcard is NOT selected.):
```
Hostname:   mycomputer.dynalias.com
Wildcard:              only for DynDNS Pro users
                          create "*.mycomputer.dynalias.com" alias
(for example to use same settings for www.mycomputer.dynalias.com)

Service Type:
  *   Host with IP address
      WebHop Redirect (URL forwarding service)
      Offline Hostname
IP Address:    Your current location's IP address is 12.345.678.90
```

---

### Post by Cool Javelin on 2014-04-02
Added:

How does Apache know which named server to use for which request?

Is the name of the intended URL sent along with the request for the site?

If all requests are coming in on port 80, how does Apache differentiate?

Mark.

---

