---
title: "router+firewall+samba+cups"
date: 2005-10-23
forum: Server Platforms
---

### Post by merrameu on 2005-10-23
Hi,

I've a pentium II and I want to install in it a ubuntu 5.10 server. 

This ubuntu will works as a firewall, router, and suports a printer. This pentium will have 2 ethernets, one conected to a ADSL and the oter one connected to a switch. Then  4 PC (with windows ) will be connected, with the switch, to internet and print trough this ubuntu.

Could it be possible this, with ubuntu 5.10 server? Any ideas?

Thanks

---

### Post by herrpoon on 2005-10-23
I'm pretty sure that that would be fine, but there are better options if you only want it to use for the purposes described.  A friend uses smoothwall for exactly what you do and I have to say it's rather impressive!  The installation is very easy, just pop in a CD and configure a few things and you're away!

---

### Post by merrameu on 2005-10-23
Thanks,

But, can I share a print with smothwall?

I browsed the info page of smothwall and I can't find anything about share a printer?

Thanks

---

### Post by herrpoon on 2005-10-23
That shouldn't be a problem, all you have to do is install samba and configure it as needed :smile:

---

### Post by wildscribe on 2005-10-23
For security purposes, Smoothwall does not include Samba and support for a print server. I am not sure how difficult it would be to install those programs, but you would be better off by using a second machine for a file and print server rather than having these programs on your router. 

You also might want to try IPcop. [www.ipcop.org](www.ipcop.org)
I have been using it as a router on a Pentium III for the past three years and it works great. Support for multipule public IP addresses and even packet shaping. 

Cheers!

- - - Wild

---

### Post by tvh on 2005-10-24
Never use the router-firewall machine for anything else than routing and firewalling. Get another machine for samba as suggested earliel in this thread. 

I have samba+cups here, NT-style domain that works just like a 'real' M$ server,  totally transparent linux server from the user's point of view. Except it's far better ;)

---

