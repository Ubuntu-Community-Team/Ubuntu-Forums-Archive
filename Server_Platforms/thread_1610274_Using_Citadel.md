---
title: "Using Citadel"
date: 2010-10-31
forum: Server Platforms
---

### Post by Vegan on 2010-10-31
I am looking to use Citadel in my machine, some questions come to mind before I install it again on my new server.

Can this tool support phpBB sending mail for activations etc?

Can I use CLI mail commands?

I have noted it can support a vast number of domains.

---

### Post by Vegan on 2010-11-02
Nobody use Citadel?

---

### Post by HermanAB on 2010-11-03
Howdy,

[http://www.aeronetworks.ca/howtos/citadel-ssl-certificate.html](http://www.aeronetworks.ca/howtos/citadel-ssl-certificate.html)
[http://www.aeronetworks.ca/howtos/citadel-basics.html](http://www.aeronetworks.ca/howtos/citadel-basics.html)
[http://www.aeronetworks.ca/howtos/citadel-clients.html](http://www.aeronetworks.ca/howtos/citadel-clients.html)
[http://www.aeronetworks.ca/howtos/citadel-howto.html](http://www.aeronetworks.ca/howtos/citadel-howto.html)
[http://www.aeronetworks.ca/virtualmachines/virtualmachines.html](http://www.aeronetworks.ca/virtualmachines/virtualmachines.html)

Citadel supports all mail protocols and interfaces.  It also has a 'sendmail' utility for compatibility with legacy systems.  So on a server, simply use the usual script methods to send a message.

---

### Post by Vegan on 2010-11-04
I's mot sure how my forum software uses mail, but I suspect its calling sendmail which is the old school mail program.

I have a LAMP stack so I am expecting Citadel to play nice with the existing software.

I tried it and its default is to another port so it seems to be OK.

---

