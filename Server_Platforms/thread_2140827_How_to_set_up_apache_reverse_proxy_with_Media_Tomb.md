---
title: "How to set up apache reverse proxy with Media Tomb?"
date: 2013-04-30
forum: Server Platforms
---

### Post by geekman92 on 2013-04-30
Hi there! =)

I'm running ubuntu server 12.04 LTS headless and trying to set up a reverse proxy through apache. What I would like is for me to visit [http://mywebsite.com/media](http://mywebsite.com/media) and it would redirect me to [http://localhost:49152/](http://localhost:49152/). I have managed to successfully do this for Transmission using **[THIS]("http://www.linuxplained.com/transmission-apache-proxy-setup/") **tutorial but can't seem to get it to work for Media Tomb. I have tested that the Media Tomb web interface works by visiting [http://192.168.1.99:49152/](http://192.168.1.99:49152/) and that works successfully but when I try and access it via [http://mywebsite.com/media/](http://mywebsite.com/media/) it only displays the Media Tomb banner and nothing else.

My code in the [COLOR=#000000][FONT=Consolas]/etc/apache2/mods-enabled/proxy.conf file is this:

[/FONT][/COLOR]```
<IfModule mod_proxy.c>

ProxyRequests Off


<Proxy *>
        AddDefaultCharset off
        Order Allow,Deny
        Allow from all
</Proxy>


ProxyPass /transmission http://localhost:9292/transmission
ProxyPassReverse /transmission http://localhost:9292/transmission


ProxyPass /media/ http://localhost:49152/
ProxyPassReverse /media/ http://localhost:49152/


ProxyVia On

</IfModule>

```[COLOR=#000000][FONT=Consolas]

I have done some googling and looked at VirtualHosts and tried this bit of code in my /etc/apache2/site-enabled/000-default but again only the Media Tomb banner appears and nothing else:
[/FONT][/COLOR]
```
<VirtualHost *:80>
        ServerAdmin myemail@gmail.com


        DocumentRoot /var/www
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

    Alias /tomb/ "/usr/share/mediatomb/web/"
   <Directory "/usr/share/mediatomb/web/">
       Options All
       AllowOverride None
       Order allow,deny
       Allow from all
   </Directory>


</VirtualHost>


```[COLOR=#000000][FONT=Consolas]


Please can someone assist me with my problem. I'm not sure what is going wrong as the proxy/VirtualHost seems to be working but it is not loading the entire webpage.

Thanks in advance! =)[/FONT][/COLOR]

---

### Post by TheFu on 2013-05-01
Google found this [http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/4696552](http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/4696552) - doesn't look good for a solution, if this is true.

---

### Post by geekman92 on 2013-05-02
Argh that sucks! :S Looks like I will have to open a port and access it that way! :(

---

