---
title: "Apache includes"
date: 2008-11-25
forum: Server Platforms
---

### Post by OOzypal on 2008-11-25
Hello,

After developing a site locally, I uploaded to my reseller account; however, it did not work. My host told me to prepare and an include file that they will connect to my host plan. My VHOST in my local machine is ```

NameVirtualHost 192.168.1.2

<VirtualHost 192.168.1.2>
    <Directory /home/hab/www/html/gp>
        Options FollowSymLinks Indexes
	AllowOverride All
	Allow from All  
       AddCharset            utf-8         .html
    </Directory>
   
     DirectoryIndex index.php
     DocumentRoot /home/hab/www/html/gp/
     ServerName   www.gp.loc
     ServerAlias  *.gp.loc
     AddDefaultCharset  utf-8
     DirectoryIndex index.php index.html
</VirtualHost>


```

How can I make this into include file and should be changed?

---

### Post by sdnelson on 2008-11-25
Take your example and place it in a file - call it myvhost.conf.

Then in one of the conf files under the apache directory add:

Include /your directory/myvhost.conf

Done..

---

### Post by OOzypal on 2008-11-25
Yea but what should I put instead my IP address 192.168.1.2

---

### Post by sdnelson on 2008-11-25
Here's what I do. I have several websites on my servers. 

<VirtualHost <HostAddr or HostName>:80>                         
  ServerName [www.mydomain.com](www.mydomain.com)                  
  ServerAlias mydomain.com *.mydomain.com
  CustomLog /var/log/apache2/mydomain.log common      
  <Directory />                                      
    Options None +FollowSymLinks                     
    AllowOverride None                               
    Order allow,deny                                 
    Allow from all                                   
  </Directory>                                       
  DocumentRoot /var/www/hosts/mydomain
</VirtualHost> 

Hope this helps.

---

### Post by OOzypal on 2008-11-25
yes it did help.

Is it possible to put these config into .htaccess file

---

### Post by sdnelson on 2008-11-25
I don't believe so.. Apache needs to know what to do upon startup and what Vhosts are available.

---

### Post by MJN on 2008-11-26
> **OOzypal said:**
> Yea but what should I put instead my IP address 192.168.1.2Replace it with a wildcard (*) unless you have a specific reason to bind it to one, and only one, address.
 
Note that your NameVirtualHost and VirtualHost directives should match.
 
Mathew

---

