---
title: "Setting Ubuntu Server up as router for VMWare host-only network"
date: 2006-09-25
forum: Server Platforms
---

### Post by dshuck on 2006-09-25
I am somewhat new to Ubuntu and Linux as a whole, but have been playing with it long enough to occasionally hurt myself.  I have an Ubuntu Server running VMWare Server.  I am setting up some of my appliances and am having trouble getting my head around the right way to approach making my host-only network available to exteral hosts by setting up routes on my Ubuntu Server host.

For instance, if my host-only network is a 10.0.0.x range, I am guessing that I should be able to assign a public IP address to my eth0, then route to a specific virtual machine with a 10.0.0.x address.

Does anyone know of some semi-n00b friendly examples or documents on making this work?

Thanks in advance...

---

### Post by Child of Wonder on 2006-09-25
You're going to need to set up NAT and port forwarding with iptables.

I'm at work otherwise I'd Google it for you.  There should be a few good guides out there.

---

