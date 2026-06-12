---
title: "can access samba server ok but nslookup reports wrong ip of ubuntu box"
date: 2004-12-26
forum: Server Platforms
---

### Post by insanek on 2004-12-26
i won't bore you all with the background, so heres a quick overview ...

I can connect to my ubuntu box via samba (from my xp sp2 box).
I think my xp box knows about the samba shares via udp broadcast (after lots of reading of the samba manual).


But i cannot ping the ubuntu box via its hostname (its hostname is the same as its netbiox name).
If i do an nslookup (connecting to the xp box running internet connection sharing), it oddly reports the wrong ip address... it reports 192.168.0.103... where its actual IP is 192.168.0.106....

Is there a way to force the ubuntu box to register its dns info with the dns server?

btw
I can ping other box's on the network fine via there hostnames.
Also, when doing a nslookup it reports the info fine, just the wrong ip i.e.

Non-authoritative answer:
Name:    whacktop.mshome.net     <--- right hostname/domain info
Address:  192.168.0.103                < ----- wrong IP.

---

