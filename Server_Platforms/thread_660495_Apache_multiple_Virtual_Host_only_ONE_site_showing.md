---
title: "Apache multiple Virtual Host only ONE site showing???"
date: 2008-01-06
forum: Server Platforms
---

### Post by invar9 on 2008-01-06
OK..... I have looked at all of the post, and I think I have everything set up like the tutorails but my 2 sites are not showing up, only the first one. 
Setup..... Fresh load of 7.10 and Apache. 
I have site [www.ONE.com](www.ONE.com) and site [www.TWO.com](www.TWO.com)
I have pit a index.html in each of the document roots to tell them apart. 
No mater what site I go to ONE or TWO only the ONE will display. It is like apache is not processing the request from the browser. 
I have disabled the default site with the a2dissite 000-default.config to make my [www.ONE.com](www.ONE.com) show up. I just CAN'T get the [www.TWO.com](www.TWO.com) to show up. ANY help will be greatly appreciated. 

Here are the configs. 
SITE [www.ONE.com](www.ONE.com) 
> <VirtualHost *>
DocumentRoot "/var/www/ONE.com/htdocs/"
ServerName [www.ONE.com](www.ONE.com)
<Directory "/var/www/ONE.com/htdocs/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

SITE [www.TWO.com](www.TWO.com)
> <VirtualHost *>
DocumentRoot "/var/www/TWO.com/htdocs/"
ServerName [www.TWO.com](www.TWO.com)
<Directory "/var/www/TWO/htdocs/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>


While I am testing I have my HOSTS file pointing
XXX.XXX.XXX.30     [www.ONE.com](www.ONE.com)
XXX.XXX.XXX.30     [www.TWO.com](www.TWO.com)

All of this was set up through webmin so I don't know if there is a issue with the configs that webmin creates?

I have even tried replacing my ONE and TWO configs with the ones from the tutorials and changing the document roots and server names. 

The apache error logs do not show a error because the ONE site is being served up correctly. 

Again, ANY help will be greatly appreciated and please let m eknow if you need any further information to troubleshoot. 

THank You

---

### Post by Swmmrman on 2008-01-07
I battled this myself.  My solution.  was to go into each virtual servers config. From there i just set the server name of each server.  And no adress.  This worked really well for me.  The first page of apache's area should read like this



 Virtual Server  	Handles the name-based server xxx1.dyndns.org on all addresses
Address Any
Port Any 	Server Name xxx1.dyndns.org 
Document Root /var/www/
Virtual Server 	Handles the name-based server xxx2.dyndns.org on all addresses
Address Any
Port Any 	Server Name xxx2.dyndns.org
Document Root /var/www2

Also after selecting the virtual server at the very bottom is virtual server details.
make sure the top to are set to default.
And the bottom 2 are selected with correct document root and the servers name [www.ONE.com](www.ONE.com) and [www.TWO.com](www.TWO.com)

*Edit* Missed a line of his post.
And as below poster said.  Make sure they are on

---

### Post by k_grdn on 2008-01-07
Hi,

Check the vhosts files exist in /etc/apache2/sites-enabled.

The files should be symlinked to /etc/apache2/sites-available, apache needs to be restarted after the links have been made.

Regards,

k_grdn

---

### Post by Swmmrman on 2008-01-07
Oh by the way i didnt disable the default site.  I just redirected to the 1 site.  The defualt server is still there.  I removed the original folders.  and started my sites.

My first attemp resulted in the same as yours.  It would always load the first site.  Make sure that the adress isnt any!!(Thats why.  I had to set mine to default server)

You directives(Config) match mine perfectly.  Try going in threw webmin and makng sure both Virt servers are set on adress to default server.

---

### Post by omgitsjeckle on 2008-01-18
I am seeming to be having the same issue of only one site showing instead of both as it should be. I've used Webmin to setup the second virtual host, as I don't have much experience setting up Apache (Moved from Abyss Server on a Windows Box)

My hopes were to be able to have multiple 'hosts' running simply on different ports instead of having to use separate addresses. Below are my two host files that have been generated, if someone wouldn't mind taking a look through them and possibly offering some insight as to this problem; on a side note, the listen parameter has been set for both port 80 and 1024.

> 
NameVirtualHost *
<VirtualHost *:80>
ServerAdmin [email]omgitsjeckle@gmail.com[/email]
	
DocumentRoot /home/omgitsjeckle/wwwredirect
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

ErrorLog /home/omgitsjeckle/wwwredirect/error.log

LogLevel warn

CustomLog /home/omgitsjeckle/wwwredirect/access.log "combined"
	ServerSignature On
</VirtualHost>


