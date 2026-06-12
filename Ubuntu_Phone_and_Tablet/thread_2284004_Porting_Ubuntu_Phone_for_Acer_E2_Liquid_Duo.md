---
title: "Porting Ubuntu Phone for Acer E2 Liquid Duo"
date: 2015-06-26
forum: Ubuntu Phone and Tablet
---

### Post by lip25022 on 2015-06-26
Hey guys,

So the whole philosophy behind Ubuntu Phone is the so-called convergence. On the Mobile OS market though there are already big names such as Android or IOS, that are already widely spread all over the world. So if we want to make Ubuntu phone a success, we have to make it easy to use and install on a variety of devices, not just 2 or 3 nexus and a few pre-installed phones here and there.

Taking a look at the porting guide, it seems obvious that Ubuntu Developers want to promote porting the OS to a large number of devices.

> it is possible and encouraged to enable other devices to run the mobile OS

So here I am, not particularly knowledgeable in the mobile / android field, but wanting to tackle the port of Ubuntu Phone for Acer E2 Liquid Duo.

**Phone Specs**

[IMG]http://cdn2.gsmarena.com/vv/bigpic/Acer-Liquid-E2.jpg[/IMG]


[TABLE]
[TR]
[TD="class: ttl"]**OS**[/TD]
[TD="class: nfo"]Android OS, v4.2.1 (Jelly Bean)[/TD]
[/TR]
[TR]
[TD="class: ttl"]**Chipset**[/TD]
[TD="class: nfo"]Mediatek MT6589[/TD]
[/TR]
[TR]
[TD="class: ttl"]**CPU**
[/TD]
[TD="class: nfo"]Quad-core 1.2 GHz Cortex-A7[/TD]
[/TR]
[TR]
[TD="class: ttl"]**GPU**[/TD]
[TD="class: nfo"]PowerVR SGX544
[/TD]
[/TR]
[/TABLE]

I have read carefully [the porting guide]("https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/"), done some extra researches, installed ubuntu-sdk, ubuntu-phablet-tools and ubuntu-emulator. But I am pretty much stuck.

What's the relation between android sources and Ubuntu Phone ?

Where should I begin ?

 Is there a way to emulate my device on my Ubuntu desktop to debug my port when it's ready ?

Thanks in advance for you help :D

---

### Post by lip25022 on 2015-07-05
Anyone ?

---

