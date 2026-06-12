---
title: "Recommendations for solid-state industrial server?"
date: 2012-05-08
forum: Server Platforms
---

### Post by Jonathan L on 2012-05-08
Hello All

I have a client whose applications require a small "heat-sink brick" server with small (4 Gbyte or so) solid-state disk.  The application is industrial control, outputting about 100 1Kbyte UDP packets/sec and perhaps some serial on RS-232 or RS-485.  There will be no writing, as logs will go out to a network, nor video output, ssh only.  We could get by with one ether, but two is better.

I've been looking at these Relio 1420 from Sealevel and also M1 from Aleutia.

[http://www.sealevel.com/store/computing-hmi/industrial-computers/compact/r1420-relio-1-6ghz-intel-atom-n450-embedded-computer-2gb-ram.html](http://www.sealevel.com/store/computing-hmi/industrial-computers/compact/r1420-relio-1-6ghz-intel-atom-n450-embedded-computer-2gb-ram.html)

[http://aleutia.com/m1-fanless-mini-atom-server-with-four-lan-ports](http://aleutia.com/m1-fanless-mini-atom-server-with-four-lan-ports)

Anybody have good experience with these or similar?  Or other recommendations?

Likely to run 10.04 LTS server, controlled over custom (to-be-written) control panel in Apache, or perhaps tcl/tk or similar.

Many thanks for any suggestions.

Kind regards,
Jonathan.

---

### Post by elico on 2012-05-08
from the basic specs the relio seems like supports linux on the paper and also has better Ethernet interface then the M1.
the m1 has Realtek 8111DL that is nice but under packets load you will be surprised how much better intel Ethernet are.

---

