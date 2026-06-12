---
title: "can't see multiple web sites from outside of lan"
date: 2009-10-22
forum: Server Platforms
---

### Post by confusedstingray on 2009-10-22
I have Ubuntu 8.10 and apache2, PHP, Bind9, postfix, squirrelmail.
trying to run 3 - 4 web sites using ip virtualhosts. 
everything works behind router if you type the website address it shows the proper page on all 4 sites but if  I try it from the internet (outside) i get 1 site and errorpage on the others.
here is my apache files 

the httpd.conf
<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from 192.168.1.130
</Location>
<Location /server-info>
    SetHandler server-info
    Order deny,allow
    Deny from all
    Allow from 192.168.1.130 
</Location>

the ports.conf
Listen 192.168.1.104:80
listen 192.168.1.205:80
listen 192.168.1.208:80
<IfModule mod_ssl.c>
Listen 443
</IfModule>

here is www2.conf
<VirtualHost 192.168.1.208>
DocumentRoot /var/www/legodude
ServerName legodude.xxx.ca
ServerAlias [www.legodude.xxx.ca](www.legodude.xxx.ca)
<Directory "/var/www/legodude">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
the other sites are pretty well the same just different ips and root directories

also have my router fowarding port 80 to my server and have i a static ip from my isp and i have my isp set my dns record pointing my websites to the static ip from trial and error it seems to be a problem with bind and apache recieving info from the internet
any help would be great

---

### Post by confusedstingray on 2009-10-22
forgot to mention that the mailserver and squirellmail work from outside and inside 
do not want to play with bind to much

---

### Post by cdenley on 2009-10-22
I suggest you:

-create all vhost configurations in /etc/apache2/sites-available
-enable vhosts with a2ensite
-clear the contents of httpd.conf
-remove www2.conf, wherever you put it
-provide us with the domain names in question and your public IP, or at least verfiy they are all resolving correctly
```

host legodude.xxx.ca
dig @208.67.222.222 +short legodude.xxx.ca
wget -q -O - http://whatismyip.org/ && echo

```
That domain appears to resolve to a [www.dnsmadeeasy.com](www.dnsmadeeasy.com) server, not your server.

---

### Post by confusedstingray on 2009-10-22
all my vhost configurations are in sites-available
i try clearing the httpd.conf
the reall domains are the-halls.ca, legodude.the-halls.ca
and they do resolve to my ip

---

### Post by cdenley on 2009-10-22
Now that you have the vhost configurations in the appropriate place post your vhost configurations.

---

### Post by cariboo on 2009-10-22
I would suggest you shut things down until you get it fixed. I just checked your url and I get a directory listing of everything in your web root.

---

### Post by confusedstingray on 2009-10-22
ok here is one of my vhost conf
cat [www.the-halls.ca.conf](www.the-halls.ca.conf)
<VirtualHost 192.168.0.205>
ServerAdmin [email]bghall@the-halls.ca[/email]
DocumentRoot /var/www/the-halls
ServerName [www.the-halls.ca](www.the-halls.ca)
ServerAlias the-halls.ca
ErrorLog /var/www/the-halls/logs/error_log
<Directory "/var/www/the-halls">
allow from all
Options +Indexes
</Directory>
<Directory "/var/www/the-halls/cgi-bin">
</Directory>
</VirtualHost>

---

### Post by cdenley on 2009-10-22
> **confusedstingray said:**
> ok here is one of my vhost conf
cat [www.the-halls.ca.conf](www.the-halls.ca.conf)
<VirtualHost 192.168.0.205>
ServerAdmin [email]bghall@the-halls.ca[/email]
DocumentRoot /var/www/the-halls
ServerName [www.the-halls.ca](www.the-halls.ca)
ServerAlias the-halls.ca
ErrorLog /var/www/the-halls/logs/error_log
<Directory "/var/www/the-halls">
allow from all
Options +Indexes
</Directory>
<Directory "/var/www/the-halls/cgi-bin">
</Directory>
</VirtualHost>

Well, only seeing one of your vhosts doesn't help us help you with why apache isn't returning different vhosts for different server names. Does that file have a link in /etc/apache2/sites-enabled created by a2ensite? Have you reloaded or restarted apache since enabling it? You don't need to give your vhosts a .conf file extension.

---

### Post by confusedstingray on 2009-10-22
all files have a link in /etc/apache2/sites-enabled and created by a2ensite
cat legodude.the-halls.ca.conf
<VirtualHost 192.168.0.208>
DocumentRoot /var/www/legodude
ServerName legodude.the-halls.ca
ServerAlias legodude.the-halls.ca
<Directory "/var/www/legodude">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

cat watersedge.the-halls.ca.conf
<VirtualHost 192.168.0.200>
ServerAdmin [email]watersedge@the-halls.ca[/email]
DocumentRoot /var/www/watersedge
ServerName watersedge.the-halls.ca
ServerAlias [www.watersedge.the-halls.ca](www.watersedge.the-halls.ca)
ErrorLog /var/www/watersedge/logs/error_log
TransferLog /var/www/watersedge/logs/access_log
<Directory "/var/www/watersedge">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
and apache has been reloaded

---

### Post by cdenley on 2009-10-22
Well your router is going to forward all incoming connections on port 80 to a single LAN IP. If connections are being routed to 192.168.0.208, then legodude.the-halls.ca.conf will be used. If 192.168.0.200, then watersedge.the-halls.ca.conf will be used. What I think you want is to replace all those LAN IP addresses with "*".

---

