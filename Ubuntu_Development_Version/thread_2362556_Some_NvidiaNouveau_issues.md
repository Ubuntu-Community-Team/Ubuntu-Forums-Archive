---
title: "Some Nvidia/Nouveau issues"
date: 2017-05-30
forum: Ubuntu Development Version
---

### Post by fthx on 2017-05-30
Hi, 

I experience the following issues (Nvidia 375.66, Quadro M1000M, Skylake) :

- with Nvidia-only mode (to avoid tearing), proprietary and Intel GPU disabled, I cannot reach the max level of backlight ; at startup it is ok but if I change the brightness level, it never reaches this max level again, by far. Am I the only one to see that bug ?

- when I use Nouveau instead of Nvidia proprietary, I can launch apps with Nvidia GPU by right-clicking on them. When I launch Talos Principle with Nouveau (kernel 4.10 or 4.11), I reach a very low FPS level, lower than Intel GPU. Is it an usual behaviour or not ? With Nvidia proprietary I get 15 times more FPS than Nouveau... In some other 3D tests I see the same thing.

---

