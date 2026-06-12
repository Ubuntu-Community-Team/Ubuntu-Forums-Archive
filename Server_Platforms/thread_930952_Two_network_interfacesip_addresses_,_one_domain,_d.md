---
title: "Two network interfaces/ip addresses , one domain, different site"
date: 2008-09-26
forum: Server Platforms
---

### Post by iLLiCiTgr on 2008-09-26
I know the title may be a little confusing.
What i'm trying to do is have a different website shown in public when accessed from the web and a different one shown when accessed by vpn.
This is done for development purposes.

i have already setup apache to listen to all interfaces
Listen 80

i also have this on sites-enabled

NameVirtualHost  10.8.1.1
NameVirtualHost  85.xx.xx.254

<VirtualHost 10.8.1.1>
    ServerName domain.com
    DocumentRoot /var/www/domain-development
...
</VirtualHost>

<VirtualHost 85.xx.xx.254>
    ServerName domain.com
    DocumentRoot /var/www/domain-public
...
</VirtualHost>

i have full access to my vpn and if i access 10.8.1.1 i can see the default listing according to 000-default.

Any ideas? Thanks

---

### Post by lykwydchykyn on 2008-09-27
Did you disable the default site?

---

### Post by iLLiCiTgr on 2008-09-27
You mean 000-default or the public site?
I've tried it both. in every case, only the public site appears even with vpn connected.
I've tried tctdump on the tun0 interface to check vpn traffic

Here is something strange.. when i try to open the site it receives

10:51:51.416622 IP 10.8.1.6.59519 > 85.xx.xx.254.80: F 1437:1437(0) ack 2787 win 16730

When i add the domain to my hosts file and try to open the website it receives

10:50:44.459462 IP 10.8.1.6.59452 > 10.8.1.1.80: . ack 284 win 17267

Like even with openvpn connected and even with the traffic going through openvpn, the header still contains the public ip..

Could this be just a dns issue?

---

