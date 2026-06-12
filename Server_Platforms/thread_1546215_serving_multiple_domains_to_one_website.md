---
title: "serving multiple domains to one website"
date: 2010-08-05
forum: Server Platforms
---

### Post by duceduc on 2010-08-05
I have a domain.com site up and running on my server. I just bought domain.net, domain.org and I would like it to point to the same site on domain.com. I am not sure how to go about doing this.

I used zoneedit for my dns. So far I have pointed my 2 new domains to the same dns as my .com on zoneedit and I have created (A) ip address for them.  If I did this correctly, the new domains are pointing to my server and all is left is to edit the virtualhost?

Was this the correct? I don't know how from here on.

---

### Post by JPorter on 2010-08-05
You need to make sure that the domain registries are all pointing to a nameserver that you can control, and then make sure there are DNS entries on the nameserver for each of the domains, pointing to the right IP.

If the multiple domain names are serving the same content (same "website"), you should set up 301 redirects in Apache or in .htaccess to redirect the secondary domain names to the "primary" domain.  This causes the user's browser to switch to the correct canonical domain name, and prevents the search engines from lowering your organic ranking due to duplicate site content.  

No virtual hosts required if the content isn't different, virtual hosts are used when you want to serve more than one website (with unique content) from a single server or IP.

---

### Post by JPorter on 2010-08-05
[error] dup post

---

### Post by duceduc on 2010-08-05
I fixed my issues by setting up a .htaccess file. Now all 3 domains are pointing to my primary [www.domain.com](www.domain.com)

Here is my code. I changed the script to suit my situation and is working. Is it possible to have fewer lines than how I am having it now? Can I combine 6 lines into 2?
```
RewriteCond %{HTTP_Host} ^(www\.)?secondary-domain1\.com$ [NC]
RewriteRule ^(.*)$ http://www.maindomain.com/$1 [L,R=301]

RewriteCond %{HTTP_Host} ^(www\.)?secondary-domain2\.com$ [NC]
RewriteRule ^(.*)$ http://www.maindomain.com/$1 [L,R=301]

RewriteCond %{HTTP_Host} ^maindomain\.com$ [NC]
RewriteRule ^(.*)$ http://www.maindomain.com/$1 [L,R=301]
```

This is somewhat of an off topic. Before I purchased the other 2 domains, I had one main domain and and a sub domain active on my server. When I purchased the other 2 and setup my nameserver and dns to point to my ip, the domains were directing to my subdomain and not my main. I was curious as why it didn't point to my main domain. I suppose it has to be how I setup my virtualhost for my subdomain. I've looked at it but I don't know what is wrong. 
```
<VirtualHost *:80>

<Directory />
Options FollowSymLinks
AllowOverride all
</Directory>

<Directory /var/www/subdomain/httpdocs/>
Options Indexes FollowSymLinks MultiViews
AllowOverride all
Order allow,deny
allow from all
</Directory>

ErrorLog	/var/www/subdomain/httpdocs/logs/error.log
CustomLog	/var/www/subdomain/httpdocs/logs/access.log combined

ServerName	sub.domain.com
ServerAlias	sub.domain
DocumentRoot	/var/www/subdomain/httpdocs

</VirtualHost>

```

---

