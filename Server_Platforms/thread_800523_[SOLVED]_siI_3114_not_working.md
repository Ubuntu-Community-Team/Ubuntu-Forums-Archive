---
title: "[SOLVED] siI 3114 not working"
date: 2008-05-19
forum: Server Platforms
---

### Post by NateMan on 2008-05-19
I have a siI 3114 installed in my server. It didn't show up during installation and it shows up in lspci.

00:06.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

That's the lspci for the card. It should be supported by default in the 2.6 kernal, but it doesn't show up even though the card is functioning. Any ideas on what to do? 

Thanks Again!

---

### Post by NateMan on 2008-05-22
Turns out the problem is a bad manual, it had a bad diagram showing which ports were enabled and which weren't. Card was working all along. Glad to have that one solved...

---

