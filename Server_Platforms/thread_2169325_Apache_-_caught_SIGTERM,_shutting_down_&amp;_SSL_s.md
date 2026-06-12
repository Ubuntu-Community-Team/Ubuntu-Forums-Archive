---
title: "Apache - caught SIGTERM, shutting down &amp; SSL setup issues."
date: 2013-08-21
forum: Server Platforms
---

### Post by Roasted on 2013-08-21
I'm running Ubuntu Server 12.04.2 on a home server. I'm trying to add SSL support to it and basically shut off port 80 traffic altogether. I went through this guide here:

[http://www.zoharbabin.com/install-ssl-on-ubuntu-and-enable-https](http://www.zoharbabin.com/install-ssl-on-ubuntu-and-enable-https)

With this guide, I had success using a 13.04 virtual machine. I know 13.04 isn't 12.04 server, but it's what I had readily available at the time. With the VM, I had no issues, but I was also using localhost for everything and was not integrating an actual domain name with it, which is where I think this might be fouling up.

Within the error.log for Apache, I have a few entries that is somewhat concerning. It keeps saying that:

```
[warn] RSA server certificate CommonName (CN) 'my.domain.org' does NOT match server name!?
```

Some Googling suggested that perhaps I need to make sure that the CN from when I made the cert versus the ServerName in VirtualHosts need to match. Well... they do. Eh?

Here are my config files:

[/etc/apache2/sites-available/default]("http://paste.ubuntu.com/6011092/")
[/etc/apache2/ports.conf]("http://paste.ubuntu.com/6011087/")

Can anybody see what I'm missing?

EDIT - I am using no-ip.com for my DDNS usage, which is where I got the domain that I am using in the VirtualHosts entry as well as the CommonName for the cert. It was suggested that perhaps no-ip doesn't allow you to use your own certs. Perhaps that could be it? Regardless, do my configs look correct? That's my primary concern at the moment.

---

