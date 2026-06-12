---
title: "server virtualization"
date: 2009-05-10
forum: Virtualisation
---

### Post by ridgeb on 2009-05-10
hi all,
i have just very quickly become a fan of ubuntu which is on my laptop as the desktop version, and i am also virtualizing the server version to test it out before i install it onto my old pc i've setup as a mini server.

The problem i'm having at the moment is that the ubuntu server running as a guest on sun virtual box cannot seem to access the network and vise versa, am i doing something wrong?

It can download new packages from the internet but another machine on the network cannot ping it, i've tried manually changing to a static ip and droping the firewalls but to no joy.

Any suggestions would be a big help thanks.

and well done ubuntu, I'm practically converted from windows

---

### Post by veloce on 2009-05-11
Sounds like you set up the networking as NAT. If you want other machines on the network to see your server, the networking needs to be "bridged".

I don't know how to do that in VirtualBox but I'm sure there are instructions about if you can't see an obvious menu item.

---

