---
title: "Apache configuration for Koha"
date: 2007-03-21
forum: Server Platforms
---

### Post by Der_Bettler on 2007-03-21
I am almost finished installing Koha, a F/OSS Integrated Library System, on my box running Edgy. I have all the Perl modules and their dependencies, and the program is installed. Its interface is web-based, using Apache on the localhost to serve the pages. However, when I tried to access the application I found that Apache wasn't running. When I try to start Apache from the CLI, I get the following:

> apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs  

I'm not sure, really, where to start here. To the best of my knowledge, the configuration file is telling Apache to listen to Port 80 (and also Port 8080). Here are the contents of httpd.conf that are not commented out:


> include /etc/koha-httpd.conf
Listen 80
Listen 8080  

It seems to refer to koha-httpd.conf. Here are the contents of that file that are not commented out:


> # KOHA's OPAC Configuration
<VirtualHost RoyalFlamingos:80>
ServerAdmin (email address)
DocumentRoot /usr/local/koha/opac/htdocs
ServerName RoyalFlamingos
ScriptAlias /cgi-bin/koha/ /usr/local/koha/opac/cgi-bin/
Redirect permanent index.html [http://RoyalFlamingos:80/cgi-bin/koha/opac-main.pl](http://RoyalFlamingos:80/cgi-bin/koha/opac-main.pl)
ErrorLog /usr/local/koha/log/opac-error_log
TransferLog /usr/local/koha/log/opac-access_log
SetEnv PERL5LIB "/usr/local/koha/intranet/modules"
SetEnv KOHA_CONF "/etc/koha.conf"

</VirtualHost>

# KOHA's INTRANET Configuration
<VirtualHost RoyalFlamingos:8080>
ServerAdmin (email address)
DocumentRoot /usr/local/koha/intranet/htdocs
ServerName RoyalFlamingos
ScriptAlias /cgi-bin/koha/ "/usr/local/koha/intranet/cgi-bin/"
Redirect permanent index.html [http://RoyalFlamingos:8080/cgi-bin/koha/mainpage.pl](http://RoyalFlamingos:8080/cgi-bin/koha/mainpage.pl)
ErrorLog /usr/local/koha/log/koha-error_log
TransferLog /usr/local/koha/log/koha-access_log
SetEnv PERL5LIB "/usr/local/koha/intranet/modules"
SetEnv KOHA_CONF "/etc/koha.conf"

</VirtualHost>  

So, my question is: What do I check next? I am rather new to using Apache and am trying to organize a small library collection.  Thanks for the help.

---

