---
title: "squid proxy and https and certificate"
date: 2016-02-17
forum: Server Platforms
---

### Post by mohamed26 on 2016-02-17
hi 
am hosting a hotspot business for mobiles only , and i want to add a transparent proxy(cache)server like squid ,am very noob to this ,after googling around i got this fact:-
you can't cache https websites like facebook and youtube without first distribute "manually" a certificate file to all clients devices.
with manually i meant i have to go to the client device and insert the cer file with my hands 
please tell me is that correct ???? 

thank you in advance

---

### Post by SeijiSensei on 2016-02-17
If you want to use a self-signed certificate on the proxy, then yes, you will need to install it on every client.  

Squid's ssl_bump feature forwards your requests to remote HTTPS sites, then masquerades itself as the remote server when talking to the clients.  If the clients do not "trust" the proxy, you'll see complaints about a potential "man-in-the-middle" attack.

I don't know if you can get around this issue by using a commercial SSL certificate on the proxy.  Have you read the SSLBump documentation here: [http://wiki.squid-cache.org/Features/SslBump]("http://wiki.squid-cache.org/Features/SslBump")?  If you're using Squid 3.5, follow the links on that page for documentation of the method used in that version.

---