> 
<VirtualHost *:1024>
DocumentRoot /home/omgitsjeckle/wwwroot
<Directory "/home/omgitsjeckle/wwwroot">
allow from all
Options +Indexes
</Directory>
ErrorLog /home/omgitsjeckle/wwwroot/error.log
LogLevel warn
CustomLog /home/omgitsjeckle/wwwroot/access.log "combined"
ServerPath /home/omgitsjeckle/wwwroot
</VirtualHost>


---

### Post by Vinno on 2008-01-18
Try and put "Listen 1024" in your apache port file. e.g /etc/apache2/ports.conf and restart apache with "sudo /etc/init.d/apache2 restart"
Then using ```
http://localhost:port
```

---

### Post by omgitsjeckle on 2008-01-18
Vinno:

I had already declared the listen parameter from the initial setup of apache. All this appears to be doing at the time, is to allow me to view the default configuration's host (port 80) from port 1024, instead of viewing the host files setup to run when accessed from port 1024.

---

### Post by rfulcher on 2008-03-03
I am having the same issue and can't seem to figure out what the fix is.

I can provide more information on my config.

---

### Post by ctyc on 2008-03-04
I use two entries in httpd.conf per virtual host...it works.

Ex)
#this is to allow the myhub.ca virtualhost to work
<Directory /var/www/one.com/>
        Order allow,deny
        Allow from all
</Directory>

AND)
<VirtualHost *:80>
        ServerName [www.one.com](www.one.com)
        DocumentRoot /var/www/one.com/
</VirtualHost>

---

### Post by rfulcher on 2008-03-04
Here is my setup.  Both files are in the sites-available directory and both have links created with a2ensite in the sites-enabled.

File Name is "sitea"

NameVirtualHost *
<VirtualHost *>
  ServerName [www.sitea.org](www.sitea.org)
  ServerAlias [www.sitea.org](www.sitea.org) sitea.org *.sitea.org
  ServerAdmin [email]rfulcher@siteb.org[/email]
  DocumentRoot /var/www/sitea.org/
  DirectoryIndex default.htm

  <Directory /var/www/sitea.org/>
    Order allow,deny
    Allow from all
  </Directory>

  # Log Files
  ErrorLog /var/www/sitea.org/logs/error.log
  CustomLog /var/www/sitea.org/logs/access.log combined
</VirtualHost>

File name is "siteb"

