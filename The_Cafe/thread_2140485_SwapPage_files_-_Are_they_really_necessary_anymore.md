---
title: "Swap/Page files - Are they really necessary anymore?"
date: 2013-04-29
forum: The Cafe
---

### Post by u-noob-tu on 2013-04-29
These days new computers are coming with more and more RAM out of the box, and 8GB or higher is becoming common. This makes me wonder: are page files/swap areas really necessary anymore? Sure, it's possible to use all that RAM and then it would become necessary, but I can't think of many programs that can push a computer that hard. Can anyone shed some light on this subject for me?

---

### Post by zer010 on 2013-04-29
Swap space probably becomes more of an issue when editing/encoding large graphics/video files.

---

### Post by ibjsb4 on 2013-04-29
You could always see for yourself.

```
sudo swapoff -a
```

```
sudo swapon -a
```

---

### Post by codingman on 2013-04-29
err... It seems like a bigger problem with laptops, as in for hibernation. I don't make a swap anymore, cause I never use it and it takes precious time when you need to setup Arch.

---

### Post by CharlesA on 2013-04-29
> **codingman said:**
> err... It seems like a bigger problem with laptops, as in for hibernation. I don't make a swap anymore, cause I never use it and it takes precious time when you need to setup Arch.

That's probably the only reason you really need swap.

I have one on my server, but the whole 2x max RAM thing kinda gets old.

---

### Post by lykwydchykyn on 2013-04-29
Apart from hibernation, I wouldn't see any point in swap with that much RAM.  I mean, can you imagine if you were utilizing even half that much swap (4gb)?  Think of how long it takes to copy a 4 Gb file to a partition. Seems like you'd be better off not swapping at all.

---

### Post by Paqman on 2013-04-30
I still tend to keep a swap file on hand in case it's needed, but with 4GB RAM I find it's very rarely used. Tbh after installing Raring recently I haven't bothered to set the swap file up yet, I'll probably get around to it but the system works fine without it.

---

