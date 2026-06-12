---
title: "apache require ip not functioning"
date: 2017-11-02
forum: Server Platforms
---

### Post by jovian2 on 2017-11-02
Hello all,

Im trying to restrict some websites hosted on my 17.10 Desktop with Apache to be internal on my network only while other sites are public. The sites currently are all accessible from anywhere which is the problem. I have enabled four configs. The default 000-default.conf, nagios.conf, jupiter.com.conf and one called Internal.conf The 000-default one is still default configuration and has not been touched. Jupiter.com is used for external sites, nagios is nagios, and internal is for internal websites.

Here is the config for Internal
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName jupiter/teampass
    DocumentRoot /var/www/html/teampass
    ErrorLog ${APACHE_LOG_DIR}/teampass-error.log
    CustomLog ${APACHE_LOG_DIR}/teampass-access.log combined
        <Directory /var/www/html/teampass>
                Options Indexes FollowSymLinks
                AllowOverride All
                <IfModule mod_authz_core.c>
                  <RequireAny>
                        Require ip 127.0.0.1
                        Require ip ::1
                        Require ip 192.168.8
                  </RequireAny>
                </IfModule>
        </Directory>
</VirtualHost>
```


One thing that comes off as odd is the RequireAny comes up as just white text like its not recognizing it. Require ip does show color so it looks like the module is loaded. I have also tried the following config setting with the same results.

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName jupiter/teampass
    DocumentRoot /var/www/html/teampass
    ErrorLog ${APACHE_LOG_DIR}/teampass-error.log
    CustomLog ${APACHE_LOG_DIR}/teampass-access.log combined
        <Directory /var/www/html/teampass>
                Options Indexes FollowSymLinks
                AllowOverride All
                Require ip 127.0.0.1
                Require ip ::1
        </Directory>
</VirtualHost>
```

Here is some information about my envirionment


```
@Jupiter:~$ apache2ctl -S
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
VirtualHost configuration:
*:80                   is a NameVirtualHost
         default server 127.0.1.1 (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost 127.0.1.1 (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost jupiter/teampass (/etc/apache2/sites-enabled/internal.conf:31)
         port 80 namevhost jupiter/phpmyadmin (/etc/apache2/sites-enabled/internal.conf:51)
         port 80 namevhost redacted_url.net/minecraft (/etc/apache2/sites-enabled/jupiter.com.conf:35)
                 alias [www.redacted_url.net/minecraft](www.redacted_url.net/minecraft)
         port 80 namevhost redacted_url.net/tametheark (/etc/apache2/sites-enabled/jupiter.com.conf:44)
                 alias [www.redacted_url.net/tametheark](www.redacted_url.net/tametheark)
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www/html"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex watchdog-callback: using_defaults
Mutex default: dir="/var/run/apache2/" mechanism=default
Mutex mpm-accept: using_defaults
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
User: name="www-data" id=33 not_used
Group: name="www-data" id=33 not_used
```


In jupiter.com.conf config I am using AuthUserFile to require a site password so I know the configs are being read but cant seem to get require ip to work in any of my congfigs.

```
@Jupiter:~$ apache2 -version
Server version: Apache/2.4.27 (Ubuntu)
Server built:   2017-09-18T15:05:48

```
Any help would be greatly appreciated.

---

### Post by TheFu on 2017-11-02
I think
[B]ServerName jupiter/teampass 
[/B]won't work.

It needs to be a domain name, not what you have there.

BTW, if you used 'code tags', it would be easier to read.  Adv Reply (#)

---

### Post by jovian2 on 2017-11-14
Finally getting back to this project.

The Servername works for me currently, unless you are saying its not compatible with Require IP? Point of this is to make this site internal on my network and not accessible externally while other sites are externally accessible.

Here is the portion of that config in a box:
```

<VirtualHost *:80>    
    ServerAdmin webmaster@localhost
    ServerName jupiter/teampass
    DocumentRoot /var/www/html/teampass
    ErrorLog ${APACHE_LOG_DIR}/teampass-error.log
    CustomLog ${APACHE_LOG_DIR}/teampass-access.log combined
        <Directory /var/www/html/teampass>
                Options Indexes FollowSymLinks
                AllowOverride All
                <IfModule mod_authz_core.c>
                  <RequireAny>
                        Require ip 127.0.0.1
                        Require ip ::1
                        Require ip 192.168.8
                  </RequireAny>
                </IfModule>
        </Directory>
</VirtualHost>

```

You can see the RequireAny not showing colored here:
[IMG]https://i.imgur.com/bn4pd6p.png[/IMG]

---

### Post by jovian2 on 2017-11-15
If anyone has another ideas of making certain sites accessible to only internal while others to the Internet im open to the idea. Just want to secure this before I actually start using it.

---

### Post by TheFu on 2017-11-15
Please see [https://httpd.apache.org/docs/2.4/mod/core.html#servername](https://httpd.apache.org/docs/2.4/mod/core.html#servername) .  I've never seen a ServerName with a '/' - it expects a hostname or FQDN (domainname) which can be resolved via normal DNS or /etc/hosts entries.

Here is what I use.  I don't use IPv6 and have it disabled at the OS level across all my systems.
```

     DocumentRoot /var/www/html
     <Directory /var/www/html/>
       Options +FollowSymlinks
       AllowOverride All
        <RequireAny>
                Require ip 10.1.10
                Require ip 172.22.2
        </RequireAny>

```
Effectively, this forces VPN/SOCKS proxy use to access the website.  It only works from those internal networks.

BTW, using apache for this is just 1 layer.  In security, it is a best practice to have 2 layers of protection. Trusting a single protection scheme is seat-of-the-pants design. The other layer commonly used would be a firewall - either on the router or on the server it self or on the reverse proxy.  
A simple router can't see Name-based servers, so if you are using the same IP for different security levels, that won't work.  A reverse-proxy CAN deal with name-based access. It would be best to run that process on a different system.

---

### Post by jovian2 on 2017-11-20
Thanks for the security suggestions, I do have other items setup to prevent issue. This is more me trying to figure out why this is not functioning as I would expect it to.

Tried the above and changed my config to the following:

```

<VirtualHost *:80>
    ServerName redactedurl.net/teampass
    DocumentRoot /var/www/html/teampass
    ErrorLog ${APACHE_LOG_DIR}/teampass-error.log
    CustomLog ${APACHE_LOG_DIR}/teampass-access.log combined
        <Directory /var/www/html/teampass>
                Options +FollowSymLinks
                AllowOverride All
                  <RequireAny>
                        Require ip 127.0.0.1
                        Require ip ::1
                        Require ip 192.168.8
                  </RequireAny>
        </Directory>
</VirtualHost>

```

With the above im still able to get to the site externally. If I a2dissite the virtual host I am also still able to get to it because of the [COLOR=#000000]000-default.conf virtual host. Maybe this has something to do with it?[/COLOR]

---

### Post by SeijiSensei on 2017-11-20
One simple solution is to create a separate <VirtualHost> that operates on a different port like 8080 and put the local items in there.  Block access to the port from the outside with an iptables rule.

---

