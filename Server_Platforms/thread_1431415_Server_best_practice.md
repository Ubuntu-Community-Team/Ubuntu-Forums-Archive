---
title: "Server best practice?"
date: 2010-03-16
forum: Server Platforms
---

### Post by nmccrina on 2010-03-16
I'm just starting out on my way to being an [awesome sysadmin]("http://xkcd.com/705/"). I installed a server in Virtualbox, and I noticed that it was not necessary to be logged in in order to serve web pages; that is, I could boot the server and leave it at the login prompt and still be able to get to the site. It's kind of a "duh!" thing I guess, because obviously the apache daemon has started, but it seems weird compared to normal desktop practice. Is this how "real" servers are left? Are they only logged into when something needs to be changed?

Sorry for my n00bosity :P

---

### Post by wojox on 2010-03-16
So you actually did log in. Through ssh? My server sits beside my desktop tower. No keyboard attached to it or monitor. So yes that sounds about normal.

Love the cartoon. :D

---

### Post by KB1JWQ on 2010-03-16
This is correct.  I've got a farm of a few hundred servers, and the way they work is you can pull the power plug, plug it back in, boot it, and you're done.  Having to go through all 300 or so boxes and log into them all would be horrible.

In fact, it's a security loophole to leave a box logged in; anyone who walked by could theoretically gain access.  

Any other questions on this topic?  I can talk for hours about this stuff. :-)

---

### Post by nmccrina on 2010-03-16
> **KB1JWQ said:**
> This is correct.  I've got a farm of a few hundred servers, and the way they work is you can pull the power plug, plug it back in, boot it, and you're done.  Having to go through all 300 or so boxes and log into them all would be horrible.

In fact, it's a security loophole to leave a box logged in; anyone who walked by could theoretically gain access.  

Any other questions on this topic?  I can talk for hours about this stuff. :-)

I have tons of questions, lol. I don't even know where to begin! Right now I'm racing through "DNS and BIND" so I can set up a nameserver so I can register a domain name. :) Would you recommend that, or something like MaraDNS? (My Web Tech professor said he used MaraDNS).

Edit: Oh, and I just reread wojox's post. Can you connect to a server inside a virtual machine from the host OS through ssh? I have a Windows 7 host and a Ubuntu Server guest.

---

### Post by KB1JWQ on 2010-03-16
Yes, you can log into a virtual machine; just make sure you've set networking on the host to bridge mode; NAT adds a layer of complexity that you'd be better off not dealing with.

I'd be hard pressed to advise anything other than BIND; its the gold standard of DNS servers, and it's one of the fundamental *nix tools that almost everyone understands / speaks to varying degrees.

You can do a LOT with it, but setting it up to do most minor stuff shouldn't be too difficult.

---

