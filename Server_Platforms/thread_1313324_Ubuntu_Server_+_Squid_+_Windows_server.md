---
title: "Ubuntu Server + Squid + Windows server ??"
date: 2009-11-03
forum: Server Platforms
---

### Post by jahservant on 2009-11-03
Basically, I want to set up an Ubuntu Server with Squid for caching.  Easy enough.

The problem comes that the default gateway is a M$ Windows SBS 2003 (which MUST be the default gateway - it is our Email Server with a static IP address).

My question is this: how can I configure the Windows server to force all computers on the network to use the Ubuntu server for caching?  I've seen examples of how to do this with other Linux servers, but never with a Windows server.

Outside of running around to each computer and manually configuring them to use the Ubuntu server for caching, I don't know how I would go about this.  Ideas, anyone?  Is it possible?

---

### Post by jahservant on 2009-11-05
*bump*

... anyone??

---

### Post by koenn on 2009-11-05
Your post is full of inaccuracies so it's pretty hard to even figure out what the question is, let alone give a relebant answer.

> 
The problem comes that the default gateway is a M$ Windows SBS 2003 (which MUST be the default gateway - it is our Email Server with a static IP address).
Having a static IP address or being a mail server is no excuse for having to be the default gateway.

> 
My question is this: how can I configure the Windows server to force all computers on the network to use the Ubuntu server for caching? I've seen examples of how to do this with other Linux servers, but never with a Windows server.
If your Windows server is an active directory domain controller, you can push this with GPO.

You can also set up PAC (Proxy Auto-Config) or WPAD (Web Proxy Automatic Discovery)


Since we're, presumably, talking about managing a Windows environment  this is really a Windows question ...

---

