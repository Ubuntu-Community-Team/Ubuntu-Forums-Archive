---
title: "Losing my static IPs"
date: 2011-12-18
forum: Server Platforms
---

### Post by 1_tao on 2011-12-18
Hello - After many years of having static IP addresses from my DSL connection I am switching to Xfinity (Comcast) cable modem service that will have me dealing with dynamic addresses via DHCP.

I have several sites on two boxes that use apache2 set up with the older style httdp.conf. My DNS is handled by freedns.afraid.org and I have installed the latest ddclient which includes the freedns protocol.

My question is what will my edited httpd.conf look like to have it work via ddclient?
 
Here's my httpd.conf:

= = = =

NameVirtualHost 69.9.xxx.xxx
ServerName 69.9.xxx.xxx
<VirtualHost 69.9.xxx.xxx>
        ServerName something.com
        DocumentRoot /www/html
</VirtualHost>

<VirtualHost 69.9.xxx.xxx>
        ServerName something.com
        ServerAlias something.com
        ServerAdmin [email]something@gmail.com[/email]
        DocumentRoot /www/something.com/html/
        ErrorLog /www/something.com/logs/error.log
        CustomLog /www/something.com/logs/access.log common
</VirtualHost>

<VirtualHost etc.

---

### Post by volkswagner on 2011-12-18
You say you have two boxes.  

Are they behind a router?  Does each get a unique DHCP address from your isp?

My immediate reaction was to say just say:

Change:
```
NameVirtualHost 69.9.xxx.xxx
```

to
```
NameVirtualHost *
```
This change would require changing the listen directive to match.

I'm just not sure how you are directing to the different server machines.

Please offer more detail on your network topology.

---

### Post by 1_tao on 2011-12-19
Hello, thanks for your help. 

Can you point me to an example of an httpd.conf file for a server that does virtual hosting inside a cable modem/router?

The two boxes I have that serve several websites currently have their own unique static IPs from my (soon to be) former ISP on a slow DSL connection (one of them did NAT and was the router for my home network). I will be moving them inside a cable-modem/router from Xfinity (Comcast) soon.

The DNS for my hosted websites is handled by freedns.afraid.org and the version of ddclient I'm using supports the freedns protocol. My cursory understanding of how this works is the ddclient periodically tells freedns my public IP, is that right? 

If I change the directive for the NameVirtualHost from its current static IP to a wild card, do I also change the VirtualHost directives below it? 

I think an example of what this looks like will help me. I'm sure many people have a set up like I describe and it may be simple and obvious, but I have only ever employed the static IP style I've been using for 9 years and need to learn how to set up for dynamic IP configuration.

Oh. Please also tell me what you meant by the 'listen directive'

Thanks and let me know if I've left anything out.

---

### Post by Jonathan L on 2011-12-19
> Can you point me to an example of an httpd.conf file for a server that does virtual hosting inside a cable modem/router? [...]


Hi Tao

Here's the portion I think you need.  This server has no "Bind" directive (so binds to all addresses this server has), nor a "Listen" directive, so listens on port 80. See [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

This system has a number of named virtual hosts.  By the time this server is contacted, everything with name resolution has already happened.  (Ie, we've registered the IP address and DNS resolutation has taken place.)  

```
NameVirtualHost *:80

<Directory /var/www/virtuals>
        AllowOverride All
</Directory>

<VirtualHost *:80>
        ServerName example.com
        DocumentRoot /var/www/data
</VirtualHost>

<VirtualHost *:80>
        ServerName www.mydomain.com
        DocumentRoot /var/www/virtuals/www.mydomain.com
</VirtualHost>

<VirtualHost *:80>
        ServerName cat.mydomain.com
        DocumentRoot /var/www/virtuals/cat.mydomain.com
</VirtualHost>

```

Hope that helps.

Kind regards,
Jonathan.

---

