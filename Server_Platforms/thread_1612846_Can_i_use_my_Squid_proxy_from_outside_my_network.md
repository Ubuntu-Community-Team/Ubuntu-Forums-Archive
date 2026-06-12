---
title: "Can i use my Squid proxy from outside my network?"
date: 2010-11-03
forum: Server Platforms
---

### Post by DFord425 on 2010-11-03
Is it possible to use my Squid Proxy from outside my network and if so, what do i have to change in the squid.conf file so that i can do that. So far, im able to access it from my home network but when i have a friend try to use it from outside the network, it times out for him.

---

### Post by SeijiSensei on 2010-11-03
You have to forward a port on your router back to port 3128 on the Squid box (assuming you're using the default setup).  

That said, it's a very bad idea unless you impose some form of authentication or restrict access by IP address.  Otherwise, some automated process will one day find your open proxy and potentially start using it for nefarious purposes.  You don't want to see a law-enforcement official at your doorstep because it looked like your household was downloading child pornography.

You can try to hide the proxy by forwarding a different port on your router besides 3128 (so-called "security through obscurity"), but scanning tools have ways of finding those as well.

---

### Post by DFord425 on 2010-11-03
Thanks for the heads up. I am already using a different port and i still need to set up authentication for it as well which i will have review the conf file to determine what i need to do. Thanks again.

---

