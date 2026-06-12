---
title: "Squid and Shorewall - no more proxy"
date: 2006-11-09
forum: Server Platforms
---

### Post by davebgimp on 2006-11-09
I've been running squid on a remote server and using ssh to tunnel it.

Basically I open an ssh session like so:

**ssh -L 3128:127.0.0.1:3128 [email]daveb@xx.xxx.xxx.xxx[/email]**

....and then while that's open, I set my browser to localhost, port 3128. 

It works great. However...

I recently installed shorewall on the server. With the firewall running on the remote server, I cannot view web pages in the above method. I've got SSH allowed, but obviously I need to do something with 3128 to make it accessible, but I can't seem to figure it out.

Has anyone used this proxy method before and gotten it to work with shorewall? In the general sense, i know what needs to happen, but I'm very new with firewalls and shorewall in general.

If not, can anyone recommend another way to do this?

---

### Post by davebgimp on 2006-11-14
Looks like when I first configured Shorewall, I was a little more restrictive than I needed to be, retricting both in and out traffic. Following [this]("http://www.shorewall.net/standalone.htm") howto, I was up and running with a permissive *out* and restricted *in* setup in under 10 minutes. Seems like Squid and everything else I had trouble with is working great now. :)

---

