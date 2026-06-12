---
title: "Setting up a filtered network through Ubuntu CE"
date: 2007-01-20
forum: Ubuntu Christian Edition
---

### Post by stooph on 2007-01-20
Hi, I'm new around here, and with ubuntu. I've updated my old linux box with ubuntu 6.10, and then found Ubuntu CE.  I would like to use Ubuntu to filter my connection, and allow windows clients to access the internet through it.  My configuration will be as follows:  
1.  Dsl modem with inter router(I've read that I don't want to have my ubuntu box directly connected to the Internet.)
2.  Eth0 network card on ubuntu box
3.  Eth1 network card on ubuntu box connected to my wireless router/switch.
4.  Few windows clients around the house.

I want the Ubuntu box to "filter" all internet connections passing through it.  Currently I have Ubuntu 6.10 and I have run the Dansguardian script. This computer is simply plugged into the back of my current router and has been handed a IP from the router.  I think I could keep the current configuration and just have my windows clients update the proxy settings in IE, but that would be to easy to circumvent.  I would rather have all traffic "flow" through the Ubuntu Box and allow DansGuardian to allow or deny pages.

I'm open to suggestions, and would like to hear what you think.
Thank You, Kevin

---

### Post by tonhou on 2007-01-21
What you are proposing is quite feasible.

The other systems must have their proxy settings set in the browser to point to the ip address of the dansguardian system and port 8080.

In Firefox:
Edit -> Preferences -> General -> Connection Settings -> Manual proxy configuration

Check manual proxy configuration and add “your DG box ip address” in first box and “8080” in second
Then tick “Use this proxy server for all protocols”

These settings can be locked, instructions are available below to do this:

Modify the file sudo gedit /usr/lib/firefox/firefox.cfg

by adding the following:

lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

Hope this is helpful.

--Tony

---

### Post by stooph on 2007-01-21
Thanks Tony, I know that's one option, but I'm using Windows Clients with IE.  I'm at the point now with it operational to work as a proxy on the network.  I think that It's too easy to circumvent the proxy on an IE client.  

What I need to figure out, is how to set up ubuntu to have dsl modem hooked directly to eth0, and use ubuntu as a router for my internal network(which is connected to eth1).

With this in place, I want DansGuardian to filter all connections passing through the Ubuntu Box/router.  Can I leave my windows clients the way they are, without running them through a proxy?

I'm not sure i'm making sense, but I'm sure that what I'm talking about is possible.
Thanks Kevin

---

### Post by stooph on 2007-01-23
Can't a client just remove the proxy info from the browser settings.  I know in IE it's easy to change.  How can I keep from a user changing these setitngs and bypassing my DG Box? Thanks, Kevin

---

### Post by stooph on 2007-01-26
I think If I configure my router to not let port 80 pass through will this work?
That way the internet will not be accessable through the router, but has to go through the dg box? Thanks, Kevin

---

