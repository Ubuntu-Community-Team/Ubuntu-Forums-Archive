---
title: "How to set a static ip"
date: 2013-11-27
forum: Server Platforms
---

### Post by ov10fac on 2013-11-27
OK,  I know this has to have been answered before, but I sure can't find it.  First, it seems silly to me to release a server package that uses a dhcp ip address.  Why would you ever build a server that relies on dhcp.  Most servers I am familiar with use static ips for obvious reasons.  

Ok, so I've vented now, so on to the problem.  I have been looking all over the web to a way to set up static IP in my install of Ubuntu Server 12.04, all to no avail.  I have found things about stopping the network manager, but that's not running on the server.  I have looked for ways to kill dhclient, and nothing seems to work.  I have set up interfaces file and that works when I use ifdown/ifup, but as soon as we reboot right back to dhcp ip address.

Very frustrating for such a simple thing.

So can anyone please tell me how to set up static ips on ubuntu server.  And, yes I know it can be done in the dhcp server, but guess what, thats one of the things I want to use this server to do,  dah...

OK, so any and all ideas gratefully accepted.

---

### Post by rackit on 2013-11-27
Have a look here: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

---

### Post by oldfred on 2013-11-27
See info on static.
[https://help.ubuntu.com/13.04/serverguide/network-configuration.html](https://help.ubuntu.com/13.04/serverguide/network-configuration.html)

But you also have to make sure the address you select is not used anywhere else including the allocated DHCP. My old router allocated 50 or 100 addresses starting at 100, so those could not be used either. My new Comcast router allocates everything and you have to go into Router and exclude an address or tell the router it is manually configured.

---

