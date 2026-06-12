---
title: "Assign many domains to server"
date: 2014-02-13
forum: Server Platforms
---

### Post by George_Catsicadell on 2014-02-13
hi all, i am George Catsicadellis i am new in this forum and i am a beginner in ubuntu server. i been learning alot about ubuntu by accessing the posts here. and i have successfully installed first time ever ubuntu server. and i am very happy. and i wanted to thank you to ubuntuforums community here for all the help and for all the contributions. i also have a question if you can please help me, after i install ubuntu server, how can i setup my server in such a way that i can assign many domains to server. what i dont understand is my server ip is only one, so how many domains will work. for example how can i make it like a shared server?

many thanks and kind regards,

George Catsicadellis

---

### Post by TheFu on 2014-02-13
Well, your server CAN have multiple IP addresses, but this will mess with routing unless they are on different networks.
I guess you really mean to ask about virtual hosts for web servers?  These are based on the name that the client requests, not the IP.  That also means that only 1 "domain" can have an SSL (HTTPS) connection. There are complex ways around this limitation, but those are dependent on the client having support or setting up a reverse proxy that feeds to many back-end web servers.

So - the way to accomplish this is through web server settings.
Of course, the DNS names all need to point to the same IP or no clients will be directed there. It is better to pay someone else to run the DNS - DNS is hacked all the time.
There are many, many virtualhost how-tos out there. [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3) is one.

What is the limit of web domains per server?  Well that depends on the amount of traffic. I've seen 300 domains on a single server, but as long as the network and disks can keep up, I wouldn't worry.  Whatever you do, please, please, please do NOT enable FTP. Use sftp and ssh connections.

---

### Post by SeijiSensei on 2014-02-13
First, I'd start by reading the [web server section of the Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html").  In general, you want to clone /etc/apache2/sites-available/000-default and edit it to match one of your virtual hosts.  Then use "a2ensite" to enable the site.  (This creates a symbolic link to the file in /etc/apache2/sites-enabled.)  Upon restarting Apache, you should be able to connect to [http://someplace.example.com/](http://someplace.example.com/).

For a more detailed and technical presentation, read this documentation on the Apache site itself: [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

---

### Post by nerdtron on 2014-02-13
HOST MULTIPLE WEB SITES WITH ONE PHYSICAL SERVER (one IP)

 
Install apache2

 ```
sudo apt-get install apache2


```  

Verify that you installed apache2, open the web browser and point it to the IP address of the server.
web browser: [http://192.x.x.x](http://192.x.x.x)

Once verified, go to the www directory and make folder for each site.
```
cd /var/www

 mkdir sitea
 mkdir siteb

```
Copy the html files/webpages for each site on each folder.
Be sure that each folder contains the web files and index.html for each

Make a log directory for each

 mkdir /var/www/logs

Edit the apache2 defaults file.

 nano /etc/apache2/sites-available/default

 
Make it look like this:


 ```
NameVirtualHost *

 

 <VirtualHost *>
 	ServerName sitea.com
 	ServerAlias [www.sitea.com]("http://www.sitea.com/")
 	Document Root /var/www/sitea
 	CustomLog /var/www/logs/sitea.log combined
 	ErrorLog /var/www/logs/sitea.log
 </VirtualHost>
 

 <VirtualHost *>
 	ServerName siteb.com
 	ServerAlias [www.siteb.com]("http://www.sitea.com/")
 	Document Root /var/www/siteb
 	CustomLog /var/www/logs/siteb.log combined
 	ErrorLog /var/www/logs/siteb.log
 	<Files “index.html”>
 		Order Deny, Allow
 		Deny from all
 		Allow from <IP>
 	</Files>
 </VirtualHost>

``` 
Restart apache2
/etc/initd/apache2 restart


NOTE: Now you should have configured your DNS to have A records for both domain to point on a single IP.
Now try browsing the website using the names.

Web browser: 	sitea.com

 Web browser: siteb.com

---

