---
title: "Slow ping and network speed on Ubuntu Server 10.10"
date: 2011-03-24
forum: Server Platforms
---

### Post by zirtik on 2011-03-24
Hi,

I have two servers with the same exact hardware configuration running Ubuntu Server 10.10. One of them is really fast and when I ping localhost, I get an average 0.003 ms rtt. The other one is configured exactly the same but pinging localhost yields 0.012 ms average rtt.

I tried everything from changing MTU's (currently both set to 1500) to increasing or decreasing TCP window size settings. Both network cards are set to full duplex. Nothing worked and I'm starting to suspect this might be a hardware issue. However, I've already replaced the motherboard and the network card with no luck.

Pinging other computers in the same subnet results in the same performance difference. I've also tried to measure the delay writing a simple TCP client/server and observed the same problem in the slower server. These machines will only be operating on a small subnet, and small performance differences really matter.

I've been dealing with this for quite a while and can't think of anything else. Any ideas on what I might be missing? 

Thanks in advance.

---

