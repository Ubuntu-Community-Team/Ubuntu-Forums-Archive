---
title: "debian lenny server apache2 reverse proxy problem"
date: 2010-04-23
forum: Server Platforms
---

### Post by tapas_mishra on 2010-04-23
I want to host sites.
 [http://www.myserver.com](http://www.myserver.com)
 [http://site1.myserver.com](http://site1.myserver.com)
 I have a public IP rest is on LAN.The main site is on public IP and want any request on site1.myserver.com to be redirected to internal LAN web server which will process the requests.
 I am using a Debian Lenny and apache2.
 

 In an earlier post on the forum I was able to configure Apache Reverse Proxy
  by changing apache2.conf  
 the sites hosted at that time were  
 [http://www.myserver.com](http://www.myserver.com)
 [http://www.myserver.com/site1](http://www.myserver.com/site1)
 

 Now I have formatted my server and it is a fresh installation of Debian Lenny and apache2 on it so previous settings are not there.
 This time I created two virtual hosts.There are two files in /etc/apache2/apache2.conf  
 site1.myserver.com
 and myserver.com
 then  
 a2ensite myserver.com
 a2ensite site1.myserver.com
 

 The configuration of these are as follows
  /etc/apache2/sites-available/myserver.com
 contains
 ```

 NameVirtualHost 10.10.10.10:80
 NameVirtualHost 192.168.1.14:80
 <VirtualHost 192.168.1.14:80 10.10.10.10:80>
 #10.10.10.10 is  my public IP
 #The above idea was from apache documentation http://httpd.apache.org/docs/2.0/vhosts/examples.html
         ServerAdmin webmaster@localhost
         ServerName myserver.com
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
 

 </VirtualHost>
 
```
 

 and the file
 /etc/apache2/sites-available/site1.myserver.com
 has
 

 

 ```

 NameVirtualHost 10.10.10.10:80
 NameVirtualHost 192.168.1.14:80
 <VirtualHost 192.168.1.14:80 10.10.10.10:80>
 #10.10.10.10 is  my public IP
 #The above idea was from apache documentation http://httpd.apache.org/docs/2.0/vhosts/examples.html
         ServerAdmin webmaster@localhost
         ServerName site1.myserver.com
         DocumentRoot /var/www/
         <Directory />
                 Options FollowSymLinks
                 AllowOverride None
         </Directory>
          ProxyRequests off
         <Proxy *>
         Order deny,allow
         Allow from all
         </Proxy>
         ProxyPass / http://192.168.1.6/
         ProxyPassReverse / http://192.168.1.16/
         
   
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
 

 </VirtualHost>
 
```
 

 Then /etc/init.d/apache2 restart .Now If I point my browser to
 [http://www.myserver.com](http://www.myserver.com)
 or [http://site1.myserver.com](http://site1.myserver.com)  
 they both are pointing to same site [http://www.myserver.com](http://www.myserver.com)
 

 I do not have access to DNS.
 In my /etc/hosts
 I have  
 ```

 127.0.0.1       localhost
 192.168.1.14  myserver.com myserver
 192.168.1.6   site1.myserver.com site1
 
```
 I wasted 24 hours on this went through  
 [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)
 [http://httpd.apache.org/docs/2.0/dns-caveats.html](http://httpd.apache.org/docs/2.0/dns-caveats.html)
 [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)
 but still I am not able to catch the problem.
 There is no URL rewriting till now.

---

