---
title: "pass aptituide through another server?"
date: 2009-06-17
forum: Server Platforms
---

### Post by sherl0k on 2009-06-17
I have 10 Ubuntu servers connected in a local LAN. They all have two NICs, one going to a switch that connects all these servers together, and another NIC that connects to a switch that connects to client computers. Only one of them has a second NIC, that connects out to the public internet instead of a switch with clients. How would I go about updating the other 9 servers in the LAN, using the 10th server with its public internet access? I was considering installing a proxy server on it and setting all the other servers to use it, but I'm afraid that it might mess with other networking settings on those computers - mainly, the client computers. The NIC that connects to that switch also hands out IPs over DHCP, and I don't want the clients to also have access to the proxy settings. The other option is running an aptitude mirror, but that is resource intensive.

Is there any other option available to me or are these the two I'm limited to?

---

### Post by grantemsley on 2009-06-17
You are limited to those two options.  I suppose you could do some sort of complicated script where the internet connected one downloads the debs and transfers them to each other computer, but that would be a lot more work than just running a mirror.

The servers either need to be able to access the internet (via a second nic, routing through the internet connected server, or a proxy on the internet connected server), or you need a local mirror.

Personally, I'd recommend the local mirror, as it means not having to change your network settings, and will save a ton of bandwidth when doing updates.

---

### Post by sherl0k on 2009-06-17
Yeah, I think that's the route I'm going to take. I'll have to see how big having a mirror will require, and set aside a box for just that. Thanks.

---

### Post by cariboo on 2009-06-17
Have a look at apt-cacher, it is designed to do exactly what you want. Apt-cacher is in the repositories.

---

