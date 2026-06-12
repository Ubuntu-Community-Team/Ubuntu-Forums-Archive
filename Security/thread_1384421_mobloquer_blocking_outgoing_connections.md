---
title: "mobloquer blocking outgoing connections?"
date: 2010-01-18
forum: Security
---

### Post by deankovell on 2010-01-18
Mobloquer starts up at boot and before I've even opened firefox or transmission or anything, mobloquer shows that is has started blocking several outgoing connections as well as ton of incoming connections. I was wondering if the outgoing connections is normal and what's a normal amount of network activity to show up in system monitor when I'm not actively using the internet.

---

### Post by lovinglinux on 2010-01-18
The outgoing connections may be several things like connections on the loopback device, the clock trying to contact the update server or even the Update manager trying to check for new updates. It is hard to tell without the port an IP blocked.

I don't get any blocked address when I log in. But I have several addresses allowed. For instance, I have allowed these in /etc/blockcontrol/blockcontrol.conf

```
WHITE_TCP_OUT="http https"
```

Additionally, I have allowed several outgoing connections in the allow.p2p list (in fact I use a separate allow list for outgoing):

Localhost:127.0.0.1-127.0.0.1
IANA Multicast:224.0.0.22-224.0.0.22
IANA Multicast:239.255.255.250-239.255.255.250

Plus my router IP and my DNS servers.

So, it depends on your moblock configuration, but also which blocking lists you are using.

The incoming connections are probably ghost packages, since there will still be some remote users trying to connect to your transmission, even after you close it down. This happens because their clients do not have scraped the tracker since you close Transmission, so they still have your address listed in the swarm. You could avoid this by renewing your IP or simply using UPnP to make sure the port is closed after the client is terminated. I'm not sure how good is Transmission UPnP feature, but in Ktorrent you can even close the port "manually" through the UPnP plugin. This is what I do after stopping all torrents and the connections stops immediately and moblock's log stops showing a bunch of blocked connections.

---

### Post by deankovell on 2010-01-18
Thanks lovinglinux,
   I think I understand now. UPnP was enabled in Transmission, but it has a shutdown routine where it gives the option to just quit instead. I let it finish its routine for a change and the outgoing blocks all stopped except for one repeating address (224.0.0.251) which turned out to be something avahi was doing. 
   It just made me a little nervous that there were outgoing connections that were there at all when I wasn't trying to create them. Thanks again for your time.

---

