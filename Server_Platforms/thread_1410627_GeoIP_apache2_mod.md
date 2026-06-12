---
title: "GeoIP apache2 mod"
date: 2010-02-19
forum: Server Platforms
---

### Post by bmathis on 2010-02-19
Im looking to use the Apache2 GeoIP mod to block countries from accessing a website. I've searched, but cannot seem to find any information on how to insert the code into the virtual host file. Does anyone know how to get this working or can point me in the right direction?

Thanks

- B

---

### Post by yogesh.girikumar on 2010-02-19
Hi,

You can achieve this by editing the httpd.conf file or the .htaccess file for the virtual host that you want to block countries for.


   Add the following lines to your httpd.conf file:
```
GeoIPEnable on
GeoIPDBFile /path/to/GeoIP.dat
SetEnvIf GEOIP_COUNTRY_CODE CN BlackList
SetEnvIf GEOIP_COUNTRY_CODE KR BlackList
SetEnvIf GEOIP_COUNTRY_CODE US BlackList
SetEnvIf GEOIP_COUNTRY_CODE RU WhiteList
```      Then add this in the VirtualHost configuration file: Mine is at /etc/apache2/sites-enabled/000-default
   ```
<VirtualHost www.myvhost.com:80>
..
[.. snip ..]
..
<directory /path/to_your/ServerRoot/>
Options FollowSymLinks
AllowOverride None
Allow from env=WhiteList
Deny from env=BlackList
</directory>
..
[.. snip ..]
..
</VirtualHost>
```      The country codes used are ISO 3166 country codes. The  GeoIP Database file is usually named GeoIP.dat. You can search your system for it and add it to the httpd.conf file. The "BlackList" and "WhiteList" are names that I chose to be set as Environment Variables. You can use your own.

You can also add this in the .htaccess files ( inside the directories for individual virtual hosts ) for each Virtual Host.
   If you want to allow a specific IP from a country that is denied access, you can explicitly mention it.
For example:
```
Allow from 123.231.132.112
```You can also find a lot of information about this in the GeoIP mod README file. 

     More Info here: [http://www.maxmind.com/app/mod_geoip](http://www.maxmind.com/app/mod_geoip)

---

### Post by bmathis on 2010-02-19
Thank you. With your explanation, I was able to get it working on my web server.

\\:D/

---

