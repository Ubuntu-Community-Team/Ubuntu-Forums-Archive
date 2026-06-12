---
title: "Bittorrent Proxy"
date: 2010-07-26
forum: Security
---

### Post by SailingCyclops on 2010-07-26
Hi:

I want to use a commercial VPN proxy for bittorrent tracker and bi-directional peer communications. I am on Ubuntu 10.04.

Transmission seems to only allow a tracker proxy, and Vuze, while allowing a tracker proxy seems to only allow outbound peer proxies but not incoming.

Is there another client, or patch for Transmission and/or Vuze which will allow me to use bittorrent totally through a proxy server?

Bob

---

### Post by cdenley on 2010-07-26
I don't think this would be possible. When the VPN server receives incoming traffic which isn't related to a connection you established, how is it supposed to know which user the traffic was intended for? The only way this would be possible is if the VPN service dedicated a particular TCP port for your incoming traffic, like port forwarding on a router, or they gave a unique public IP to each VPN user.

---

### Post by SailingCyclops on 2010-07-26
BTGuard does precisely that -- [http://btguard.com/](http://btguard.com/)

The proxy server establishes a public IP for the duration of the Proxy sign-in session, and routes all inbound traffic destined to that IP on any port to the same client port.

---

### Post by cdenley on 2010-07-26
> **SailingCyclops said:**
> BTGuard does precisely that -- [http://btguard.com/](http://btguard.com/)

The proxy server establishes a public IP for the duration of the Proxy sign-in session, and routes all inbound traffic destined to that IP on any port to the same client port.
Are you sure?
> 
**Can I allow incoming connections?**
Incoming connections directly to you are not anonymous. Please ignore any errors regarding incoming connections, you don't want them! 


---

### Post by SailingCyclops on 2010-07-26
You are correct! No inbound. BTGuard is useless. [http://www.cometforums.com/topic/12794868-btguard/](http://www.cometforums.com/topic/12794868-btguard/)

So, I must find a proper vpn tunneling proxy, and an appropriate client. Any suggestions? Anyone?

---

### Post by cdenley on 2010-07-26
I seriously doubt you will be able to find a VPN service that provides you with your own dedicated IP or has any kind of "port forwarding".

---

### Post by wacky_sung on 2010-07-26
Using proxy is kinda useless and costly especially you wanna use it for P2P.Lot of law enforcer are forcing those proxy servers to reveal their clients details using their service.Therefore check out their term & conditions upon signing it up.

---

