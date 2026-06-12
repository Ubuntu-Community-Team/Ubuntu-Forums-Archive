---
title: "Why is ATA over Ethernet so slow?"
date: 2011-08-01
forum: Server Platforms
---

### Post by bakegoodz on 2011-08-01
I have been playing with AOE for a while. I got sold on it from some Coraid materials saying how it so much better because it just used low level Ethernet. I was just using it for my home LAN, just sharing out a single drive. Stuff that normal geeks would use a simple file share or NAS for. I usually push many GB to this drive at one time so if I don't get as much speed as possible I get irritated. I was only getting between 10 to 20 MB/s transfers over a Gigabit network and between drives that should do at lest 80 MB/s. The AOE Target's processor wasn't being used over 40% with these transfers. After searching around for answer to my slowness problem, I found a forum post from one that said iSCSI was faster. So I tried iSCSI with the same hardware and I got about 50 MB/s transfers. Even though iSCSI was harder to setup I was sold. I decided to give AOE another chance after reading about the benefits of Jumbo frames. So I set my computers to 7000 MTU size (supposed to Realtek's max) and my Procurve switch (not currently doing any VLANs or fancy stuff) to Jumbo frames. And tried AOE once more, now it was doing 15 to 30 MB/s. I compiled Coraid's latest source and tired the latest version, but there was no difference in speed. So I restored my iSCSI config. Now I get 55 tot 65 MB/s transfers with iSCSI and it's CPU utilization is about half of AOE's too, so I'm pretty happy. I liked AOE's simplicity, but it's too slow. What's the deal? Is there iSCSI is inferier because of TCP/IP overhead argument a bunch of BS? Or is there something unique about my hardware that influences this Outcome?

---

