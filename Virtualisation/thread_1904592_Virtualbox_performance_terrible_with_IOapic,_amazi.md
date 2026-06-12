---
title: "Virtualbox performance terrible with IOapic, amazing without it"
date: 2012-01-05
forum: Virtualisation
---

### Post by azenz on 2012-01-05
Installing my Windows XP guest with my Virtualbox 4.1.8 (installed from website .deb, 64 bit version) on my Kubuntu 11.10 host took an extremely long time. Booting the virgin system on my fast SSD took minutes. After some googling I found that in previous years the IOapic feature with multiple CPUs was the culprit. So I changed the system to 1 CPU with IOapic disabled, and lone behold, the system boots in about 10 secs, and performance is lightning fast! I mean you won't believe the difference. Before, even opening "My computer" took quite a while, and now it occurs instantly. 

Since I use a quad core machine, that of course now means that only 1 cpu can be used by the guest OS. I am very disappointed about that. 

Now, this problem is not new, people on this forum have written about it since 2008. But now it's 2012!!!! Surely, such a long-standing problem that people wrote about years ago must have been addressed by now? Anybody any suggestions?

---

### Post by xyzzyman on 2012-01-07
I've found the slowdown from ioapic virtualization is way worse in XP guests than win7 and linux guests. It's always still there though. It's not really a problem the Virtualbox programmers can really "fix". As it is, most apps aren't even written to support multiple cores, so virtualizing the multiple cores has got to be a pretty intensive process in code and execution.

---

