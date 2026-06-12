---
title: "Apache redirect lan 80 requests or serve same website on 2 ports"
date: 2009-10-05
forum: Server Platforms
---

### Post by SilvaRizla on 2009-10-05
My ISP bans port 80 so I'm using port 8888 to serve my site to the wan with a port 80 redirect from no-ip.com

I'd like to save LAN users from having to input myip:**8888** and to be able to just enter myip in the address bar to get to my site.  Is there a way I can have an internal redirect on my LAN or is it possible to serve the site on ports 80 and 8888 at the same time?

---

### Post by cdenley on 2009-10-05
> **SilvaRizla said:**
> My ISP bans port 80 so I'm using port 8888 to serve my site to the wan with a port 80 redirect from no-ip.com

I'd like to save LAN users from having to input myip:**8888** and to be able to just enter myip in the address bar to get to my site.  Is there a way I can have an internal redirect on my LAN or is it possible to serve the site on ports 80 and 8888 at the same time?

You certainly can have your site served on both ports, you just need to edit you vhost configuration and ports.conf file accordingly.
example vhost
```

<VirtualHost *:80 *:8888>
...

```
example ports.conf
```

NameVirtualHost *:80
NameVirtualHost *:8888
Listen 80
Listen 8888

```

It sounds like the request must come through the web on port 8888 in order to get through your ISP. The only way a user can avoid having to specify the port is if an external server proxies all the traffic to your server. I'm not familiar with the services offered by no-ip, but I doubt they will proxy all your traffic. The only other solution would be to have users access your site through a frames page hosted on another server which has one visible frame containing the actual site, hiding the real URL of your server.

EDIT:
Or, of course, you can simply have an external server redirect to the correct URL ([http://mydomain.com:8888/](http://mydomain.com:8888/) or [http://xxx.xxx.xxx.xxx:8888/](http://xxx.xxx.xxx.xxx:8888/)).

---

### Post by arvevans on 2009-10-05
I use a redirection service:

[INDENT]<http://www.dyndns.com/>[/INDENT]

There are several others that do the same thing.
_._

---

### Post by SilvaRizla on 2009-10-06
> **cdenley said:**
> You certainly can have your site served on both ports, you just need to edit you vhost configuration and ports.conf file accordingly.
example vhost
```

<VirtualHost *:80 *:8888>
...

```
example ports.conf
```

NameVirtualHost *:80
NameVirtualHost *:8888
Listen 80
Listen 8888

```


Thanks this is just what I needed

---

