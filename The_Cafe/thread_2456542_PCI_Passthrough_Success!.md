---
title: "PCI Passthrough Success!"
date: 2021-01-13
forum: The Cafe
---

### Post by Tadaen_Sylvermane on 2021-01-13
Yesterday I found out my current cpu / mobo could support iommu. As such I achieved a goal I've wanted awhile now. How to run my Windows games easily while still being able to run Linux without dual booting. Always knew about passthrough but assumed I didn't have the hardware capable.

i5 3470, 16gb of ram, rx570 gpu, 120gb ssd with Xubuntu on it, 250gb ssd holding my kvm image.

It took a bit of fiddling about but I got it worked out and it runs beautifully. I'm waiting for a 1080p hdmi dummy plug so I can get my 1600x900 monitor and plug it back into my mobo graphics with my 1080p main. Thus far though I've been testing my Steam streaming from it > the same desktop and the performance doesn't seem to be any different than streaming to my tv on a whole other machine. solid fps, not crazy but definitely workable. Running world of warcraft just roaming around the the cities / out killing stuff the cpu never gets above 50% so it seems to have some headroom. I have not  tried running about the newest expansion. 50fps on average doing that. It's beautiful. I'm very pleased. 

Right now I'm envisioning a future system with 8 4tb spinning drives in zfs raidz2 with 64gb of ram, high core count cpu Ryzen or something along with an RX6800 for each windows instance. It would be a full windows gaming machine backed by zfs. The possibilities are endless. Suck it UNRAID.

---

### Post by grahammechanical on 2021-01-13
Are you like me mystified as to the topic of this thread?

[https://en.wikipedia.org/wiki/Input%E2%80%93output_memory_management_unit](https://en.wikipedia.org/wiki/Input%E2%80%93output_memory_management_unit)

Wikipedia didn't enlighten me much. :) But congratulations @Tadaen_Sylvermane

Regards

---

### Post by Tadaen_Sylvermane on 2021-01-13
Yes i am mystified still. I didn't figure it out myself and am clueless on how it all works. I googled. But it works and it's a simple process assuming you have the hardware.

---

