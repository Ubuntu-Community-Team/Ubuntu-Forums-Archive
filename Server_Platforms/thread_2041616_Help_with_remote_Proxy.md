---
title: "Help with remote Proxy"
date: 2012-08-13
forum: Server Platforms
---

### Post by taterhead114 on 2012-08-13
I am trying to find a way to forward a way to forward traffic through my Ubuntu box to my other computers (particularly ones outside my local network). I don't need to connect with or remotely use any of the ones on the local network of the server,but I do want to use the IP address (trying to use Netflix on a semi-secure link). I am using the desktop version or Ubuntu for now. Any help getting me in the right direction would greatly be appreciated.

---

### Post by ignore on 2012-08-14
parseConfigFile: squid.conf:4969 unrecognized: 'https_port'

---

### Post by taterhead114 on 2012-08-14
I was able to get what I needed by using ssh and putty set up as a socks proxy. 

I am curious, though I don't think its possible, can I point to my server if it has a non static IP?

---

