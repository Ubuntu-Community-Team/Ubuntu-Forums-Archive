---
title: "best network configuration?"
date: 2012-10-28
forum: Server Platforms
---

### Post by ieee488 on 2012-10-28
I currently have a cable modem connected to a router by Ethernet cable.

And I have powerline Ethernet devices so that other PCs throughout the home connects to the internet through that router.

I am thinking about adding a server, but I am not sure how to set up a network to include that server.

Should I give the server internet access and have all the PCs access it to get out to the internet?

Or do I have the server be on the network and be almost like any other PC?

As you can see, I am a total newbie at this networking stuff.

---

### Post by littlegreiger on 2012-10-28
It really depends on what you want to do with the server. If you're just using it as a local server for files, backups, etc. I'd just connect it to your router like a regular PC. And if you need access from outside your network just forward the ports through the router to the server.

---

### Post by Habitual on 2012-10-28
> **ieee488 said:**
> ...As you can see, I am a total newbie at this networking stuff.

[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/) may be of some use.

---

### Post by sandyd on 2012-10-28
> **ieee488 said:**
> I currently have a cable modem connected to a router by Ethernet cable.

And I have powerline Ethernet devices so that other PCs throughout the home connects to the internet through that router.

I am thinking about adding a server, but I am not sure how to set up a network to include that server.

Should I give the server internet access and have all the PCs access it to get out to the internet?

Or do I have the server be on the network and be almost like any other PC?

As you can see, I am a total newbie at this networking stuff.
That is really totaly up to you

You could install a firewall distribution such as m0n0wall, Clearos, Vyatta, and put network traffic through it, or with your router, route port 80 to your server for webhosting (if your ISP doesn't block it). The possibilities are endless.

---

### Post by ieee488 on 2012-10-28
Thanks everyone.

I don't want to host a website on this server; I just want to use it to share files across the various PCs in my own network.

---

### Post by kennethconn on 2012-10-29
The most common setup based on your requirements is to just have the server physically installed like any other PC on your network. 

Configuration wise, it should use a static IP address (the other PCs on your network probably get their IP address dynamically from the router).

Have a look at [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

You should also ensure that the IP address you choose for the server is outside the scope or range of dynamic IP addresses that the router provides.

---

