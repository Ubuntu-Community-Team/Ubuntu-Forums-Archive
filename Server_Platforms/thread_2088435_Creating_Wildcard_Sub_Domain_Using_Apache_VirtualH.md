---
title: "Creating Wildcard Sub Domain Using Apache VirtualHost"
date: 2012-11-26
forum: Server Platforms
---

### Post by robson9776 on 2012-11-26
Dear All,

I want to have this configuration on my server :

1. if user request using this URL : example.com or [www.example.com](www.example.com), user will see index.php in this directory /home/admin1/public_html/

2. but when user request using other sub domain (wildcard) for example : subdomain.example.com, user will see index.php in this path : /home/admin1/public_html/uweb/subdomain.example.com

any sub-domain requested will be satisfied with index.php in this path : /home/admin1/public_html/uweb/***.example.com

technical support on my hosting suggest me to use this method : [http://www.wiredstudios.com/php-programming/setting-up-wildcard-dns-for-subdomains-on-cpanel.html](http://www.wiredstudios.com/php-programming/setting-up-wildcard-dns-for-subdomains-on-cpanel.html)

based on that tutorial, the PHP now has a new job... to redirect on specific folder when user request with sub domain. I don't like this method. for me, it would be better if Apache can handle this.

nearly close to what I need is this method : [http://stackoverflow.com/questions/758351/virtualhost-for-wildcard-subdomain-and-static-subdomain](http://stackoverflow.com/questions/758351/virtualhost-for-wildcard-subdomain-and-static-subdomain)

but, I have a problem with VirtualHost setting, how to create VirtualHost correctly for that situation?

here's what I've done but didn't work :

## I think this one is for www or without www, automatically generated with WHM
<VirtualHost xx.xx.xx.xx:80> 
ServerName example.com
ServerAlias [www.example.com](www.example.com)
DocumentRoot /home/admin1/public_html
</VirtualHost>

## Here's what I'm trying to add
<VirtualHost xx.xx.xx.xx:80>
    ServerName *.example.com
    DocumentRoot /home/admin1/public_html/uweb/%0
</VirtualHost>

please note, I also add DNS record using cPanel :
NAME : *.example.com
TTL : 14400
CLASS : IN
TYPE : A
RECORD : X.X.X.X (my server's IP)

---

### Post by pkadeel on 2012-11-26
I guess this is what you want
[http://httpd.apache.org/docs/2.2/vhosts/mass.html](http://httpd.apache.org/docs/2.2/vhosts/mass.html)

---

