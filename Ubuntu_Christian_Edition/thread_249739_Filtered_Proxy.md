---
title: "Filtered Proxy"
date: 2006-09-02
forum: Ubuntu Christian Edition
---

### Post by bkanuka on 2006-09-02
I have [a form of] Ubuntu CE installed, and the web filter works great, but only on this computer.  I want to be able to set up one computer as the filter and have other computers connect through it.  How do I set up this kind of proxy?

---

### Post by CameronCalver on 2006-09-03
yes you firstly have to set up squid then squidguard

---

### Post by deano on 2006-09-03
I would hazard a guess that you can just point your client machines at the ip address of your Ubuntu CE installed machine at port 8080 default dansguardian port.  you may need to also change a ACL in there to allow access from you network.

Other things you would want to do to make life easyer:-

1 give the Ubuntu CE machine a static ip address and add dns servers into /etc/resol.conf

2 install a dhcp server on the Ubuntu CE machine to give ip's to your local network.

I've not currently got Ubuntu CE machine with me, so if i'm wrong hopefully someone will come along and correct me.

cheers
Deano

---

