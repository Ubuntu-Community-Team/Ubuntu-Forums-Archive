---
title: "Resolving to IP, not Domain Name"
date: 2014-09-02
forum: Server Platforms
---

### Post by brent12 on 2014-09-02
[COLOR=#000000][FONT=Verdana]I think I made a conf mistake, but spacing out on how to fix...[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Inherited site originally hosted at GoDaddy, used their control panel to point at ns1-5.linode.com.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Used the Linode DNS Manager to make the default records for the domain, everything looks right.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Going to mydomain.com redirects successfully, but switches to the Linode IP address instead of mydomain.com[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]My /etc/hosts (IP obscured)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]127.0.0.1 mydomain.com localhost localhost.localdomain myhostname[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]50.116.**.*** mydomain.com myhostname[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]# The following lines are desirable for IPv6 capable hosts[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]::1 mydomain.com localhost ip6-localhost ip6-loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ff02::1 ip6-allnodes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ff02::2 ip6-allrouters[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]My mydomain.com.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]# domain: mydomain.com[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]# public: /home/public/mydomain.com/[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]<VirtualHost 50.116.**.***:80>[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]# Admin email, Server Name (domain name), and any aliases[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ServerAdmin ***[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ServerName mydomain.com[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ServerAlias [/FONT][/COLOR][www.mydomain.com]("http://www.mydomain.com/")

[COLOR=#000000][FONT=Verdana]# Index file and Document Root (where the public files are located)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]DirectoryIndex index.html index.php[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]DocumentRoot /home/public/mydomain.com/public[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]# Log file locations[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]LogLevel warn[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ErrorLog /home/public/mydomain.com/log/error.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]CustomLog /home/public/mydomain.com/log/access.log combined[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]</VirtualHost>[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]<VirtualHost 50.116.**.***:443>[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]SSLEngine On[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]SSLCertificateFile /etc/ssl/localcerts/apache.pem[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]SSLCertificateKeyFile /etc/ssl/localcerts/apache.key[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]ServerAdmin ***[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ServerName mydomain.com[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]DocumentRoot /home/public/mydomain.com/public[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ErrorLog /home/public/mydomain.com/log/error.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]CustomLog /home/public/mydomain.com/log/access.log combined[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]</VirtualHost>[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]What did I mess up here?[/FONT][/COLOR]

---

### Post by brent12 on 2014-09-02
I am an idiot, there is a commercial shopping cart software installed that was redirecting to the IP address used during setup/testing/etc.

---

