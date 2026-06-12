---
title: "Apache2: problems with subdomains"
date: 2013-02-05
forum: Server Platforms
---

### Post by renee3 on 2013-02-05
Hi,

I use in my server Ubuntu 12.04 LTS 64 bit operating system and Apache2 2.0 web server software.
I have problems with subdomains. I have domain: example.eu and i'm trying to do subdomain like test.example.eu.

My httpd.conf look like this:
ServerName 127.0.1.1

My /etc/apache2/sites-available/test.example.eu look like this:

<VirtualHost *:80> 
    ServerName example.eu     
ServerAlias [www.example.eu]("http://www.example.eu")
 DocumentRoot /var/www     
<Directory />
 Options FollowSymLinks         
AllowOverride None     
</Directory>
 <Directory /var/www/>         
Options Indexes FollowSymLinks MultiViews
 AllowOverride None         Order allow,deny         allow from all
 </Directory>        DirectoryIndex index.php index.html 
</VirtualHost>
 <VirtualHost *:80>
 ServerName test.example.eu     
DocumentRoot /var/www/
<Directory /var/www/>         
Options Indexes FollowSymLinks         
AllowOverride All         Order Deny,
Allow         Allow from all     </Directory> 
</VirtualHost>

I have also done a2ensite test.example.eu

If i do service apache2 reload , i dont see any error message
But if i try to visit test.exaple.eu with web browser i receive error: Cannot display the web page.

Can anybody give some advice ?

---

### Post by SeijiSensei on 2013-02-05
Do you an entry in /etc/hosts or in your DNS server that resolves test.example.eu to the correct IP address?

---

### Post by Doug S on 2013-02-05
It is a DNS issue and nothing to do with Apache? I.E. Is the client computer able to translate "test.example.eu". Does "nslookup test.example.eu" give an IP address? Examples (for my network): ```
doug@doug-64:~/config/bind$ nslookup s15.smythies.com   [COLOR=red]<<<< exists in DNS[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53
Name:   s15.smythies.com
Address: 192.168.111.112
doug@doug-64:~/config/bind$ nslookup zzz.smythies.com  [COLOR=red]<<<< does not exist in DNS[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53
** server can't find zzz.smythies.com: NXDOMAIN
```Note: I had not seen Seiji's excellent reply above, and I always forget to think about the hosts file option that Seiji mentioned.

---

