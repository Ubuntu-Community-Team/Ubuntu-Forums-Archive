---
title: "VPN connection with NetworkManager and manually"
date: 2007-11-08
forum: Server Platforms
---

### Post by RommeDeSerieux on 2007-11-08
I'm setting up a server for a company which accesses the internet with VPN. Installing ubuntu on that server and setting it up went fine, but when i try to connect to vpn, it's horribly slow. I can use IM networks over it and pinging with a large packet size works fine, but when trying to access a webpage, it somewhat freezes shortly after sending the headers and some content. I can wait about 5 minutes for just one webpage to load.

ppp logs show nothing while this is happening, i've double-checked that compression options and mtu are the same on the VPN server (i have access to it) and the machine i'm setting up.

I've tried to set up the same connection on my laptop with Xubuntu 7.10 (the machine i'm experiencing this bug on has Ubuntu Server 7.10 installed) using NetworkManager and it's pptp plugin, and it worked flawlessly. But i can't really use VPN with NetworkManager on a server machine because it will only work if i acquire my IP address via DHCP, which is unacceptable on a NAT gateway, and also requires me to be logged in to work at all.

Had anyone ever experienced this? Is there a way to use NetworkManager's pptp plugin without NetworkManager itself, perhaps?

---

