---
title: "Warning Light on Server?"
date: 2009-09-13
forum: Server Platforms
---

### Post by slibuntu on 2009-09-13
Hi, 

I know this isn't a specifically ubuntu related question, but I reckon you guys may be able to answer it. One of my servers has it's warning light flashing, it appears to be working fine otherwise. What are some possible reasons why the warning light may be flashing on a server? As is usual with these things, the manual is nowhere to be found..

---

### Post by jondkent on 2009-09-13
Hi,

Not knowing what the server is, my experience has been that these can be:

failed disk
battery charge low for RAID
memory errors
backup power supply failure/fault

and so on..

there must be something the manufacture's web site, esp if its HP or Dell.

---

### Post by PilotJLR on 2009-09-13
Does your server have a management card? With HP, it's called iLO. With IBM, it's called RSA.

You would have to address the card, then login to its web interface, and it will tell you what the fault is.

Of course, also find the server's manual online.

---

### Post by tgalati4 on 2009-09-13
Probably a slow fan.  Time to clean it out.

---

### Post by windependence on 2009-09-14
I agree  with PilotLJR and I'll add that some IBM servers have LED diagnostics on the case of the server with an overlay to explain what the lights are. I'm thinking it's not any of the easy ones because he said he can't find the manual and with HP and IBM, or even Dell, they're pretty easy to find online.

Give us the make and model number and we can help you.

-Tim

---

### Post by scorp123 on 2009-09-14
> **slibuntu said:**
>  One of my servers has it's warning light flashing, it appears to be working fine otherwise. What are some possible reasons why the warning light may be flashing on a server? Sorry, but my crystal ball is out for repairs and I suck at Tarot ... So unforunately this means you will have to tell us the make / brand / model of that server. :D

---

### Post by tubezninja on 2009-09-14
We definitely need to know what make and model of the server is to tell you how to diagnose the problem.

For what it's worth: I once admin'd a batch of Dell rackmount servers that were sold with Windows pre-installed.  Apparently there was a Windows diagnostics driver that the motherboard expected to see running, and if not, it would trigger and amber flashing warning light.  So if we isntalled linux on them, well... :)

---

### Post by windependence on 2009-09-14
Most servers have an admin partition independent of the OS. You load the partition before the OS and it works with any OS you install. You can, of course install without the admin partition, but it's nice to have the monitoring tools, usually free.

-Tim

---

### Post by jondkent on 2009-09-15
Or course it would be nice to know if any of the above suggestions have been of use to the thread owner, or if this issue is still on-going.  They seem very quite :confused:

---

