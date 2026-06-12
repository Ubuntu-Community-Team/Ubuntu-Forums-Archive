---
title: "zonesigner &amp; dnssec-tools with different options"
date: 2016-04-02
forum: Server Platforms
---

### Post by mark277 on 2016-04-02
Hi guys,

basically i am configuring a DNS server with DNSSEC and testing different cryptographic algorithms. I am using ubuntu 14.04 with bind version 9.9.5. I installed dnssec-tools, and everytime I want to change the cryptographic algorithm I simply edit the dnssec-tools.conf, specify an algorithm such as RSASHA256 along with the KSK length and the ZSK length and save the configuration. I then run the zonesigner command to sign the specific zone, and the zone is signed successfully showing me everything went well. Please note that till now everything is fine and I managed to sign the zone using RSASHA256, RSASHA512 and RSASHA1. However, now i'm trying to sign the zone using Elliptic Curve Cryptography with the algorithm being ECDSAP256SHA256. I configure everything, as I did before from the dnssec-tools.conf file. I then type the zonesigner command to sign the zone and when I hit enter, the screen displays the words Generating Key Pair for three times and stops right there, therefore it is stuck like that. I waited for it to continue for about 15 mins but it never does, it looks like it is stuck. However when I check for the files it creates as soon as the zone is signed, I found out that the key pair files are created and so are the DS record files but the thing is that there is no file with the signed version of the zone which usually is (example.com.signed). Instead there is another file like this (example.com.zs). I've tried doing it several times but I never succeeded to get the signed version of the file. Also when I use a DNSSEC analyser to check if everything was done correctly I find that the DNSKEY RR and RRSIG RR are missing, because there is no signed file of the zone.

Has anyone got any ideas of what I might be doing wrong?

Thanks in advance.
Mark

---

### Post by howefield on 2016-04-02
Thread moved to the "*Server Platforms*" forum.

---

