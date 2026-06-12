---
title: "zope behind apache reverse proxy css and images broken"
date: 2010-06-07
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-07
Hi,
a reverse proxy scenario

```

Server A              Server B (Zope Application)
Public IP            192.168.1.5
     
```                  
On the first one that is A in Apache vhost file I made 
```

ProxyPass / http://192.168.1.5:8080/VirtualHostBase/http/192.168.1.5:8080/virtual_hosting/VirtualHostRoot/eduCommons

ProxyPassReverse / http://192.168.1.5:8080/VirtualHostBase/http/192.168.1.5:8080/virtual_hosting/VirtualHostRoot/eduCommons

```

but the CSS and images on internet which people are accessing are broken while it is running perfectly fine if I access on LAN.

as
```

http://192.168.1.5:8080/VirtualHostBase/http/192.168.1.5:8080/virtual_hosting/VirtualHostRoot/eduCommons

```
I have checked the  
[URL="http://zope.org/Documentation/Books/ZopeBook/2_6Edition/InstallingZope.stx/VirtualHosting.stx"]
documentation page
[/URL]
and 
[here also ]("http://cheimes.de/opensource/docs/zope-apache2/zope-apache2-3/")

but still the problem persists.

Also on LAN if the same is accessed like this
```

http://192.168.1.5:8080/VirtualHostBase/http/192.168.1.5:80/VirtualHostRoot/eduCommons

```
then CSS and Java script is broken.
It is an eduCommons CMS.
Which I am trying to access via internet.
Any one who have used Zope please let me know if I have done any mistake above?

---

