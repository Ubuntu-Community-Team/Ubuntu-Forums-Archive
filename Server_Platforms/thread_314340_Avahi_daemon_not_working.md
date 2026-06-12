---
title: "Avahi daemon not working"
date: 2006-12-07
forum: Server Platforms
---

### Post by thecwin on 2006-12-07
I have installed the avahi-daemon onto Ubuntu Server 6.06, with an acx111 wireless card. Unfortunately, all I can seem to find with avahi-browse is the local network, similarly other computers cannot resolve it's address from the hostname.local, nor can they find it's shared services. 

I know multicasting is at least partially working, since I installed a non-avahi mt-daapd and other computers can see it'd DAAP share in iTunes. I am not using mt-daapd and avahi at the same time, as to ensure there are no conflicts.

This machine is not connected to an internet connection so has no default route, only wireless (wlan0), but I'm assuming the linux kernel is intelligent enough to work out that the default interface for outgoing multicast packets should be the only active interface with MULTICAST specified, and mt-daapd seems to be working just fine. Just incase, I added 224.0.0.0/4 to use the wlan0 interface. mt-daapd still worked and avahi still didn't. Also, ping 224.0.0.1 didn't work before I added the route, but did afterwards. 

Any ideas why this isn't working? I couldn't find anything in the logfile, and verbose mode for avahi-browse just says that there's no more in the cache. I tried tcpdump but it doesn't seem to work with wlan0...

Thanks

---

