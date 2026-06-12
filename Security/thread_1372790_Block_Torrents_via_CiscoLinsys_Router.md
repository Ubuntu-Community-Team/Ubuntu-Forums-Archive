---
title: "Block Torrents via Cisco/Linsys Router"
date: 2010-01-04
forum: Security
---

### Post by running_rabbit07 on 2010-01-04
I have a roommate moving in that is known for rampant torrents. In my "access restrictions" settings on the router I am able to set rules for each host that is issued an IP and I set each IP by MAC address(meaning each host gets a reserved IP). What would be the most likely application and port numbers to block to prevent these activities?

Thanks.

---

### Post by wirelessmonkey on 2010-01-05
The most common defaults for bittorrent are 6881-6889, but most torrent clients will let you select either a random port, or manually set the port. You'll probably need to set both tcp and udp filters, if you do this.
If your router allows you to do QoS, you may be able to throttle his torrents down to near nothing, but it depends on what your router can do.

---

### Post by running_rabbit07 on 2010-01-05
That's great info. She hasn't set up her system yet, but when she does I will start playing with the QoS settings. 

Thanks.

---

### Post by kiranmurari on 2010-01-05
[SIZE=2]You can run bit torrent on any port that you like. Like MSN messenger it will default to port 80 to download stuff if it can't access the internet on any port. This means that it is not an application that can be stopped by denying certain ports you need something that is more intelligent. The only way to stop it is with a proxy server. Turn off NAT (for everyone else but yourself) and use a Proxy to provide Internet access.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]But still you can give a try on blocking the torrent ports. Assuming the client used is Bittorrent. Prior to version 3.2, BitTorrent by default uses ports in the range of 6881-6889. As of 3.2 and later, the range has been extended to 6881-6999. Torrent is a TCP connection oriented protocol, NOT a UDP.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]Also you can use "Website Blocking by Keyword" feature. Add the keyword **torrent** to block all URLs containing the keyword torrent.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]Hope this helps.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]Regards,
Kiran[/SIZE]

---

### Post by bodhi.zazen on 2010-01-05
Torrents can be difficult to block. You could try opendns :

[http://www.geckoandfly.com/2009/12/07/barracuda-hardware-web-filter-alternative-block-p2p-torrent-traffic-and-port/](http://www.geckoandfly.com/2009/12/07/barracuda-hardware-web-filter-alternative-block-p2p-torrent-traffic-and-port/)

If that fails, the next step might be to configure a hardware router and use something such as ipcop.

---

### Post by iponeverything on 2010-01-05
Another way to very effectively throttle, but not totally kill, bitorrent is by restricting the number of outgoing connections the host with assigned IP is allowed to initiate. If you make it something like 150, its unlikely to affect anything else that they are doing, but it cause bitorrent to top out at about 40 or 50k.

The way that is able to suck down so much bandwidth is by opening a very large number of connections, each only moving a trickle of data, but collectively can saturate a pipe.

This is doable, and can be implemented on a transparent in-line bridge.

Another solution drop a machine in line and have it use tc to create bandwidth pools to limit the effective bandwidth available to certain hosts. See:

[http://ubuntuforums.org/showthread.php?t=946624](http://ubuntuforums.org/showthread.php?t=946624)

---

### Post by wirelessmonkey on 2010-01-05
Torrents themselves don't use udp, but peer sharing and tracker connections often do.

---

### Post by running_rabbit07 on 2010-01-05
Lots of great ideas. "Thank you," everyone. 

The girl has no clue on most of this stuff to get by the simplest of blockage. I will probably go with some of my own filtering within the router along with the OpenDNS to alleviate her from torrenting things that aren't open source products.

---

