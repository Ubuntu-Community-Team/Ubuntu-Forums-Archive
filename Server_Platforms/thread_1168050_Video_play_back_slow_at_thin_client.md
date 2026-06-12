---
title: "Video play back slow at thin client"
date: 2009-05-23
forum: Server Platforms
---

### Post by DrTT on 2009-05-23
Hi,

I have made a little homeserver (edububtu, ltsp) with 3 thin clients fot my children. I noticed that when my children will play back video or look at youtube the video is a little bit shacky. As it has not enough frames per second. The sound is perfect. I try to figure out what the bottleneck is but I don't have a clue.

Details:
"server": AMD athlon 2600+ with 1gb memory, 2 networkcards 100/10 and a 5 port switch
Thin clients: Wyse, Via 550 MHz 512 Mb, no harddisk

When I look at youtube at the server, the video is perfect. When I look at "top" or systemmonitor I see that the CPU% is about 80%, not 100%. 

Another strange thing:
When I look at iTalc I see all the thin clients twice. Why???
This is what I see:
Pu Yan (puyan) @ Edubuntuserver [192.168.1.144:10020]
Pu Yan (puyan) @ Edubuntuserver [192.168.0.254:10020]
Ying Xiu (yingxiu) @ Edubuntuserver {192.1.144:10021]
Ying Xiu (yingxiu) @ Edubuntuserver {192.0.254:10021]

Can somebody explain this?

Theo

---

