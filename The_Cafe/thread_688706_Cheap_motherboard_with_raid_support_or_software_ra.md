---
title: "Cheap motherboard with raid support or software raid?"
date: 2008-02-05
forum: The Cafe
---

### Post by milosz.galazka on 2008-02-05
Hello,

Which one is better: use software raid or get cheap motherboard with raid support?

I want to use raid 0 with two disks at home. But I don't know how will this behave on usual cheap motherboard. Maybe there are some caveats?

Thanks for suggestions :)
Milosz

---

### Post by rfruth on 2008-02-05
Hardware is almost always faster than software so get a cheap MB with *good* RAID support.

---

### Post by x0as on 2008-02-05
A cheap motherboard isn't going to be proper hardware raid anyway, just fakeraid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Trail on 2008-02-06
I would suggest software raid.

A proper hardware Raid controller costs like 300$, so I doubt you'll ever see one. So it's either software Raid through the motherboard drivers, or through kernel. They both would use the CPU. So I'll pick kernel.

In fact, I have a bit of personal experience to share. I use 5 hdds and 2 dvd roms on my desktop; 2 hdds are sata on my two sata slots, the 2 dvds use an IDE slot and two of the hdds use the other IDE slot. My motherboard has support for Raid so it sports two more IDE slots specifically for raid. So I now use one of those slots for the other hdd.

The problem was that (about a year ago) if i used two hdds (JBOD) in the motherboard raid-ide slot, only the first would be recognised by Linux, and it would run at a horrible speed while using 100% cpu. With dma, that hdd would get a 2mb/s speed, and WITHOUT dma it would get 3mb/s (as opposed to 50-60mb/s). Some of the recent kernels must have included some sort of update on this matter, and now I get normal speeds (40+ mb/s) without full cpu usage. I do not know if a second hdd there would be recognised with this new kernel (and i can't be assed to try, if it ain't broke, don't fix it).

---

### Post by milosz.galazka on 2008-02-06
Thanks for all replies,they were very helpful :)

I didn't know about fakeraid... I used software based raid on freebsd so I will stick with it. 

Thanks!

---

