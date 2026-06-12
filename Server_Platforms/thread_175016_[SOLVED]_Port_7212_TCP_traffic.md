---
title: "[SOLVED] Port 7212 TCP traffic"
date: 2006-05-12
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-05-12
Is anyone else getting this on their firewall?
It seems like this is happening a lot lately.

I just changed my network hardware setup and I've gotten 7 hits on that port in less than 6 minutes, incoming.

No security sweeps report anything unusual or out of place.

(This is insane. . .over 24 hits in 5 minutes, and ports 1025-1027 were the dominant traffic before what with messenger spam and all.)

(EDIT #2: Just did a quick check with Snort, and these hits are coming from source ports in mostly the 1000 to 4000 range, but sometimes over 33000. They all say "TCP Options (6)" next to themselves.)

---

