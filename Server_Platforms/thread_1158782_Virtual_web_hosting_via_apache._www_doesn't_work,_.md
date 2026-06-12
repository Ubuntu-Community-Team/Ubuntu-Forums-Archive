---
title: "Virtual web hosting via apache. www doesn't work, but subdomains do."
date: 2009-05-14
forum: Server Platforms
---

### Post by yong_sa on 2009-05-14
Hello:

I upgraded Intrepid to Jaunty and now my apache server is working funny.

[www.*mydomain](www.*mydomain)*.com Doesn't work 
*mydomain*.com Doesn't work

For the two addresses above I get the following messages on firefox:
> The server at [www.*mydomain](www.*mydomain)*.com is taking too long to respond.
and
> The server at *mydomain*.com is taking too long to respond.
respectively.

sub1.*mydomain*.com displays fine
sub2.*mydomain*.com displays fine

Here's what I have for my virtualhosting configuration:

apache2.conf
> # Include the virtual host configurations:

NameVirtualHost *:80
Listen 80

Include /etc/apache2/sites-enabled/

AddType application/x-httpd-php .html


<IfModule mod_ssl.c>
    NameVirtualHost xxx.xxx.xxx.xxx:443
</IfModule>



I have 3 files in the sites-enabled directory in the following order:

sub1.mydomain.com
> 
<VirtualHost *:80>
ServerName sub1.mydomain.com
ServerAlias [www.sub1.mydomain.com](www.sub1.mydomain.com)
ServerAdmin [email]joe@aol.com[/email]

DirectoryIndex index.html index.htm index.php
DocumentRoot /var/sub1.mydomain.com/
</VirtualHost>



[www.mydomain.com](www.mydomain.com)
> 
<VirtualHost *:80>
ServerName [www.mydomain.com](www.mydomain.com)
ServerAlias mydomain.com
ServerAdmin [email]joe@aol.com[/email]

DirectoryIndex index.html index.htm index.php
DocumentRoot /var/www
</VirtualHost>





sub2.mydomain.com
> 
<VirtualHost *:80>
ServerName sub2.mydomain.com
ServerAlias [www.sub2.mydomain.com](www.sub2.mydomain.com)
ServerAdmin [email]joe@aol.com[/email]

DirectoryIndex index.html index.htm index.php
DocumentRoot /var/sub2.mydomain.com/
</VirtualHost>


Other:
When I go to localhost on firefox, it defaults to sub1.mydomain.com
When I go to 127.0.0.1 on firefox, it defaults to sub1.mydomain.com

Any ideas on how to fix this? Thank you in advance for your help!



Sincerely,

yong_sa

---

### Post by yong_sa on 2009-05-14
Nevermind... I suspect that it's a dns propogation / Dynamic IP address issue.

I ping [www.mydomain.com](www.mydomain.com) and mydomain.com and it goes to the old IP.

I ping the sub1.mydomain.com and sub2.mydomain.com and it goes to the new one.

I'll update the subject if this is the case.

-------------

On that note, is there a way to automatically update dynamic ips to a DNS hosting service so that It won't go down whenever my ISP changes the ip address?

---

### Post by a9k3d on 2009-05-14
if you want the default site to be mydomain.com (whereas its sub1 right now) you'll have to change its name in/sites-enabled/ to be alphabetically before the others.

I'd change it from [www.my](www.my)... to 000-my...

You'll have to make the symbolic link manually - a2ensite won't help.

---

