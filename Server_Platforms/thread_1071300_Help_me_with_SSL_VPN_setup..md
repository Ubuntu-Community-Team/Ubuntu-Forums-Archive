---
title: "Help me with SSL VPN setup."
date: 2009-02-16
forum: Server Platforms
---

### Post by falconed7 on 2009-02-16
Hey everyone.

I am wanting to setup an SSL VPN so that I can access files on my server. I have heard that Adito is good for this however, there is very minimal documentation.

I basically want browser-based access to certain folders on my server without the need to install software on the client side (unless it's a browser).

Can this be done with Adito?
Cheers.

---

### Post by WeyOh on 2009-02-16
Hey,

You're question is interesting, but I'm not sure you can achieve that with VPN.

I have recently set up a VPN network at home, but what I can do is connect with my preconfigured laptop to the network. If you want to have browser access, why don't you just set up apache with openssl to have browser access? It all depends on what you want to access and from where...

Anyway, here's the howto I followed: [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

---

### Post by falconed7 on 2009-02-16
> **WeyOh said:**
> Hey,

You're question is interesting, but I'm not sure you can achieve that with VPN.

I have recently set up a VPN network at home, but what I can do is connect with my preconfigured laptop to the network. If you want to have browser access, why don't you just set up apache with openssl to have browser access? It all depends on what you want to access and from where...

Anyway, here's the howto I followed: [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

I was advised that an SSL VPN could be used to do those things. The problem is with all the options most require a program to be installed on the client PC. I would like to access my server from university/friends house.

---

