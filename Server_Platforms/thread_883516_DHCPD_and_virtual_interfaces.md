---
title: "DHCPD and virtual interfaces"
date: 2008-08-08
forum: Server Platforms
---

### Post by idefixgallier on 2008-08-08
Hi!

I am using a dhcpd server for some years now without any
problems.

Now I have the task to set up a virtual interface (eth0:1, 10.0.0.4/16) to an
existing physical interface (eth0, 10.0.0.1/16).

Running the virtual interface causes the dhcp server to listen on 10.0.0.4 (it is configured to listen to eth0) but answeres on 10.0.0.1.
That prevents every client to get an ip address (although it is the same subnet !?!)

Can somebody explain that - or better - does someone have a solution vor that?

lg
Martin

---

### Post by StickyStyle on 2008-08-08
Maybe explain what your trying to accomplish with having dhcpd on the subinterface.  Both of those interfaces are on the same network, so what you have described doesn't quite make sense.

---

### Post by idefixgallier on 2008-08-08
Hi, 

yes it sounds a little bit weired ....

So what I want to do is that:

I want to establish heartbeat with 2 nodes.
The heartbeat daemon works with a virtual interface that
is moved to the fallback server in case of troubles.

In that is my problem, if I set up a virtual IP on an
exisiting physical interface, dhcpd does not answere 
requests correctly - altough it does according to the logs, but
tcpdump shows that it listens to 10.0.0.4 (the physical interface)
and answeres via 10.0.0.1 (the virtual interface).
Then no client gets its IP (although I dont understand it because, 
as i said, both interfaces are on the same network)

I hope my poor english explains the situation a little bit ...

lg
Martin

---

### Post by windependence on 2008-08-08
I could be wrong but I believe to set up heartbeat you need to set up static IPs. At any rate, that would solve your problem.

-Tim

---

### Post by idefixgallier on 2008-08-08
The daemon itself needs for his checks the static ip's thats correct.
But the virtual server it provides has a virtual ip that could be switched from one node to the other

lg

---

