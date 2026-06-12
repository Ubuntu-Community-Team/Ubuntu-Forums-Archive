---
title: "apache - issue with site forwarder"
date: 2008-02-25
forum: Server Platforms
---

### Post by tiger.woods on 2008-02-25
I have a domain mydomain.com setup at GoDaddy that I want to forward to a sub domain yourbox.somedomain.com that is currently setup as a virtual server on my box, can this be done?

I host off of a box at my location - GoDaddy just houses the DNS records.

The site yourbox.somedomain.com resolves and is currently active so all is good there. The problem is I want to create a new domain mydomain.com and have it forward to yourbox.somedomain.com.

The site yourbox.somedomain.com is set up on a linux box using virtual hosting and there is a default Apache website for anything not resolving to any of the virtual hosts, normal setup I believe.

What's happening is that after making the changes at GoDaddy for forwarding mydomain.com and directing it to yourbox.somedomain.com the default website on the server is coming up.

Hopefully some one can give some guidance..

Thanks.

TW,

---

### Post by rapiscan on 2008-02-25
The problem is that Apache doesn't know that mydomain.com belongs to the yourbox.somedomain.com virtual host.  In other words, it doesn't know were it's supposed to send incoming traffic that is requesting mydomain.com.  Try using the ServerAlias directive. In your apache config, go to your VirtualHost section and add the ServerAlias for mydomain.com, like this:

```
ServerAlias mydomain.com
```

Be sure to test your config, then restart apache if the config is ok.

```
sudo apache2ctl configtest
```
```
sudo apache2ctl graceful
```

(This restart code is assuming that you're using apache2).

---

