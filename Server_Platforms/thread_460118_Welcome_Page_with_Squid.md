---
title: "Welcome Page with Squid"
date: 2007-05-31
forum: Server Platforms
---

### Post by Phantom784 on 2007-05-31
I'm configuring an Ubuntu machine as a network bridge/transparent proxy.  I'm re-routing all HTTP traffic to go through a squid proxy, also on the machine.  I want to configure this proxy so that, the first time someone visits any website, they will be directed to a web server on the bridge that will display a "welcome page".  After this first interception, HTTP traffic should be allowed to flow normally. Does anyone know how to configure squid to act like this.  Also, are there any online forums that would be better to ask this in?  (I couldn't find any squid-specific forums on google, but maybe I missed something.)

---

### Post by craigp84 on 2007-06-01
Hi Phantom784

Sounds like what you're looking for is a captive portal. Check out the project called nocatauth over on nocat.net

Hope this helps,

Craig

---

