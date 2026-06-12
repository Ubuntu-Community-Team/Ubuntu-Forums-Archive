---
title: "Squid/Wireless config"
date: 2010-10-25
forum: Server Platforms
---

### Post by hobatter on 2010-10-25
Not sure if I should place this in Networking or Server but here it goes. I have a home network that I use for various purposes including a Ubuntu Server which currently hosts a voice server. I have 2 wireless networks because I use WEP for some devices that do not support WPA. I have 3 kids who use the WEP "B"network to which I am hoping to route through a squid proxy server. Currently "B" is a DD-WRT router connected to another router that I repeating. I also use a Samba server that the "A" network uses only. I want the proxy to be a content filter mainly but allow me to see any website denials as well. Maybe use ACL or even something more advanced? The pic below is what I had invisioned but I do not know what IP scheme to give the Squid box. Do I use 1 or 2 ethernet ports for the Proxy and a 3rd for the voice server? I do not know if I bridge a connection on the server to connect the "B" router. If I router DHCP clients through "B" will the proxy be able to see the specific user or just the IP from the router? I am reading a lot and learning a lot. I have been running Linux for a desktop for years but not a advanced user "yet". I hope I didn't ramble too damn much. Thanks.
 
[IMG]http://img100.imageshack.us/img100/3797/homegroup.jpg[/IMG]

---

