---
title: "Dynamic routing for redundant Internet links"
date: 2010-01-14
forum: Server Platforms
---

### Post by NIT006.5 on 2010-01-14
Hi,

Have searched for other posts on this topic but haven't found anything that helps much. As far as I can tell, the server guides only explain a bit about what dynamic routing is, but not how to implement it.

My situation is this:

We require a server with 3 interfaces. One local, one to a vsat link and the other to a fibre link. The fibre will be the default route for Internet traffic but we want dynamic routing to automatically switch to the vsat link when the fibre link goes down (which happens fairly often in Zimbabwe!) and then switch back to the fibre link when it comes back up again. 

The first option would be to handle dynamic routing on a Cisco router, but at the prices of Cisco devices here, it's not the most affordable option.

Can anyone point me in the right direction to implement this on Ubuntu server?

Many thanks.

---

### Post by neoanderthal on 2010-01-14
I *think* vrrpd will work for you, but I'm not positive.

[http://manpages.ubuntu.com/manpages/hardy/man8/vrrpd.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/vrrpd.8.html)

---

### Post by NIT006.5 on 2010-01-14
Thanks for the response. I wasn't aware of this and it's useful to know, but this seems to be more for router redundancy (not link redundancy) and would involve having two servers/routers if I understand it correctly, rather than dynamic routing on one server.

The only other thing I've found is quagga which I'm downloading now and will test out.

---

### Post by BkkBonanza on 2010-01-14
This seems like the kind of thing monit could handle easily. 

Or even simpler, a small script daemon could monitor the links and alter the routing table depending on link responses. Start the script with an upstart config using the respawn option. This way if it gets clobbered it will be automatically started again.

---

