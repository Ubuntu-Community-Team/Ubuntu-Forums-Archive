---
title: "Unable to communicate with devices outside of my network"
date: 2014-09-18
forum: Server Platforms
---

### Post by Edward_Collinson on 2014-09-18
Hi,

I am having issues connecting to websites outside of my local network. But I can connect to the server through ssh and Samba on the local network :/

Example here: [http://gyazo.com/ac4a0c2dd8ae897502ff51fd09bc0db2](http://gyazo.com/ac4a0c2dd8ae897502ff51fd09bc0db2)
This also affects things like apt-get with "unable to resolve hostname" error.
My ifconfig is here: [http://pastebin.com/fRvKTV8c](http://pastebin.com/fRvKTV8c)

I assume that it is nothing to do with the IP Setup due it it being able to connect to my PC over Wifi and the rest of my systems in the house :P
Also I am running ubuntu 13.10 if that helps.

Thanks for reading :)

~Ed

---

### Post by Edward_Collinson on 2014-09-18
Infact nevermind, I fixed it by setting the network interface to DHCP

---

