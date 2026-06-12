---
title: "Connecting to the internet in Vmware without NAT ."
date: 2012-05-17
forum: Virtualisation
---

### Post by Docmero on 2012-05-17
[CENTER]Hi ,
I've installed win 7 64 bit (guest ) on Ubuntu 11.10 (host)via Vmware .
It can connect to the internet via NAT well .
However , I want to connect to the internet directly
on the virtual win 7 without using NAT . I want to use a separate USB adepter .
I brought RT73 wifi USB adepter .
The virtual system detected it and installed the driver .
the system connected to the network and it shows that I'm connected  to the internet .
However , no single app can connect to internet . I logged to the router gate
to make sure I'm connected to the network and It was successful .
Every thing on this network is fine except for not being able to connect to internet .
Thanks

[/CENTER]

---

### Post by Docmero on 2012-05-17
UPDATE :
I solved the problem by disabling  the local are network connection (which uses NAT ) and left the wirless connection only activated . It's working perfectly now . It seems there was a conflict between both networks . Thanks .

---

### Post by dcstar on 2012-05-18
> **Docmero said:**
> UPDATE :
I solved the problem........

Than **Mark** the thread.

---

