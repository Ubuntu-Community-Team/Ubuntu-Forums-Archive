---
title: "Apache 2.2 Port-based Virtual Host Problem"
date: 2010-05-02
forum: Server Platforms
---

### Post by desertoak on 2010-05-02
Hi, 

I have 2 web-servers on diffrent hardware connected to a router who is connected to the internet.

There are two adresses:
webserver-1 exampleserver1.com
webserver-2 exampleserver2.com

When i connect to exampleserver1.com all is fine. (Router-config port-forwarding port 80 to webserver-1)

But when i try connect to exampleserver2.com i must route the traffic to webserver-2. Tried diffrent ports but apache refuse anything but port 80.

Tried to put this in httpd.conf file:

```
You have multiple domains going to the same IP and also want to serve multiple ports. By defining the ports in the "NameVirtualHost" tag, you can allow this to work. If you try using <VirtualHost name:port> without the NameVirtualHost name:port or you try to use the Listen directive, your configuration will not work.

Server configuration

Listen 80
Listen 1194

NameVirtualHost 192.168.0.197:1194

<VirtualHost 192.168.0.197:1194>
ServerName exampleserver2.com
DocumentRoot /var/www
</VirtualHost>

```

But it dosen't work. Am i missing something?

Thanks in advance!

/Daniel
Running Apache 2.2 Ubuntu 10.04

---

