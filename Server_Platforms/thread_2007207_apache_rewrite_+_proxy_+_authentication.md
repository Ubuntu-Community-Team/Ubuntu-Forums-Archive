---
title: "apache rewrite + proxy + authentication"
date: 2012-06-20
forum: Server Platforms
---

### Post by atomsk81 on 2012-06-20
hello all,

so here's my situation:

**The Problem/Requirements:**

I got one machine on my local network which runs 2 services (sabnzbd and torrentflux the php client for torrents). There is no dns since it is only one machine, so lets say this machine has ip 192.168.1.2 on the local network. 

I can access the two services in my LAN from these URLs:
[U]
[http://192.168.1.2/torrentflux](http://192.168.1.2/torrentflux)[/U]  (port:80)[U]
[http://192.168.1.2:8080/sabnzbd](http://192.168.1.2:8080/sabnzbd)[/U] 

what i am trying to do first is to create two virtual host files (one for each service) that are placed in /etc/apache2/sites-available (and /sites-enabled when enabled) so that when i visit the above URLs i will get redirected to port 443 (https) so basically to make this more clear:

**1st case:** visit--> _[http://192.168.1.2/torrentflux](http://192.168.1.2/torrentflux)_ --> redirected to _[https://192.168.1.2/torrentflux](https://192.168.1.2/torrentflux)_
**2nd case: **visit--> _[http://192.168.1.2:8080/sabnzbd](http://192.168.1.2:8080/sabnzbd) _--> redirected to _[https://192.168.1.2/sabznbd](https://192.168.1.2/sabznbd) _

from there i can open the 443 external port of my router and have the applications being served externally by accessing _[https://myip/torrentflux](https://myip/torrentflux) _and _[https://myip/sabnzbd](https://myip/sabnzbd)_. 
Additionally i require authentication whenever i visit these two URLs, either locally or externally there should always be authentication. 

**The Solution:**

So I came up with the following two vhost files but they don't work quite right. The behavior is the following:

**1st case: **visit--> _[http://192.168.1.2:8080/sabnzbd](http://192.168.1.2:8080/sabnzbd)_ --> redirected to https version and prompted with selfsigned certificate acceptance page --> accept --> prompted with apache authentication dialogue box --> enter username/password --> enter the site. The overall behavior is CORRECT.
**2nd case: **visit --> _[http://192.168.1.2/torrentflux](http://192.168.1.2/torrentflux)_ --> redirected to https version and prompted with selfsigned certificate acceptance page --> accept --> [COLOR=Red]**NO apache authentication dialogue box**[/COLOR] --> enter the site. Behavior is wrong since in this case for some reason apache authentication is being bypassed.

also whenever i reload apache configuration when these two virtual hosts are enabled i get the following warning:

```
[warn] _default_ VirtualHost overlap on port 443, the first has precedence

```and the VHOST files:

Maybe there's a simpler way of doing this, but i'm not an expert, i've tried looking for examples but i couldn't find much. Any help will be appreciated. Thanks.

**sabnzbd vhost**
```

<VirtualHost *:80>
    ServerName 192.168.1.2

   <Location />
      RedirectPermanent / https://192.168.1.2/
   </Location>
</VirtualHost>

<VirtualHost *:443>
    ServerName 192.168.1.2

    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>

    SSLEngine on
    SSLProxyEngine On
    SSLCertificateFile /etc/apache2/ssl/server.crt
    SSLCertificateKeyFile /etc/apache2/ssl/server.key

    <Location /sabnzbd>
        Order deny,allow
        Allow from all
        AuthType Basic
        AuthName "Abandon all hope ye who enter here"
        AuthUserFile /opt/passwd/sabnzbd
        Require valid-user
        ProxyPass http://localhost:8080/sabnzbd
        ProxyPassReverse http://localhost:8080/sabnzbd
    </Location>

    ErrorLog /var/log/apache2/nzb-error.log
    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn
    CustomLog /var/log/apache2/nzb-access.log combined
    CookieLog /var/log/apache2/nzb-cookie.log
</VirtualHost>
```[B]
torrentflux vhost[/B]
```
<VirtualHost *:80>
        RewriteEngine on
        ReWriteCond %{SERVER_PORT} !^443$
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]
</VirtualHost>

<VirtualHost *:443>
    DocumentRoot /usr/share/torrentflux/www/

    SSLEngine on
    SSLCertificateFile /etc/apache2/ssl/server.crt
    SSLCertificateKeyFile /etc/apache2/ssl/server.key

    <Location />
        Order deny,allow
        Allow from all
        AuthType Basic
        AuthName "Abandon all hope ye who enter here"
        AuthUserFile /opt/passwd/sabnzbd
        Require valid-user
    </Location>

    ErrorLog /var/log/apache2/nzb-error.log
    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn
    CustomLog /var/log/apache2/nzb-access.log combined
    CookieLog /var/log/apache2/nzb-cookie.log
</VirtualHost>
```

---

### Post by SeijiSensei on 2012-06-20
You can have only one SSL listener per IP address without jumping through some hoops.  You're better off putting the SSL vhosts in separate directories below the DocumentRoot.

If you have complete control over your network and can assign IP addresses at will, then you can fix the problem by adding a "virtual interface" like this:

```
/sbin/ifconfig eth0:0 192.168.1.204 netmask 255.255.255.0 broadcast 192.168.1.255
```

If you use DHCP make sure this address is outside the range of client addresses the DHCP server manages.  You can put this command in /etc/rc.local or add an entry in /etc/network/faces like:

```

auto eth0:0
iface eth0:0 inet static
  address 192.168.1.204
  netmask 255.255.255.0
  broadcast 192.168.1.255

```

Do not include a "gateway" directive for this address; it will use the previously defined default gateway.

Now in one of your virtual host definitions, add this:

```

Listen 192.168.1.204:443
<VirtualHost 192.168.1.204:443>
   ServerName another.example.com
   [stuff]
</VirtualHost>

```

Restart Apache.  You should be able to make an SSL connection to each of the IP addresses and get different sites.

---

### Post by atomsk81 on 2012-06-21
hello,
thanks for you reply

Your approach seems ok but I believe it's too much for my case. I just want to serve the applications on the same IP under a different directory. I'm hoping to find an alternative that has small amendments in my configuration since I almost got it right. If i don't succeed I will try configuring one service to a different IP as you said.

thanks again :)

---

### Post by SeijiSensei on 2012-06-21
Well, you can try this approach: [http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI](http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI)

That's the only other option besides using separate IP addresses if you want to support multiple SSL connections.

---

