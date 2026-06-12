---
title: "Creating subdomain with Apache without A/AAAA record possible ?"
date: 2014-10-21
forum: Server Platforms
---

### Post by akshayproduct on 2014-10-21
My previous hosting provider always asked me create a A/AAAA record before creating subdomain via virtualhost. Without it, subdomain never worked.

My new hosting provider provides facility only to assign domain name to a IP address in its DNS manager. 

So, I have assigned an ip address to a domain and its working fine. How do I create subdomain now ? I tried using a copy of working virtual host for subdomain (my old server), but its not working.

Is it because domain has a specific ip address ? How do I solve this ? Domain is working fine after creating virtual host. As far as I can find from online forums and discussions, there is no mention of A/AAAA record. How should I get my subdomain working ?

```

[COLOR=#000000][FONT=verdana]<VirtualHost *:80>
# Admin email, Server Name (domain name) and any aliases
ServerAdmin *********gmail.com
ServerName sub.domain.com
ServerAlias sub.domain.com


# Index file and Document Root (where the public files are located)

DirectoryIndex index.php

DocumentRoot /home/ApacheWebsites/subdomain

# Custom log file locations

LogLevel warn

ErrorLog /home/ApacheWebsites/logs/error.log

CustomLog /home/ApacheWebsites/logs/access.log combined
<Directory /home/ApacheWebsites/subdomain/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Require all granted
allow from all
</Directory>

</VirtualHost>



[/FONT][/COLOR]

```

---

### Post by SeijiSensei on 2014-10-21
Add an entry for the "subdomain" (it's really a "hostname") to the DNS records and have it point to the same server.  Apache will handle selecting the proper virtual host definition for the hostname.

---

### Post by akshayproduct on 2014-10-22
I am sorry, that was my bad. I had to enter ip addresses in network/interface before using them.

---

