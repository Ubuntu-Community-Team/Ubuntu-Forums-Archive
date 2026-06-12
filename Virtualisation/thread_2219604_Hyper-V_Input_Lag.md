---
title: "Hyper-V Input Lag"
date: 2014-04-24
forum: Virtualisation
---

### Post by falven on 2014-04-24
Hello,
I apologize if this question has been asked in advance. I could not find an answer to my issue through search.
I just installed Ubuntu 14.04 LTS on Hyper-V as a Version 2 VM with Secure Boot Disabled.
I also made sure the integration services were installed via ```
grep | hv
```

[IMG]http://i.imgur.com/WuLbqEi.png[/IMG]

There is A LOT of input lag, nearly unusable. I gave the VM two cores (Quad Core i5 3570K @3.40ghz) and 4096MB of ram/12gb.
So it should have plenty of resources. I am guessing I just have improperly configured graphics or something. I have an NVIDIA GTX760. Also, would like to be able to change res every time I open the Hyper-V Virtual Machine Connection like I do with my Windows VM.

The performance on the vm in terms of opening programs and stuff is great, it really just is the input lag (graphics or mouse/keyboard)...
Thanks!
-Frank

---

### Post by falven on 2014-04-25
Well. Thanks for the help everyone! /sarcasm

 I found the solution(s).
 Option 1: Use XRDP and Remote Desktop to manage the Hyper-V VM rather than the Hyper-V viewer.
 Option 2: Use VMWare which has much better Linux Support, and you could even install OS-X.
 Only downside is Windows OS support is better in Hyper-V to an extent. Still not better to justify it though IMO.

 IDK what happened to these forums but they've turned into a Leech-Fest. I can't believe out of 100+ viewers there wasn't a single reply. Sad day.

---

