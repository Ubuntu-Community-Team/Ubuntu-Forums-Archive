---
title: "how to change server name of a request"
date: 2010-07-15
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-15
Hi,
I want to know how can we change the server name of an incoming HTTP_REQUEST  
for example 

A request comes for 

[http://www.mydomain.com](http://www.mydomain.com)

I want this to be served via server on my LAN internally changing the server name to some thing else.
This should not be visible to client browser from internet.

Also in a situation where a request is coming for

 [http://www.mydomain.com/directory1](http://www.mydomain.com/directory1)

[http://www.mydomain.com/directory2](http://www.mydomain.com/directory2)
[http://www.mydomain.com/directory3](http://www.mydomain.com/directory3)

each of these three requests for different directories  I want to be served via different server names on same IP on LAN.
i.e. /directory1 being handled by some thing 
[http://myinternal_server1](http://myinternal_server1)
and /directory2 by [http://myinternal_server2](http://myinternal_server2)

and /directory3 by [http://myinternal_server3](http://myinternal_server3)

where myinternal_server1  myinternal_server2 myinternal_server3 are all on same on IP on lan internally.
I am using Apache2 on Ubuntu 10.04

---

### Post by LepeKaname on 2010-07-15
I'm not sure if I get your question, but it seems that can be solved using a DNS server in your local network and setting for example:

```
myinternal_server2 to 111.222.333.444 (local IP)
```

All of them (the names) will point to the same server. 

If you are using apache, it will just be enough to set the virtualHost in this way:

```
<VirtualHost *:80>
    ServerName  mydomain.com
    ServerAlias www.mydomain.com
    DocumentRoot /var/www/mysite
</VirtualHost>
<VirtualHost *:80>
    ServerName  myinternal_server2
    DocumentRoot /var/www/mysite/directory1
</VirtualHost>

```
I hope that is what you mean.

---

### Post by tapas_mishra on 2010-07-15
Not exactly.Lets take following scenario


A----B

Server A with public IP 
and Server B on LAN.
On Server B many websites.
Document Root of these is as
/var/www/website1
/var/www/website2
/var/www/website3
and also main website 
/var/www/main_website

Server A does not containt data directories.

now from internet a request is coming 

[http://www.mydomain.com](http://www.mydomain.com)

it reaches A 
I want this request to be served via 
/var/www/main_website on B with a server name which is not known to client browser from internet.To the client browser it should appear that request is served by A only on the [www.mydomain.com](www.mydomain.com) client browser should not know about internal_server_B

Also in case of following requests 

[http://www.mydomain.com/website1](http://www.mydomain.com/website1)

it should be handled by apache at A so that it is served via 
contents (we can say document root) in folder
/var/www/website1 at B
internally B is known to A by different hostnames
which I kept in 
/etc/hosts

---

### Post by LepeKaname on 2010-07-16
The only way I know is setting up a proxy. You have plenty of options... Not sure if this link may help you: 

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html)

Other way to do it is using apache and setting all the virtualhosts you need... something like:

```
<VirtualHost *:80>
    ServerName www.mydomain.com
    <Proxy *>
        Order allow,deny
        Allow from all
        #Allow from myhost 
    </Proxy>
    ProxyPass / http://myinternal_server2/directory1/
    ProxyPassReverse / http://myinternal_server2/directory1/
</VirtualHost>
```

More or less like that. You will need the mod_proxy enabled.

I'm sure this is a very slow solution, but at least It works. I have no experience setting other type of proxy (not needed to). If a proxy is what you need, I suggest you to open other thread...

---

### Post by Sanjeevtrip on 2010-07-16
you can setup firewall for port-forwarding to your local webserver

---

