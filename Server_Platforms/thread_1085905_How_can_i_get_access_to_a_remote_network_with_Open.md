---
title: "How can i get access to a remote network with OpenVPN?"
date: 2009-03-03
forum: Server Platforms
---

### Post by BlackDex on 2009-03-03
Hello there,

I have just setup an OpenVPN server.
It kinda works with connecting etc..
And i even can access the Samba share located on that same server.

That server has an IP of 10.0.0.10.
The IP of the VPN is 10.0.1.1.

On a Windows platform i can access the VPN and use both of the above IP's to access the Samba share.

What i can not, is access routers/printers/access-points that are on that 10.0.0.x network.

There is a route set to "10.0.0.0 255.255.255.0", so if i am correct it should route all the requests to the 10.0.0.0 network over the VPN, but it seems it does this only for the server where the VPN-Server is on also.


In short, i can't access any networked devices on that 10.0.0.0 network. How can i fix this problem???

Here is the current server config: [http://pastebin.com/f4ebfc998](http://pastebin.com/f4ebfc998)

---

### Post by jlintz on 2009-03-04
Whats your routing table look like on your server?

---

### Post by BlackDex on 2009-03-05
I Kinda fixed it now.
Changed the gateway of the printer to that of the server, and now it is fixed.

---

