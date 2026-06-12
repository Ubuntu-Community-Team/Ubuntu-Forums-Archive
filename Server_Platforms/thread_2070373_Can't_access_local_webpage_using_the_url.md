---
title: "Can't access local webpage using the url"
date: 2012-10-12
forum: Server Platforms
---

### Post by aerojun on 2012-10-12
Good evening,

I am using Ubuntu 12.04 Server on VMWare; I have instaled BIND9 and Apache2 and created a DNS Server and Web Server.

I'm trying to make a local webpage ("www.interwebs.edu.mx") that anyone in my LAN can access it, but everytime i ping the url, it says it can't find the host (This is while using any other PC, not the server). When i use the server it finds it.
**[COLOR=Red]Everything was configured as ROOT.[/COLOR]**

These are my files:
**[SIZE=3][COLOR=Red]DNS[/COLOR][/SIZE]**
[COLOR=Red]**dom12498.edu.mx.fwd**[/COLOR]
```

$ORIGIN dom12498.edu.mx.
;
; BIND data file for local loopback interface
;
$TTL    3D
@       SOA     SERVER-10.dom12498.edu.mx.     root.dom12498.edu.mx. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@       IN      NS      SERVER-10.dom12498.edu.mx.
@    IN    A    127.0.0.1
@    IN    AAAA    ::1
SERVER-10.dom12498.edu.mx.       IN      A       192.168.1.110
PC-10.dom12498.edu.mx.    IN    A    192.168.1.210
www    IN    CNAME    SERVER-10.dom12498.edu.mx

```**[COLOR=Red]dom12498.edu.mx.rev[/COLOR]**
```
$ORIGIN 1.168.192.in-addr.arpa.
;
; BIND reverse data file for local loopback interface
;
$TTL    3D
@       SOA     SERVER-10.dom12498.edu.mx.  localhost.dom12498.edu.mx. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@       IN      NS      SERVER-10.dom12498.edu.mx.
110     IN      PTR     SERVER-10.dom12498.edu.mx.
210    IN    PTR    PC-10.dom12498.edu.mx.

```[COLOR=Red]**named.conf.local**[/COLOR]
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization

zone "dom12498.edu.mx" {
    type master;
    file "/etc/bind/dom12498.edu.mx.fwd";
    allow-query { any; };
};

zone "interwebs.edu.mx" {
    type master;
    file "/etc/bind/dom12498.edu.mx.fwd";
    allow-query { any; };
};

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/dom12498.edu.mx.rev";
    allow-query { any; };
};

include "/etc/bind/zones.rfc1918";

```[SIZE=3]**[COLOR=Red]WEB SERVER[/COLOR]**[/SIZE]
**[COLOR=Red]interwebs.edu.mx.conf[/COLOR]**
```

<VirtualHost *:80>
ServerAdmin webmaster@interwebs.edu.mx
DocumentRoot /var/www
ServerName interwebs.edu.mx
ServerAlias www.interwebs.edu.mx *interwebs.edu.mx
DirectoryIndex index.html
ErrorLog /var/log/apache2/error.log

<Directory /var/www>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>

</VirtualHost>

```**[COLOR=Red]/etc/apache2/sites-available/interwebs.edu.mx[/COLOR]**
```

<VirtualHost *:80>
    ServerName www.interwebs.edu.mx
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

```[COLOR=Red]**httpd.conf**[/COLOR]
```
ServerName SERVER-10.dom12498.edu.mx

```/etc/hosts
```

127.0.0.1    localhost
127.0.1.1    ubuntu
192.168.1.110    www.interwebs.edu.mx

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```**[COLOR=Red]/etc/resolv.conf[/COLOR]**
```
search dom12498.edu.mx
nameserver 192.168.1.110
```Some Screenshots:
[IMG]http://i.imgur.com/wexiU.png?1[/IMG]
[IMG]http://i.imgur.com/rzdQN.png?1[/IMG]


[IMG]http://i.imgur.com/2f9Kz.png[/IMG]

You have my gratitude.

---

