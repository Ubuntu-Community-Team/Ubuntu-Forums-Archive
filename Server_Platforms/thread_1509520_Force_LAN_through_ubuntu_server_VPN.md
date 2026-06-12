---
title: "Force LAN through ubuntu server VPN?"
date: 2010-06-14
forum: Server Platforms
---

### Post by MrQuan on 2010-06-14
I've had my ubuntu server running Karmic happily for a while now. This is my file server, media server, and web server. :-)

Recently I've created a VPN account for my internet traffic so I'm not filtered/recorded (yes Australia's new laws are as invasive as China's :mad:).  Just letting you know it's a legitimate VPN, not for spamming or hacking or anything!  I digress...

This VPN is working fine from my main Windows PC, but I have some laptops and an iPhone that I also want to go through this VPN, but I can only login with one connection at a time - this means only one PC can be VPNed at a time unless I share the connection.  I am able to shared the Windows VPN connection, but my windows PC isn't always on, my ubuntu server is!

This is what *I think* I need to do:

[LIST]
[*]Set up the VPN connection on my ubuntu server that automatically re-connects if there is ever a connection issue.
[*]Share this connection with the LAN over Ethernet and wifi (maybe this will be a proxy setting or something?)
[*]Redirect all Internet traffic through the ubuntu server's VPN connection, and if possible black all direct access to the Internet (perhaps this is a DSL router setting to only allow the ubuntu server?)
[*]This must be compatible with all LAN devices (Linux, Windows, Mac, iPhone).
[/LIST]

I hope someone can help me because this is a bit beyond what I can sort out alone.  I'm not even sure if my stategy is good or not, so any advice is very much appreciated.

Many thanks,
MrQuan

---

