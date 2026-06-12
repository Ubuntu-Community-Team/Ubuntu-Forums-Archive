---
title: "domain name to work on LAN"
date: 2005-12-19
forum: Server Platforms
---

### Post by alexj on 2005-12-19
Hi everyone,

The issue might me primitive, I am just a bit lost here.

I am running a mixed network with Ubuntu server. I have a domain name, and I redirect some ports to my server. I set up a couple of A records on external provider, so I can access my sire from outside. I need to be able to access the same server by the domain name from my LAN. What should I do? And is this the right forum to ask this question? 

Thanks

Alex

---

### Post by maglis on 2005-12-19
It is not clear if you have only external DNS server or there is an internal (LAN) DNS server too. You say you have set up dns records on external provider and that you can access these in your internal network. When a machine inside asks for another machine inside, does it get its IP by asking the external DNS server? Does the external DNS server reply with the internal IP address? Does the outside world have direct access to internal IP addresses?

Please make it a bit more clear so we could say something more informative.

---

### Post by alexj on 2005-12-22
[QUOTE=maglis]It is not clear if you have only external DNS server or there is an internal (LAN) DNS server too. You say you have set up dns records on external provider and that you can access these in your internal network. When a machine inside asks for another machine inside, does it get its IP by asking the external DNS server? Does the external DNS server reply with the internal IP address? Does the outside world have direct access to internal IP addresses?

Please make it a bit more clear so we could say something more informative.[/QUOTE]

I am sitting behind a firewall, provided by my hardware router. the same router provides DHCP for my desktops (although I can live without DHCP). I guess the same router acts as a DNS proxy, although I am guessing here.

I did not configure DNS.

External A-records point to my router, that re-directs ports 25, 80 etc to my Ubuntu box

---

### Post by Gandalf on 2005-12-23
Well to use local DNS it's very very easy
Edit /etc/hosts and add to the end of it
```

XXX.XXX.XXX.XXX domain.tld www.domain.tld mail.domain.tld ftp.domain.tld

```

where XXX.XXX.XXX.XXX is your internal IP (if it's on the same computer then it's 127.0.0.1 or if it's another PC then it's something like 192.168.X.X, replace domain.tld with ur domain and extension...

---

### Post by maglis on 2005-12-24
[quote=alexj]I am sitting behind a firewall, provided by my hardware router. the same router provides DHCP for my desktops (although I can live without DHCP). I guess the same router acts as a DNS proxy, although I am guessing here.

I did not configure DNS.

External A-records point to my router, that re-directs ports 25, 80 etc to my Ubuntu box[/quote] Are your internal network IP addresses private or routable? If they (most likely) are private then is your server on a static IP address (most likely)? If this is the case, then the simplest thing to do is put this address to /etc/hosts file on every internal computer. Otherwise they will ask the external DNS server and it will reply with your router's public interface IP address. Then your internal pc will try to contact that address to port 80 on the internal router interface which the router is not able to forward (NAT,PAT) to your internal server. Instead it will propably show its own web configuration interface.

The more envolved solution would be to have a DNS server inside that is configured to forward dns requests that it does not know anything about to the external (ISP) dns server. Then, you need to configure your router's dhcp service to give this dns server to all internal pcs that get ip addresses from it. This way all internal pc's when ask for the web server they will get the internal ip address of the web server. All external pcs that ask for it, will get the public interface of the router which in turn will redirect trafic to internal ip.

---

### Post by majikstreet on 2005-12-24
[QUOTE=Gandalf]Well to use local DNS it's very very easy
Edit /etc/hosts and add to the end of it
```

XXX.XXX.XXX.XXX domain.tld www.domain.tld mail.domain.tld ftp.domain.tld

```

where XXX.XXX.XXX.XXX is your internal IP (if it's on the same computer then it's 127.0.0.1 or if it's another PC then it's something like 192.168.X.X, replace domain.tld with ur domain and extension...[/QUOTE]
that will work. do that :)

theres a way to do it in windows too.

---