NameVirtualHost *
    <Virtualhost *>
      DocumentRoot "/var/www/sh"
      ServerName [www.siteb.org](www.siteb.org)
      ServerAdmin [email]rfulcher@siteb.org[/email]
      DirectoryIndex index.html
      ProxyRequests on
      ProxyPreserveHost Off
      ProxyVia full

      <proxy>
        Order deny,allow
        Allow from all
      </proxy>


      ProxyPass        /  [http://live.siteb.local/](http://live.siteb.local/)
      ProxyPass        [http://webster](http://webster) [http://webster](http://webster)
      ProxyPassReverse /  [http://live.siteb.local/](http://live.siteb.local/)
      ProxyPassReverse [http://webster](http://webster) [http://webster](http://webster)
    </Virtualhost>

The thing is when I put in sitea.org or siteb.org I get siteb.org.  If I put in sitea.org/default.htm I can browse the site like normal.

Thanks for any help anyone can provide....

---

### Post by rfulcher on 2008-03-04
Here is the output of the apache2 -S command

[Tue Mar 04 09:19:00 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:*                    is a NameVirtualHost
         default server [www.sitea.org](www.sitea.org) (/etc/apache2/sites-enabled/sitea:3)
         port * namevhost [www.sitea.org](www.sitea.org) (/etc/apache2/sites-enabled/sitea:3)
         port * namevhost [www.siteb.org](www.siteb.org) (/etc/apache2/sites-enabled/siteb:3)
Syntax OK


Just more info.....

---

### Post by rfulcher on 2008-03-04
I disable the siteb and it still tries to go to that site when I put in sitea.

I have no clue why this is not working........

---

### Post by Stephen_at on 2008-03-04
I've got more than 5 websites all with different domain names hosted on my server.

here is the contents of sites-enabled:

[FONT="Courier New"]lrwxrwxrwx 1 root root 28 Feb 26 16:37 050-tetex-doc -> ../sites-available/tetex-doc
lrwxrwxrwx 1 root root 36 Feb 26 17:14 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 36 Feb 29 20:59 camsigh -> /etc/apache2/sites-available/camsigh
lrwxrwxrwx 1 root root 36 Feb 29 20:59 ladykat -> /etc/apache2/sites-available/ladykat
lrwxrwxrwx 1 root root 38 Feb 29 20:59 parthenon -> /etc/apache2/sites-available/parthenon
lrwxrwxrwx 1 root root 32 Feb 29 20:59 pnc -> /etc/apache2/sites-available/pnc
lrwxrwxrwx 1 root root 38 Mar  2 14:46 canalblog -> /etc/apache2/sites-available/canalblog
lrwxrwxrwx 1 root root 32 Mar  2 14:54 ssl -> /etc/apache2/sites-available/ssl[/FONT]

here is sites-available:
[FONT="Courier New"]
-rw-r--r-- 1 root root  339 Feb 29 20:51 tetex-doc
-rw-r--r-- 1 root root  949 Feb 29 20:51 pnc
-rw-r--r-- 1 root root 2012 Feb 29 20:51 camsigh
-rw-r--r-- 1 root root  671 Mar  2 12:51 parthenon
-rw-r--r-- 1 root root  568 Mar  2 12:52 ladykat
-rw-r--r-- 1 root root  601 Mar  2 14:46 canalblog
-rw-r--r-- 1 root root 2568 Mar  2 17:02 default
-rw-r--r-- 1 root root 2501 Mar  3 14:08 ssl[/FONT]

here is the contents of "canalblog":
[FONT="Courier New"]
<VirtualHost *>
ServerName canalplan.blogdns.com
ServerAlias canalplan.homelinux.org
DocumentRoot /webstuff/canalblogs
DirectoryIndex index.php
RewriteEngine on

<directory /webstuff/canalblogs>
RewriteEngine on
AllowOverride FileInfo Options all
</Directory>

<directory /webstuff/canalblogs/forums>
 options FollowSymlinks -Multiviews +ExecCGI
 order Deny,Allow
 Allow from All
 AddHandler cgi-script cgi
RewriteEngine Off
AllowOverride FileInfo Options all
</Directory>


</VirtualHost>[/FONT]

and here is the contents of  pnc:
[FONT="Courier New"]
<VirtualHost *>
ServerName [www.pubnight.org.uk](www.pubnight.org.uk)
ServerAlias pubnight.org.uk
DocumentRoot /webstuff/pnc
Options +ExecCGI FollowSymLinks
RewriteEngine on
DirectoryIndex index.html index.html.var index.pl index.php

# Don't rewrite requests for files in MediaWiki subdirectories,
# MediaWiki PHP files, HTTP error documents, favicon.ico, or robots.txt
RewriteCond %{REQUEST_URI} !^/(stylesheets|images|skins|download|extras)/
RewriteCond %{REQUEST_URI} !^/(redirect|texvc|index).php
RewriteCond %{REQUEST_URI} !^/error/(40(1|3|4)|500).html
RewriteCond %{REQUEST_URI} !^/favicon.ico
RewriteCond %{REQUEST_URI} !^/robots.txt

RewriteRule ^/(.*)$ /index.php/$1 [L,QSA]

</VirtualHost>[/FONT]


This is all on a new server which isn't live yet but by setting my DNS server to give the local IP address for these boxes as 192.168.0.2 I can test them and they all work fine.

---

### Post by rfulcher on 2008-03-04
Things are working now.  I can't pinpoint the exact item but all the posts really helped.

I appreciate everyone contributing.

Ubuntu forums are the best and have the best user on it.  

Thanks very much.

---

### Post by Stephen_at on 2008-03-04
Glad to hear its working!!

---

### Post by ctyc on 2008-03-04
what does the access log say or the error log say.

---

### Post by Railsbuntu on 2008-03-05
Hi,

Did you have to edit your /etc/hosts file?

I am trying to do the same as you.

---

### Post by clw3388 on 2008-04-13
I think alot of what people are missing is the symlinks as indicated on earlier reply (not mine someone else above.. cant remember name)
I too HAD the same problem with only my default site showing...
i read
[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)
and it indicates:
A VirtualHost entry must also be configured for the domain originally hosted on the server ([www.example.com](www.example.com)).

So in other words you have 2 sites. example1.com and example2.com
with what i gather you copied example1.com directives and put it in the default file located at /etc/apache2/sites-available.. this dont work..
(at least it didnt mine)..
You must (according to document) create 2 separate files and setup symlinks to both..

so in /etc/apache2/sites-available you create files called example1 and example2 then edit directives using default as a guide.. once all directives are set for document root, site name, etc,ect, you create symlinks to /etc/apache2/sites-enabled by running the sudo a2ensite example1 and again run it for example2. sudo a2ensite example2. then force a reload of apache (sudo /etc/init.d/apache2 force-reload) (or restart)

Worked for me and my dynamic ip address using dnsexit

---

### Post by Swmmrman on 2008-06-29
Glad to hear you got it working :)

---

