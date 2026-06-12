---
title: "Apache two domains on two different ip addresses"
date: 2014-10-22
forum: Server Platforms
---

### Post by akshayproduct on 2014-10-22
[COLOR=#000000][FONT=Arial]also asked here : [http://stackoverflow.com/questions/26506320/apache-two-domains-on-two-different-ip-addresses](http://stackoverflow.com/questions/26506320/apache-two-domains-on-two-different-ip-addresses)

I am trying to setup up two different domains on two different ip addresses: bbb.zzz.xxx.yyy & bbb.xxx.yyy.zzz . Problem is, domain1 is working fine. Second site (domain2) is working when I enter ip address in the browser, but it shows content of domain1 when I enter wwww.domain2.com . How should I solve this ? Is there any module missing ? I am using different files in sites-available directory for different domains.[/FONT][/COLOR]
<VirtualHost bbb.zzz.xxx.yyy>
  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin **********@gmail.com
  ServerName domain1.com
  ServerAlias [www.domain2.com](www.domain2.com)

  # Index file and Document Root (where the public files are located)
  DirectoryIndex  index.php
  DocumentRoot /home/ApacheWebsites/domain1/httpdocs

  # Custom log file locations
  LogLevel warn
  ErrorLog /home/ApacheWebsites/logs/error.log


 CustomLog /home/ApacheWebsites/logs/access.log combined


    <Directory /home/ApacheWebsites/domain1/httpdocs/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
           Require all granted
            allow from all
    </Directory>
<VirtualHost bbb.xxx.yyy.zzz>
  # Admin email, Server Name (domain name) and any aliases
      ServerAdmin ************@gmail.com
      ServerName domain2.com
      ServerAlias [www.domain2.com](www.domain2.com)

      # Index file and Document Root (where the public files are located)
      DirectoryIndex  index.php
      DocumentRoot /home/ApacheWebsites/domain2

      # Custom log file locations
      LogLevel warn
      ErrorLog /home/ApacheWebsites/logs/error.log
     CustomLog /home/ApacheWebsites/logs/access.log combined
        <Directory /home/ApacheWebsites/domain2/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
               Require all granted
                allow from all
        </Directory>
</VirtualHost>

---

### Post by SeijiSensei on 2014-10-22
How are the two addresses assigned in the machine?  Do you have multiple network cards, or are you using virtual interfaces like eth0:0?

I'd add ":80" to the end of each <VirtualHost> declaration like this:
```
<VirtualHost 10.10.10.10:80>
```
though I'm not sure that will change matters any.

Which version of Apache is this, 2.2 or 2.4?  Telling us your Ubuntu version will also help.

---

