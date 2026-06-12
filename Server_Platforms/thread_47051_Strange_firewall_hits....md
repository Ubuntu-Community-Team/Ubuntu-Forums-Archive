---
title: "Strange firewall hits..."
date: 2005-07-07
forum: Server Platforms
---

### Post by spacemonkey on 2005-07-07
I've been getting some wierd firewall hits right after I boot.  It's coming from an IP I don't recognize, outside my network, on port 43668.  What's so strange about it is that I have a linksys router that acts as a firewall on top of firestarter, and the only ports that are open on my firewall are a few server daemons that point to my server machine.  No ports are forwarded to this machine, yet it's still getting hit on 43668.  UPnP is also disabled on the router, so I don't think it could be a program on my computer opening a port on the router for itself.  Any ideas what this might be, and why the heck my router isn't blocking it?

---

### Post by LordHunter317 on 2005-07-07
Post the log entries...

---

### Post by Limulus on 2005-07-08
Also, what version of firestarter?

I was having trouble with a version that was behaving similarly to what you described; it turned out it was blocking ubuntu from connecting to time servers (or rather, getting the info they were sending back; ubuntu (with sudo privileges) would send a request out, but FS would block the reply on its way back...  until I figured that out, I too was confused by my (also a linksys) router's firewall allowing things through...)

version 1.0.3-1.1~5.04ubp1 solved the problem for me; if you don't have that version (check with Synaptic), then you'll need to add those repositories to Synaptic...  I put the info to do that on here: [http://members.shaw.ca/Limulus/ubuntu.html](http://members.shaw.ca/Limulus/ubuntu.html)

Hope that helps! :-)

---

