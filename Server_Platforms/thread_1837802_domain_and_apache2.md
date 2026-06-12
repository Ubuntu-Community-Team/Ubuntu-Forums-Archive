---
title: "domain and apache2"
date: 2011-09-02
forum: Server Platforms
---

### Post by fingerslip on 2011-09-02
Hello!

I have a server running ubuntu 11.04 x64, I have rtorrent and rutorrent running and want to point also a domain comerestus.tk

I have 2 virtualhost i belive properly configured i used webmin and when I make a tracert it goes to my server ip but in browser doesn't show anything.


```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
 
        DocumentRoot /var/www/
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
 
    <Location /rutorrent>
        AuthType Digest
        AuthName "gods"
        AuthDigestDomain /var/www/rutorrent/ http://94.23.254.218/rutorrent/
 
        AuthDigestProvider file
        AuthUserFile /etc/apache2/passwords
        Require valid-user
        SetEnv R_ENV "/var/www/rutorrent"
    </Location>
 
</VirtualHost>
 
<VirtualHost *:443>
        ServerAdmin webmaster@localhost
 
        SSLEngine on
        SSLCertificateFile /etc/apache2/apache.pem
 
        DocumentRoot /var/www/
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
    <Location /rutorrent>
        AuthType Digest
        AuthName "gods"
        AuthDigestDomain /var/www/rutorrent/ http://94.23.254.218/rutorrent/
 
        AuthDigestProvider file
        AuthUserFile /etc/apache2/passwords
        Require valid-user
        SetEnv R_ENV "/var/www/rutorrent"
     </Location>
</VirtualHost>
``````
<VirtualHost *:80>
DocumentRoot /var/www/comerestus/
ServerName comerestus.tk
<Directory /var/www/comerestus/>
allow from all
Options +Indexes
</Directory>
ServerAlias wwww.comerestus.tk
</VirtualHost>

``````

Tracing route to www.comerestus.tk [94.23.254.218]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  comerestus [192.168.1.1]
  2     7 ms     6 ms     7 ms  10.2.0.1
  3     8 ms     7 ms     7 ms  pa1-84-91-0-105.netvisao.pt [84.91.0.105]
  4     9 ms     7 ms     6 ms  195.219.185.53
  5    46 ms    44 ms    53 ms  80.231.158.10
  6    46 ms    44 ms    45 ms  if-2-2.tcore2.SV8-Highbridge.as6453.net [80.231.
139.1]
  7    45 ms    45 ms    44 ms  if-9-2.tcore1.L78-London.as6453.net [80.231.139.
18]
  8    45 ms    44 ms    44 ms  if-5-2.tcore1.PYE-Paris.as6453.net [80.231.130.2
]
  9   104 ms   203 ms   206 ms  if-11-4.har1.PV0-Paris.as6453.net [80.231.154.30
]
 10    43 ms     *       42 ms  th1-1-6k.fr.eu [213.251.130.49]
 11    48 ms    46 ms    47 ms  rbx-g1-a9.fr.eu [91.121.131.209]
 12    45 ms    46 ms     *     vss-4-6k.routers.ovh.net [91.121.131.162]
 13    55 ms    46 ms    47 ms  ks383852.kimsufi.com [94.23.254.218]

```

---

### Post by 11notes on 2011-09-02
```

<Directory />
        Order Deny,Allow
        Deny from all
        AllowOverride None
        Options -Indexes -Includes -ExecCGI FollowSymLinks
</Directory>


<VirtualHost *:80>
        #Host
        ServerName comerestus.tk
        ServerAlias www.comerestus.tk

        #Roots
        DocumentRoot /var/www/comerestus
        <Directory /var/www/comerestus>
                Order Allow,Deny
                Allow from all
                AllowOverride None
                Options +Indexes -Includes -ExecCGI FollowSymLinks
        </Directory>

        #Logs
        CustomLog /var/www/comerestus/access.log combined
        ErrorLog /var/www/comerestus/error.log
        LogLevel warn
</VirtualHost>


```

---

### Post by fingerslip on 2011-09-02
still not working, maybe it could be from the other has a password protection?

---

### Post by fingerslip on 2011-09-02
I think that is something in my firewall config because I disable it for a few minutes and managed to access the domain can someone take a loog at my iptables.up.rules and if something isn't well.

thx

```
# Generated by iptables-save v1.4.10 on Wed Aug 10 16:16:15 2011
*raw
:PREROUTING ACCEPT [108696:4994576]
:OUTPUT ACCEPT [285366:414332500]
COMMIT
# Completed on Wed Aug 10 16:16:15 2011
# Generated by iptables-save v1.4.10 on Wed Aug 10 16:16:15 2011
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
COMMIT
# Completed on Wed Aug 10 16:16:15 2011
# Generated by iptables-save v1.4.10 on Wed Aug 10 16:16:15 2011
*mangle
:PREROUTING ACCEPT [16:640]
:INPUT ACCEPT [16:640]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [29:43452]
:POSTROUTING ACCEPT [29:43452]
COMMIT
# Completed on Wed Aug 10 16:16:15 2011
# Generated by iptables-save v1.4.10 on Wed Aug 10 16:16:15 2011
*filter
:FORWARD ACCEPT [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
# Accept traffic from internal interfaces
-A INPUT ! -i eth0 -j ACCEPT
# Accept traffic with the ACK flag set
-A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
# Allow incoming data that is part of a connection we established
-A INPUT -m state --state ESTABLISHED -j ACCEPT
# Allow data that is related to existing connections
-A INPUT -m state --state RELATED -j ACCEPT
# Accept responses to DNS queries
-A INPUT -p udp -m udp --dport 1024:65535 --sport 53 -j ACCEPT
# Accept responses to our pings
-A INPUT -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
-A INPUT -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
-A INPUT -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
-A INPUT -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
-A INPUT -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
# Allow connections to our SSH server
-A INPUT -p tcp -m tcp --dport 21976 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
# Allow connections to our IDENT server
-A INPUT -p tcp -m tcp --dport auth -j ACCEPT
# Respond to pings
-A INPUT -p icmp -m icmp --icmp-type echo-request -j ACCEPT
# Protect our NFS server
-A INPUT -p tcp -m tcp --dport 2049:2050 -j DROP
# Protect our X11 display server
-A INPUT -p tcp -m tcp --dport 6000:6063 -j DROP
# Protect our X font server
-A INPUT -p tcp -m tcp --dport 7000:7010 -j DROP
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 50000:60000 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 4500:4600 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 20000 -j ACCEPT
# Allow connections to unprivileged ports
-A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
COMMIT
# Completed on Wed Aug 10 16:16:15 2011
```

Edit: Problem solved somehow i had deleted in firewall port 80

---

