---
title: "How do I install a nic in 10.04 server?"
date: 2010-09-06
forum: Server Platforms
---

### Post by bdemers on 2010-09-06
Trying to learn 10.04 server, just installed, no experience.  Network not working.  Ifconfig comesback with lo and virbr0 only no eth's.  I am finding no help in the documentation. Searching on network installation gives a huge listing of how to install os's from a network!  Someone have a link to what I can do to figure this out?  I know the nic is working, as I have tested it with a LiveCD 6.06LTS

Thanks.. a little frustrated, can't believe I'm getting beat up by a nic

I just reinstalled 10.04 server, this time without virtual machine support.  All kinds of network activity during the install, but when done, nothing.  Ifconfig this time only has lo, virbr0 is not there, as I would expect, but still no eth0.  I can't seem to find anything that tells me how to get the hardware to be recognized and the driver put in.  I must be missing something fundemental in my search query.

I managed to get eth0 back by removing all entries in /etc/udev/rules.d/70-persistent-net.rules.
with eth0 being seen, I checked /etc/network/interfaces and it was set up for dhcp.  I set it up for static, being sure to include a correct gateway.  I modified /etc/resolv.conf for the correct gateway.  
I did /etc/init.d/networking restart, tried a cold reboot and tried a ping of my gateway and also a known client, both on my network and both failed to return. A ping of localhost did return (well, at least I exist!)  Network card is working, the os installed files through it and a livecd can talk through it.
I returned the system to dhcp, did a restart and did not get a dhcp offer.  
So, still wondering what's going on

---

