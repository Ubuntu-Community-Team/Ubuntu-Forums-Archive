---
title: "Does port forwarding for Torrent compromise security ?"
date: 2013-12-05
forum: Security
---

### Post by linuxyogi on 2013-12-05
Hi,  I have opened a port in gufw & my router's firewall for the torrent client.   So technically there is an open port.  Can someone using this port access files on my PC ?

---

### Post by CharlesA on 2013-12-05
The only files they could access are ones you are seeding.

With that said, I didn't have any problems running torrents without opening any ports. I was using Transmission, though.

---

### Post by linuxyogi on 2013-12-05
> **CharlesA said:**
> The only files they could access are ones you are seeding.  With that said, I didn't have any problems running torrents without opening any ports. I was using Transmission, though.  I use Transmission too and I also used to use it with all ports closed. Then I was a bit curious about why people open ports so I created a thread  [https://ubuntuforums.org/showthread.php?t=1793936&highlight=torrent](https://ubuntuforums.org/showthread.php?t=1793936&highlight=torrent)  But to be frank I don't see much of a speed boost but thats may be because my broadband speed is 1 Mbps.

---

### Post by CharlesA on 2013-12-05
Ah gotcha. I didn't really see a speed increase either, but my pipe is only 15Mbps down and 2Mbps up.

---

### Post by papibe on 2013-12-05
> **linuxyogi said:**
> So technically there is an open port.  Can someone using this port access files on my PC ?
Extremely unlikely.

From the Bittorrent site:
> Unless there is a known, fully-remote exploit for the current version of BitTorrent that would break your computer's security setup, there is no risk in opening a port on your firewall for BitTorrent.
Since the torrent protocol has been around long enough, and that most Linux's clients are open source, this would not be very likely to happen.

In the case a vulnerability or an exploit was discovered, it would make the news.

Just my thoughts.
Regards.

P.S.: port forwarding only affect the uploading connections, i.e., your 'sharing' part. Sometimes that is taking care for you if either NAT PMP, UPnP, or a DMZ is set.

---

