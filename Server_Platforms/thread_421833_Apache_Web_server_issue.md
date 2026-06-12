---
title: "Apache Web server issue"
date: 2007-04-24
forum: Server Platforms
---

### Post by kphyfe on 2007-04-24
I have a X86 running ubuntu server with gb ram.  I have had a web server running for over 6 months now.  Recently the server is not allowing anyone outside of the lan to see anything.  Error is timeout or server unreachable.  

You can SSH to server from WAN
You can get all webpages from LAN with no timeout issues that is to IP and the Domain name associated with the server.
I can not find any settings that were changed to not allow or timeout request from WAN.

I am running a Linksys 54g wireless router.  It has never been a problem in the past and no upgrades made to it that would cause this change.

I have tried to use the ip to make sure that it had nothing to do with the DNS but still no luck.  I am baffled on this one.  Any help would be great.

Kent

---

### Post by jtc on 2007-04-24
Well, if you haven't changed anything, perhaps the problem lies elsewhere. Might it be so that your ISP has decided to start blocking port 80?

---

### Post by nix4me on 2007-04-24
That would be my guess too.  Alot of isp's don't allow home web servers.

nix4me

---

### Post by dumbsnake on 2007-04-24
It is pretty standard for an ISP to block HTTP.  If they are using advanced packet inspection to block requests then the only option is to install HTTPS and change the port.  If they are merely blocking port 80 (a possibility) then add the line:

```
Listen 81
```

to your httpd.conf file which should be located in your apache directory under ./conf/httpd.conf (atleast that is where it is in apache2 for me).  Then to access your website you just change it to:


```
http://example.com:81/
```

Hope that works for you.  If not, sorry, it is all I know to do.

---

### Post by strixy on 2007-04-26
Did your external IP address change? You may need to update with your DNS host.

---

