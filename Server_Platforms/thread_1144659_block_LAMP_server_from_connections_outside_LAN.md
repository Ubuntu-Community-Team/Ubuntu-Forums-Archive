---
title: "block LAMP server from connections outside LAN"
date: 2009-04-30
forum: Server Platforms
---

### Post by NewbuntuUser777 on 2009-04-30
Hi,

I'm totally new to the server world and networking too for that matter.  

I set up ubuntu LAMP server on an old machine to play around with.  I want to connect it to my router but block connections not coming from the other machine on my LAN.

To complicate things a bit I'd like to use a single keyboard to access both machines on the LAN; an ubuntu desktop and the ubuntu server.  I assume that since they will be networked there's a way to do this but I don't know how to set it up.

Any help would be greatly appreciated.

Thanks!
Dan

---

### Post by doogy2004 on 2009-04-30
check out iptables and ufw

---

### Post by cariboo on 2009-05-01
I have a 4 port kvm in my shop that I use to switch between a desktop computer and two servers, the fourth port is for computers that are in for repairs. Somewhere I picked up to a usb 2 port kvm similar to [this]("http://www.amazon.ca/TRENDnet-2-Port-USB-Switch-Cables/dp/B000F4C310").

---

### Post by HermanAB on 2009-05-01
Howdy,

The router should block public access to the LAMP server by default.

You should install ssh-server for remote access.

---

### Post by Iowan on 2009-05-01
> **HermanAB said:**
> The router should block public access to the LAMP server by default.Agreed. Unless the router port-forwards to the server, it (the server) should be invisible beyond the router.

---

### Post by eentonig on 2009-05-01
By default, your server wont be reachable from the internet, as your router wont know to what ip to forward the external request.

Is your server CLI based. In that case, install an ssh server on it and you'll be able to manage it from the other LAN based machine.

---

