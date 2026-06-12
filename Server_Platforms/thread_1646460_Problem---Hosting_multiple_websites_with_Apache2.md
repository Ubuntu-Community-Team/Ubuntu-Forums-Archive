---
title: "Problem---Hosting multiple websites with Apache2"
date: 2010-12-15
forum: Server Platforms
---

### Post by ekancepts on 2010-12-15
[CENTER]_**I am trying add three namebased virtual hosts in local apache2 webserver**_
_**OS ubuntu 10.10**_


[SIZE=2]_*The three sites are :[www.site1.eka,www.site2.eka,www.site2.eka]("http://www.site1.eka,www.site2.eka,www.site2.eka")*_[/SIZE]
[/CENTER]

[LEFT]_*The first i created a file is virtual.conf in conf.d directory its content is*_ :
[/LEFT]
#
# we're running multiple virtual hosts.
#
NameVirtualHost *:80

Next i created following files in sites-available directory

*_[www.site1.eka]("http://www.site1.eka") is as follows_*

#
#site1.eka (/etc/apache2/sites-available/www.site1.eka)
#
<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@site1.eka"]webmaster@site1.eka[/EMAIL]
        ServerName  [www.site1.eka]("http://www.site1.eka")
        ServerAlias site1.eka

        # Indexes + Directory Root.
        DocumentRoot /var/www/projects/www.site1.eka/htdocs/
        DirectoryIndex index.html
        #DocumentRoot /var/www/projects/www.site1.eka/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/projects/www.site1.eka/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/projects/www.site1.eka/logs/error.log
        CustomLog /var/www/projects/www.site1.eka/logs/access.log combined
</VirtualHost>

*_[www.site2.eka]("http://www.site2.eka") is as follows_*:

#
#site2.eka (/etc/apache2/sites-available/www.site2.eka)
#
<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@site2.eka"]webmaster@site2.eka[/EMAIL]
        ServerName  [www.site2.eka]("http://www.site2.eka")
        ServerAlias site2.eka

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/projects/www.site2.eka/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/projects/www.site2.eka/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/projects/www.site2.eka/logs/error.log
        CustomLog /var/www/projects/www.site2.eka/logs/access.log combined
</VirtualHost>

_*[www.site3.eka]("http://www.site3.eka") is as follows*_

#
#site3.eka (/etc/apache2/sites-available/www.site3.eka)
#
<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@site3.eka"]webmaster@site3.eka[/EMAIL]
        ServerName  [www.site3.eka]("http://www.site3.eka")
        ServerAlias site3.eka

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/projects/www.site3.eka/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/projects/www.site3.eka/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/projects/www.site3.eka/logs/error.log
        CustomLog /var/www/projects/www.site3.eka/logs/access.log combined
</VirtualHost>

Then i edited hosts file in /etc 

*_hosts is as follows_*:

14.96.78.172    eka-Lenovo-G560 # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     eka-Lenovo-G560 localhost6.localdomain6 localhost6
127.0.1.1       eka-Lenovo-G560

#vhosts
*:80       [www.site1.eka]("http://www.site1.eka")
*:80       [www.site2.eka]("http://www.site2.eka")
*:80       [www.site3.eka]("http://www.site3.eka")

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

*Then i ran following commands*

a2ensite [www.site1.eka]("http://www.site1.eka")
a2ensite [www.site2.eka]("http://www.site2.eka")
a2ensite [www.site3.eka]("http://www.site3.eka")

*_Then i restarted apache  /etc/init.d/apache2 restart_*

*_The output of apache2ctl -S_*
VirtualHost configuration:
127.0.0.1:80           127.0.0.1 (/etc/apache2/sites-enabled/000-default:1)
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server [www.site1.eka]("http://www.site1.eka") (/etc/apache2/sites-enabled/www.site1.eka:4)
         port 80 namevhost [www.site1.eka]("http://www.site1.eka") (/etc/apache2/sites-enabled/www.site1.eka:4)
         port 80 namevhost [www.site2.eka]("http://www.site2.eka") (/etc/apache2/sites-enabled/www.site2.eka:4)
         port 80 namevhost [www.site3.eka]("http://www.site3.eka") (/etc/apache2/sites-enabled/www.site3.eka:4)
Syntax OK

*_I also digged the site : dig [www.site1.eka]("http://www.site1.eka")_*

; <<>> DiG 9.7.1-P2 <<>> [www.site1.eka]("http://www.site1.eka")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 7507
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.site1.eka]("http://www.site1.eka").            IN    A

;; AUTHORITY SECTION:
.            8713    IN    SOA    a.root-servers.net. nstld.verisign-grs.com. 2010121500 1800 900 604800 86400

;; Query time: 83 msec
;; SERVER: 121.242.190.210#53(121.242.190.210)
;; WHEN: Thu Dec 16 01:43:48 2010
;; MSG SIZE  rcvd: 106


When i visit the url [http://www.site1.eka/](http://www.site1.eka/) in browser it says server not found.

---

### Post by Ryan Dwyer on 2010-12-16
The entries in your hosts file should say 127.0.0.1, not *:80.

---

### Post by ekancepts on 2010-12-16
The problem solved with the help of Steve -- [http://www.steve.org.uk/](http://www.steve.org.uk/)  & Ryan Dwyer

These are changes he suggested

This is wrong:

> #vhosts
> *:80 [http://www.site1.eka]("http://www.site1.eka/")
> *:80 [http://www.site2.eka]("http://www.site2.eka/")
> *:80 [http://www.site3.eka]("http://www.site3.eka/")

In /etc/hosts you should add the IP addresses of the machines,e.g.

127.0.0.1 [http://www.site1.eka]("http://www.site1.eka/") site1.eka
127.0.0.1 [http://www.site2.eka]("http://www.site2.eka/") site2.eka
127.0.0.1 [http://www.site3.eka]("http://www.site3.eka/") site3.eka

---

### Post by elico on 2010-12-16
well this will help you if you want to access the sites locally on the system.
if you want someone on the internet to access the site you must buy the domain and manage it properly.

---

