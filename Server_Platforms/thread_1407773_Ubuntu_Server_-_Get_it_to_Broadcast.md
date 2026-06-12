---
title: "Ubuntu Server - Get it to Broadcast"
date: 2010-02-15
forum: Server Platforms
---

### Post by Niwa Awin on 2010-02-15
Okay, so I have a server that is just sitting in my room because I can't get it to broadcast to the general public (I can see what's on my server as long as the computer is connected to my network).  I've done port forwarding and trying IP passthroughs, yet nothing works.  I'm out of ideas, thus I need help.  My modem is a Netopia 3347-02.

---

### Post by ikehack on 2010-02-15
You might want to try placing your server the DMZ of your network. If you're not too sure what a DMZ is, take a look at [this link]("http://en.wikipedia.org/wiki/DMZ_(computing)"). From the logical standpoint it does make sense to do port forwarding for the services on your server but a DMZ makes more sense from the security standpoint. Simply put, a DMZ is used to put servers that run specific services, like an HTTP server, so it's accessible from the outside world without posing a threat to your internal network. Still, read that Wiki regarding DMZ's.

Since most DSL, Cable, and FiOS customers are given a new IP address every day or every other day, through the process of [DHCP]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol"), it may be a burden to remember a new IP address that will be attached to the server placed in your DMZ. It would behoove you to attach it to a domain name. From a service such as [DynDNS]("http://www.dyndns.com/"), you can have your server contact DynDNS's "home base" so to speak, and update your IP address given to you by your ISP automatically and attach it to your free domain name. Which means each time you want to access your webs erver at home, you can simply type in subdomain.domain.com, where x is a DynDNS owned domain.

I hope this helps!

---

