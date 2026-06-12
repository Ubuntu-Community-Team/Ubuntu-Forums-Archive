---
title: "accessing local server from far away..."
date: 2008-02-06
forum: Server Platforms
---

### Post by woodsonoversoul on 2008-02-06
Hi all, I'm running Amrok and have a web interface script installed which brodcast and controls my current playlist. The address I type in to access this is [http://localhost:4774/](http://localhost:4774/). My question is, how would I access this outside of my local network, ie: from work. 

Tips broken down into baby steps are greatly appreciated

---

### Post by freebeer on 2008-02-06
You should be able to replace "locahost" with your home machine's IP address.  If you're behind a router at home, you'll have to forward the necessary ports in your router.

A longer term solution is to get a free dynamic domain name such as "www.myhomemachine.org" then substitute the IP address with the domain name.  Then run a script that checks to see if your IP address changes, which in turn updates your dns entry with the new address.  This way, when your IP address changes, you can still dial into "www.myhomemachine.org" and not have to remember the new IP address.

---

### Post by HermanAB on 2008-02-07
Well, you don't want to expose Amarok to the wild wild world...

So, install OpenSSH, forward port 22 through your router, then connect to the IP address of the router and then you can do whatever you want, including tunnel Amarok over SSH to work.

Buy and read the snail book.

Cheers,

Herman

---

