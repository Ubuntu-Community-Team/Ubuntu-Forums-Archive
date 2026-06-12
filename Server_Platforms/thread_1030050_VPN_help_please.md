---
title: "VPN help please"
date: 2009-01-04
forum: Server Platforms
---

### Post by djanie78 on 2009-01-04
Right here's how my network goes

internet-->firewall-->router-->ubuntu server
[COLOR="White"]........................................[/COLOR]|
[COLOR="White"]........................................[/COLOR]|
[COLOR="White"]........................................[/COLOR] -->Three other boxes 

My default gateway is my router. Am not running and DNS on my LAN
The router is also the DHCP server 

The ubuntu server is running VPN. I can connect to it from the internet with no problems. 

When i connect to the ubuntu server via VPN, is there a way i can have access to the three other boxes on the LAN

AM i making any sense at all????

I can access the ubuntu server via its LAN address through a VPN pipe. I cant however access any other thing on the LAN. 

Any help please????

---

### Post by HermanAB on 2009-01-04
Well, if the other boxes have NFS/Samba shares mounted on the server, then you should be able to access those.  Makes sense?

Otherwise, don't use a VPN, but rather install SSH Server then you can do anything.

Cheers,

Herman

---

### Post by mbeach on 2009-01-04
if you are using openvpn, this link may outline what you are trying to do:
[http://openvpn.net/index.php/documentation/howto.html#scope](http://openvpn.net/index.php/documentation/howto.html#scope)

---

### Post by djanie78 on 2009-01-05
Thanks guys will check all your suggestions out and report back

---

