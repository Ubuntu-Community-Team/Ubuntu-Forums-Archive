---
title: "Apache not serving lan with Linksys router"
date: 2009-08-07
forum: Server Platforms
---

### Post by alleycatuk on 2009-08-07
Hi,
I've set up a LAMP test machine which is working fine - I've set up a few VirtualHosts and can access them on the Apache server PC by using their domain names. So far so good!

I'd like to access the server from another PC on the LAN but it just isn't working - even if I type the ip address of the server into the browser on the other PC. (I've also set up the hosts file but if the IP address doesn't work, the hosts won't either!)

Both PCs are on a wireless network served by a Linksys WRT54G router. The pcs can ping each other quite happily - the server just won't serve a page to the other one. Do I need port forwarding set up on the router or something? I don't want the PCs exposed to/accessible from the internet so am a bit nervous about trying anything!

Any help would be fantastic.

Thanks

I solved it! Even though I could ping, firestarter was blocking port 80 - just set up a rule and it's ok now!

---

