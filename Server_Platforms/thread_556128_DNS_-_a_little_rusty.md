---
title: "DNS - a little rusty"
date: 2007-09-20
forum: Server Platforms
---

### Post by thepiston on 2007-09-20
ok, i just installed 6.06 LTS LAMP the other day. (I've never used Linux in my life)  Thanks to the ease of Ubuntu, I've got webmin, phpmyadmin, DNS, FTP, SSH all installed and working (mostly).  Here's my question...

Dreamhost is my registrar and host for 8 domains and websites.   I'm trying to use my home connection (static IP) to host with this new server.  How do I go about "unlocking" the DNS that Dreamhost is using now and use my server?  DO I just add the domain as a master zone then put my server's IP address in the nameserver of Dreamhost's panel?  That sounds logical- I think.

Also, while i have you here - how do I find my sites?? I mean, I pull up my IP of the server and I see the "apache installed" info, but how do I, say, find a folder in one of my user's accounts?  For instance, I have about 8 Joomla sites I want to pull over... are those more zones in the DNS config?  like, would I create a zone"abcdef.com" and then direct it to "/etc/home/john/abcdef" ?- am I at least correct in my logic?

---

### Post by twistedtwig on 2007-09-21
welcome to Ubuntu! :)

for the zones part I would use virtualhosts.

I have this Vhosts file:

```
################### default root directory #################

<VirtualHost *>
ServerName houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

</VirtualHost>

################### Charlotte home page #################

<VirtualHost *>
ServerName charlotte.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/charlotte
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName footfaerie.me.uk
Serveralias www.footfaerie.me.uk footfaerie.me.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### gareth west home page #################

<VirtualHost *>
ServerName gareth-west.co.uk
Serveralias www.gareth-west.co.uk gareth-west.co.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/garethwest
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### dale home page #################

<VirtualHost *>
ServerName dale.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/dale
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Ethan home page #################

<VirtualHost *>
ServerName ethan.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/ethan
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Shak home page #################

<VirtualHost *>
ServerName shak.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/shak
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### test home page #################

<VirtualHost *>
ServerName test.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/test
<Directory />
Options FollowSymLinks Indexes
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>
```

in my httpd.conf I have include vhosts.conf (the file with all that stuff in).

I think it took a little fiddling to get fully working but that is the main part.

Not sure about the rest of your post though.  will think about it.

---

### Post by koenn on 2007-09-21
> **twistedtwig said:**
> 
for the zones part I would use virtualhosts.

Even with the virualhosts (which are indeed needed to let apache handle multiple sites), clients (bowsers) would still need to find an ip address for, say, [www.dot.com](www.dot.com) and for blog.dump.org and for downloads.mycoolwebsite.net. 

I'm a bit rusty on DNS myself, but
I think you indeed need a SOA record for each domain ("start of authority"), pointing to your name server, and on your bind, you can then create A (address) records pointing to the web server that the sites live on. From there on it's apache config.

---

### Post by Brazen on 2007-09-21
> **koenn said:**
> Even with the virualhosts (which are indeed needed to let apache handle multiple sites), clients (bowsers) would still need to find an ip address for, say, [www.dot.com](www.dot.com) and for blog.dump.org and for downloads.mycoolwebsite.net. 

I'm a bit rusty on DNS myself, but
I think you indeed need a SOA record for each domain ("start of authority"), pointing to your name server, and on your bind, you can then create A (address) records pointing to the web server that the sites live on. From there on it's apache config.

But he will have to set up a BIND DNS server for this.  Will Dreamhost not let you customize your dns entries?  It would be much better if you could keep the Dreamhost nameservers as your SOA and just change your A records to point to your home IP.

Also, be aware that incoming http requests are blocked on most home internet connections by the ISP.  My ISP (Cox) blocks port 80 so I run a home webserver on port 387 (just a random port I picked) to get around that restriction since this is only used to serve up things for my personal use.

If you are no longer using Dreamhost to host your website, you might be better off switching to GoDaddy for your dns if you have a static public ip or dyndns if you have an ip that is handed out by DHCP from your ISP.

---

### Post by twistedtwig on 2007-09-21
the way I do it is... I have a dynamic ip and use easydns to update my ip with my domain name.

I setup subdomains to all point at the main domain and use virtualhosts to split them back off again

houseofhawkins.com is main domain.
shak.houseofhawkins.com is a subdomain which also points to houseofhawkins.com and the virtualhost changes the documentroot

---

### Post by thepiston on 2007-09-21
ok, I have 8 domains hosted on Dreamhost. I would use BIND to make some DNS entries (directing [www.domain.com](www.domain.com) to a certain folder on the server).  Then I'd use a DynDNA service to update my IP - and then at Dreamhost I'd put something like "piston.easydns.com" as my nameserver?

---

