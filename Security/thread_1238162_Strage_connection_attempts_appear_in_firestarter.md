---
title: "Strage connection attempts appear in firestarter"
date: 2009-08-12
forum: Security
---

### Post by reem.bs on 2009-08-12
Hey everybody
I've been noticing something that is very weird for all I know, but I might be missing something. I'm hoping you can help me.

My machine is behind two firewalls. One in the router and a local installation of firestarter.

All ports are blocked except SSH, Bittorrent and Kad. But still, when I check out my firestarter event log I see some blocked connection attempts from IPs outside of my network in various non standard ports. I have a pretty standard Netgear router and I keep its software updated.

For instance, I just received a connection attempt from some IP in the Philippines to port 35227 and it was blocked by firestarter as if it bypassed my router firewall somehow. When I try to connect to those ports from an outside machine I get blocked in my router's firewall (I don't know if there's a log in the router, so I figure that if I don't see the attempt in  firestarter's log its probably the router's doing)

Does anyone have any idea as to how these connection attempts even get to my machine?

Thanks

---

### Post by bodhi.zazen on 2009-08-12
Hard to know without more information. You will need to analyze the packets if you want this kind of information - wireshark , snort or similar.

There are many ways to get packets through a firweall and we would need to both analyze the packet and your firewall rules. do you have access to your firmware firewall rules ?

Otherwise could be anything, my guess is torrents.

---

### Post by reem.bs on 2009-08-13
Thanks bodhi.zazen
I think your guess is probably right. When I close Deluge and block its port range I stop getting these packets.
I'll need to check if I can get to my router's firmware rules, I'm not sure about it, but I will try to analyze some of these packets to see what they're about.
I still don't understand though why when my torrent client is configured to use certain ports I still get packets on other ports, and why the firewall is putting them through. Could the fact that I have a local firewall that blocks these packets interfere with my torrent downloads?

---

### Post by bodhi.zazen on 2009-08-14
That is how torrents work, share and share alike.

Most likely blocking torrents will have no effect on you, but others will not be able to upload.

Torrents are difficult as people use random ports to work around ip providers blocking torrent traffic.

---

