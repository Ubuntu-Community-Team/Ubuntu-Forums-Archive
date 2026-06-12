---
title: "Packet Bombardment"
date: 2008-09-27
forum: Security
---

### Post by StormGuy on 2008-09-27
I glanced over at Firestarter the other day and noticed that I was being bombarded with packets on port 6881.  I haven't have Bit Torrent open in weeks, so I thought is was peculiar that I was receiving random packets on that port.  I tried rebooting my computer and the router to see if the packets would stop, but as soon as I turned both back on, the packets just started hitting me again.  A new one comes every fifteen-to-thirty seconds or so.

I'm dropping the packets in IPtables and netstat confirms that I'm not listening on port 6881.  Still, the whole thing just made me a bit uneasy.  Has anybody else ever experienced this?  What could it be?

---

### Post by lovinglinux on 2008-09-27
They are probably ghost packets. This is normal, specially If your ISP gives you a static IP and you have used a torrent client a few days ago. Your IP is still listed somewhere in the p2p network, so peers are trying to connect to you.

If this is the case, then simply close port 6881 in the router and forget about it. Just open the port when you need it for torrent.

 If you don't have an static IP, then rebooting your router should renew your IP and solve the problem. If your IP is renewed but the problem doesn't stop, then you have three possible scenarios:

1 - the new IP assigned to you was being used by someone who was using p2p, so you get ghost packets from peers trying to connect to the last IP holder. THis is normal. Just close the port in the router.

2 - you could have a torrent application running on your machine without your knowledge. I'm not sure if this is possible on Linux, but uTorrent for example stays connected even after you close it.

3 - if the connection attempts are from a single IP, then it would be possible that someone is probing your open ports.

I do recommend that you close port 6881 in the router, since it is a common port for torrent and more likely to get ghost packets or port scans. If you need to use a torrent client, configure it to use a single port between 49152 and 65535 and open this port in the router whenever you want to share files.

---

