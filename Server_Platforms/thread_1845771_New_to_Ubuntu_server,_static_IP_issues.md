---
title: "New to Ubuntu server, static IP issues"
date: 2011-09-17
forum: Server Platforms
---

### Post by Eldar11 on 2011-09-17
I installed Ubuntu server 10.04 successfully, and configured with DHCP.

I don't know what to use for a static ip address, and when I choose a number that would seem to work, i can't connect once I change the /etc/network/interfaces file, the computer won't connect to the network. I have no experience with a full CLI interface and have been away from Ubuntu for a while. I'm looking to jump back into it, and I need some help starting out.

One other question is, can you install Ubuntu desktop and just add the necessary packages to have the same functionality?

---

### Post by haqking on 2011-09-17
> **Eldar11 said:**
> I installed Ubuntu server 10.04 successfully, and configured with DHCP.

I don't know what to use for a static ip address, and when I choose a number that would seem to work, i can't connect once I change the /etc/network/interfaces file, the computer won't connect to the network. I have no experience with a full CLI interface and have been away from Ubuntu for a while. I'm looking to jump back into it, and I need some help starting out.

One other question is, can you install Ubuntu desktop and just add the necessary packages to have the same functionality?

see here instead of me typing [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html) a little ways down for statics.

Only you can decide on the numbering scheme though, servers are usually low towards the router IP or towards the end of the range, so if you have a 192.168.0.x network then your router is usally 192.168.0 1 and your server or servers may be say 192.168.0.250 or similar but up to you.

 make sure you enter the correct GW and mask though, your GW in my example is 192.168.0.1 and the mask is a /24 or written as 255.255.255.0

You can add server packages to a desktop edition yes, a server is defined usually by its service and not its OS, you could also add a Desktop GUI to your Server but not recommended, but if just a small home net work then you can without a problem as long as you have enough memory and HDD space

```
sudo apt-get install ubuntu-desktop
```

---

