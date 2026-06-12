---
title: "ISP vs. VPN"
date: 2022-11-14
forum: The Cafe
---

### Post by Shibblet on 2022-11-14
I heard a rumor that ISP's specifically target VPN traffic and slow it down.  Anyone else heard of this?

---

### Post by TheFu on 2022-11-15
> **Shibblet said:**
> I heard a rumor that ISP's specifically target VPN traffic and slow it down.  Anyone else heard of this?

ISPs slow down any bulk traffic, since bandwidth is always limited during peak periods of use, regardless of what the fanbois on the internet claim.  

Smaller requests are going to always be handled faster, since it makes the most people happiest.  An HTTP GET that is less than 1 full packet **should** be handled before 20M packets for bulk transfers like video streaming.  Also, now that lots of ISPs are in the phone business too, those packets have reserved channels for use ... but the telecom industry knows how to oversubscribe data offers for phone calls. They've been doing it for over 100 yrs.

When it comes to VPNs being slow, there is definitely overhead in the encryption/decryption process.  I see that on my own LAN.  Encrypted traffic using TLS and openVPN runs about 75% slower than unencrypted traffic.  No ISP in the way.  Wireguard VPN is more efficient and runs around 40% slower than unencrypted traffic.  As you can see, there is definitely overhead ... and that's before adding in all the hops that internet traffic goes through. VPN servers can make the number of network nodes used 2-3x longer, also slowing down total thoughput.

Who to blame isn't 1 answer. There are multiple things causing VPNs to be slower and most of that slowdown is just the technology, not any malicious action.  Of course, some websites really dislike VPN users, since it hides the location for where the user really is.  This can be a legal issue for some services, as they only have the rights to provide some content for specific regions, usually split by political boundaries. Some actively block VPNs, of that I'm positive.

---

