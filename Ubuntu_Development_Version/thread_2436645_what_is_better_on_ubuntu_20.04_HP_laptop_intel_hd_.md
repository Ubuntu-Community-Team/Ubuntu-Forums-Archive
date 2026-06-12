---
title: "what is better on ubuntu 20.04 HP laptop intel hd 630 or nvidia gtx 1050 gpu"
date: 2020-02-10
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2020-02-10
That is the gist of it.  My laptop comes with both gpu's.  I have been using Intel HD 630, but was wondering if there is any advantage to using GTX 1050 with Nvidia 440.

Henry

---

### Post by CelticWarrior on 2020-02-10
It depends on the workload.

The Intel iGPU is enough for everything but some games and professional software that can use a GPU. If the iGPU has been enough for what you're doing then you should keep using it because it saves energy comparatively. Inconveniently, if the iGPU is currently enough, I'm afraid you spent more than you should for the laptop. You could have bought one of similar characteristics without the Nvida graphics.

---

### Post by Hewjr100 on 2020-02-10
I agree Nvida was a mistake.  Next one will be all AMD.

Henry

---

### Post by ping-wu on 2020-02-11
Nvidia is a major major PITA for Linux laptops.  Intel GPU's Linux driver also has its share of problems.  Ubuntu 20.04, though still in daily builts, is a perfect fit for AMD Ryzen computers!  Both laptops and desktops.  Especially wrt the open source in-kernel amdgpu drivers. 19.10 also works great.  I chose AMD GPU, not because of its open-sourceness (shame on me!), but because of its performance and seamless/boring operations.

---

