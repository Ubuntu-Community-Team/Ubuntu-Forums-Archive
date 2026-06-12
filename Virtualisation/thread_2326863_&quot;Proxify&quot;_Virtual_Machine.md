---
title: "&quot;Proxify&quot; Virtual Machine"
date: 2016-06-05
forum: Virtualisation
---

### Post by asdfgher on 2016-06-05
Hello   I have a proxy software with socks already set and want that my VM "see" this socks.   How do I do?  Regards

---

### Post by deadflowr on 2016-06-05
*Thread moved to **Virtualisation**.*

---

### Post by MAFoElffen on 2016-06-07
Are you saying that your VM guest is running a proxy for other's to connect through?

For instance if the clients are on your host network, then the proxy should have a route to the host's networks, and one to the outside. Right?  a proxy acts as an intermediary between an endpoint device, such as a computer, and another server from which a user or client is requesting a service. More specifically, a socks 4 or 5 proxy server handles the requests from clients inside a their firewall and either allows or rejects subsequent connection requests, based on the requested Internet destination or user identification. Once the connection and bind is made, then it goes to normal http...

So yes, 2 NICs. One bridged to the host NID. The other can be NAT.

Is that what you were asking?

---

