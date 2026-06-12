---
title: "&quot;Mobile&quot; web server?"
date: 2009-05-06
forum: The Cafe
---

### Post by t0p on 2009-05-06
I'm not talking about the mobile web server that the [Nokia Research Center developed]("http://research.nokia.com/research/projects/mobile-web-server/index.html") a couple of years ago.  What I want to do is this:

At home I have to use mobile broadband to connect my computer to the internet.  Specifically, I use a 3G mobile phone to make the connection.  Now, I've got apache2 running on my computer, and I want to use DynDNS so this web server is actually accessible from the web.  Traffic wasn't getting through on port 80, so I tried using an alternate port.  But no dice - [Providing access to a mobile phone from the Internet is not straightforward, as operators typically employ firewalls that prevent access from the Internet to phones inside that firewall]("http://research.nokia.com/research/projects/mobile-web-server/index.html").

So I'm throwing this out to the combined minds of the internet... can I do this?  How?

---

### Post by t0p on 2009-05-06
Okay, it seems this should be possible... If [this]("http://wiki.opensource.nokia.com/projects/Mobile_Web_Server") and [this]("http://mymobilesite.net/") can be done, surely my little project can't be too hard...

But I haven't figured it out yet...

---

### Post by Sublime Porte on 2009-05-07
use another port number.

---

### Post by t0p on 2009-05-07
> **Sublime Porte said:**
> use another port number.

Right... 

A little tip for you: try to read what folk have actually posted before you reply.

> Traffic wasn't getting through on port 80, so I tried using an alternate port.

---

