---
title: "Access Server w/ Dynamic IP?"
date: 2011-09-04
forum: Server Platforms
---

### Post by KoolAidJunkie on 2011-09-04
I recently setup my first Ubuntu Server ever because I would like to run a Teamspeak Server for me and my gaming buddies..

In Teamspeak you need a IP or URL to connect to.

How do I set Ubuntu Server to update my Dynamic IP address with zoneedit.com? So that my friends can connect to my teamspeak server with out me having to always give them the IP address when it changes?

---

### Post by 2F4U on 2011-09-04
Do you access the server from outside your home network, e.g. for the internet? If yes, dyndns may be what you are looking for:

[http://en.wikipedia.org/wiki/Dynamic_DNS](http://en.wikipedia.org/wiki/Dynamic_DNS)

---

### Post by papibe on 2011-09-04
> **2F4U said:**
> [http://en.wikipedia.org/wiki/Dynamic_DNS](http://en.wikipedia.org/wiki/Dynamic_DNS)
+1

Besides that, there are several things you need to do to make it work, and that implies understanding several concepts like static vs. dynamic IP addreses, DNS, etc. Then in your home network, static LAN IPs (or DHCP reservation), port forwarding, etc.

This is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.

---

### Post by rubylaser on 2011-09-04
To get started pointing to your server, you'll need to setup a dynamic dns client that supports[ zoneedit]("http://zoneclient.sourceforge.net/").  And create a DNS record to point at for the dynamic dns update.  Everyone's else's suggestions are spot one.

---

