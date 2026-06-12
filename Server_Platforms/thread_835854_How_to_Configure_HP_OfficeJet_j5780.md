---
title: "How to Configure HP OfficeJet j5780"
date: 2008-06-20
forum: Server Platforms
---

### Post by nexist on 2008-06-20
I installed the latest Ubuntu Server distro as I wanted a file and printer server in my home. I am trying to get this thing to work with my HP OfficeJet j5780. I cannot seem to find a step by step. Evidently I need HPLIP, which is installed, but I don't know how to tell CUPS to use it and then share it on the network for other computers to use.

I tried to use the eBox interface as well, but it appears to be worthless, hence my returning to the command line.

I did a search for HPLIP and found nothing. Is there a HOWTo or step by step instruction somewhere?

---

### Post by nexist on 2008-06-20
I installed lynx and went to localhost:631. It has printed a test page. I then edited the cupsd.conf by adding a "Listen 10.11.93.2:631" and "Browsing On #changed from Off" which should make it available on the network.

---

