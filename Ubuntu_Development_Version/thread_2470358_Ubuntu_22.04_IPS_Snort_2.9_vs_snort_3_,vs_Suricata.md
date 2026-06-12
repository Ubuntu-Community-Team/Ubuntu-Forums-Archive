---
title: "Ubuntu 22.04 IPS Snort 2.9 vs snort 3 ,vs Suricata 5 vs Suricata 7"
date: 2021-12-27
forum: Ubuntu Development Version
---

### Post by Andrew_Welham on 2021-12-27
I'm starting to think about the upgrade to ubuntu 22.04, and which IPS (not IDS) to use. I have always used Suricata, but did not upgrade to V6 last time as there is a bug causing serious performance issues when the vm is not busy. This is hopefully going to be resolved in V7. Just in case its not i've have been looking at Snort. I always thought snort 2.x was behind Suricata, but due to the performance issues in Suricata 6 and the release of Snort 3 I'm thinking of changing my mind. This then brings me to rules. I've always used the Suricata rules plus community Emerging threats.  Following  a bit of research ,there is currently no apt package for ubuntu, anyone any idea if  V3 of snort  one will be release with ubuntu 22.04? The same applies for pulled pork 3 ? Lastly the Emerging threads rules are not yet ready for Snort 3, plus i could not find any fully functional rule converter. I'm wondering is snort 3 is just a bit too early. What's people views ?

---

### Post by slickymaster on 2021-12-27
*Thread moved to **Ubuntu Development Version**.*

---

### Post by corradoventu on 2021-12-27
on my jammy i see:
corrado@corrado-n4-jj-1211:~$ apt info snort
Package: snort
Version: 2.9.15.1-6build1
corrado@corrado-n4-jj-1211:~$ apt info suricata
Package: suricata
Version: 1:6.0.4-3

---

### Post by Andrew_Welham on 2021-12-27
Thanks, I know the current version of snort on Jammy is 2.9, just wondering if it may change before the freeze

---

