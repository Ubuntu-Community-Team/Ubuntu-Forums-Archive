---
title: "Apache two websites one IP"
date: 2011-06-12
forum: Server Platforms
---

### Post by linorics on 2011-06-12
So here is my problem. I have websiteA.com and websiteB.com. I only have one public IP address. And websiteB needs to be constantly restarted, so both need to be on separate apache servers or instances.

Virtual directories wont work cause I can only point websiteA to a directory /var/www/websiteA

Reverse proxy wont work cause I can only catch a sub directory.
Proxy /websiteA/ [www.FQDN.com/websiteA](www.FQDN.com/websiteA)

Does anyone know how I could get this to work in anyway. I'm about to write my own program lol.

---

### Post by volkswagner on 2011-06-12
Apache2 restarts quickly, is it really hurting to restart apache2 if both sites use NameBased virtual hosting?  

I would try to get along with NameBased Virtual hosting... see [sticky]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for how to.

---

### Post by linorics on 2011-06-12
> **volkswagner said:**
> Apache2 restarts quickly, is it really hurting to restart apache2 if both sites use NameBased virtual hosting?  

I would try to get along with NameBased Virtual hosting... see [sticky]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for how to.

I agree but for websiteB.com they constantly cause apache to stop due to them tinkering with the apache config.

---

### Post by BkkBonanza on 2011-06-13
So run two instances of Apache. Or better yet to save memory and keep the server way more efficient switch to Nginx and run two instances of that. Or one instance of Nginx and one of Apache - whatever works. Nginx only uses 1-2 MB of memory for an instance and it's much more efficient than apache. 

Unless you really need to use special features of Apache modules then Nginx will do everything as well or better. You may think about having the website that they keep restarting on Nginx so it doesn't affect your steady site. In most cases the only changes needed to a site when switching to Nginx is rewrite rules (if used), and usually that's simple enough.

Personally I haven't used Apache for more than two years as I consider it a pig now, after switching my sites to Nginx (the #3 web server in the world now according to NetCraft survey).

---

### Post by volkswagner on 2011-06-13
> **linorics said:**
> I agree but for websiteB.com they constantly cause apache to stop due to them tinkering with the apache config.

Perhaps using "reload" will help here.

```
sudo /etc/init.d/apache2 reload
```

---

