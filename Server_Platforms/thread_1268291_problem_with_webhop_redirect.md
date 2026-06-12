---
title: "problem with webhop redirect"
date: 2009-09-16
forum: Server Platforms
---

### Post by adramalech on 2009-09-16
okay so apache2 listens to port 8080

i have switched from port 80 to 8080 because of the isp blocks 80

now my issue is i have dyndns using webhop....because i need it to use port 8080 but i don't want to use :8080 in my url

so i use [jauntylamp.dnsdojo.net ](jauntylamp.dnsdojo.net ) ---> [ zensoft.dnsdojo.net:8080 ]( zensoft.dnsdojo.net:8080 )

now i get a 404 error when i go to zensoft.dnsdojo.net:8080

this is what i get:

```

404 Not Found

The requested URL / was not found on this server.

Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at zensoft.dnsdojo.net Port 8080


```

in my apache2.conf file i have

ServerName zensoft.dnsdojo.net:8080

in ports.conf i have:

NameVirtualHost zensoft.dnsdojo.net:8080
Listen 8080

i have sites-enabled directory with

zensoft.dnsdojo.net as the file name

in zensoft.dnsdojo.net file i have

VirtualHost zensoft.dnsdojo.net:8080

DocumentRoot /var/www


i really could use some help....i might be just having some minor problem that causes a big issue...i just would like to get this working....

---

### Post by t3r0 on 2009-09-17
Hi,

if this is the only site that you host on that apache server you can remove the NameVirtualHost line from your ports.conf. 

And in your $APACHE_ROOT/sites-enabled/zensoft.dnsdojo.net change the 
<VirtualHost zensoft.dnsdojo.net:8080> to <VirtualHost *:8080>


If this doesn't solve the problem please post all the apache config files related to the site. 

- Tero

---

### Post by adramalech on 2009-09-17
okay thanks it works....

now how should i allow webmin to be accessed remotely from anywhere...

now i tried to bind it to my zensoftdnsdojo.net:10000

but still cannot access it...any suggestions??

---

