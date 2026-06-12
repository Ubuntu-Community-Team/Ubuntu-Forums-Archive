---
title: "virtual machines running servers"
date: 2009-07-22
forum: Server Platforms
---

### Post by Canuckelhead on 2009-07-22
My situation is this...
I have my box at home which I can easily connect to using DynDns.  I've configured my router to forward port 80...  Everything works great and has for ages... 

I'd like to run additional servers on virtual machines on the same box.  I'd like to be able to use DynDns for to connect to each of the VMs.

I do not know how I can route the traffic to the appropriate VMs?  One is easy...  Several?  I'm stuck...

I know that it would be much easier to use virtual hosts on the same server but that is not what I'm looking to do... 

Any ideas on where I can start?

Anybody ever hear of something that can do name based routing?

---

### Post by Thirtysixway on 2009-07-22
You can use mod_proxy along with virtualhosts to forward traffic to different servers based on the domain name.

I'm running Ubuntu server 8.04 with Apache as the host (along with vmware running the guest OS, windows 2000)

Apache running on host /etc/apache2/httpd.conf
```
<VirtualHost *>
        ServerName SUB.DOMAIN.COM
        DocumentRoot /var/www/subdomainfolder
        ProxyRequests Off

        <Proxy *>
          Order deny,allow
          Allow from all
        </Proxy>

        ProxyPass / http://192.168.1.11/
        ProxyPassReverse / http://192.168.1.11/

	ErrorDocument 503 "The guest server is currently offline."
</VirtualHost>
```

The virtualhost entry takes any requests for sub.domain.com, and forwards them to [http://192.168.1.11](http://192.168.1.11) the internal IP for the guest OS. The response is sent back through the host (hence using mod_proxy, it's acting as proxy here :)) and displayed to the user.
ErrorDocument 503 is used when the guest doesn't respond.

I hope this helps some.

---

### Post by Canuckelhead on 2009-07-23
Perfect!

---

