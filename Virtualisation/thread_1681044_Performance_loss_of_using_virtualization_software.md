---
title: "Performance loss of using virtualization software?"
date: 2011-02-03
forum: Virtualisation
---

### Post by gunnarflax on 2011-02-03
I'm considering either use a dual boot of ubuntu and windows 7 and using the windows 7 partition for gaming only and all my other computer use on ubuntu. But instead I could run windows 7 in virtualbox and not needing a seperate partition for the gaming (I know I can use WINE but it's not the ultimate solution). But what loss in performance can I expect from running the games in the virtual environment?

Please give an elaborate answer, e.g. pros and cons :) Thank you very much!

---

### Post by HermanAB on 2011-02-03
It depends...

A VM has only simple 2D graphics support.
The overall performance loss is in the order of 3%, if the host and other VMS are doing nothing.

So for business use, it is OK.  For gaming not.

---

### Post by Quadunit404 on 2011-02-03
If you have a hella powerful PC like Core i5 or above + at least 4GB of DDR3 RAM the performance loss on your physical machine is negligible (and it's even more negligible if you use hardware-assisted virtualization.) I haven't tried running any games in a VM running under VirtualBox or VMWare Player, but I am pretty sure that if you do so, the performance loss will be greater regardless of how powerful your PC may be. Hell, trying to get Unity and all its fancy Compiz effects smoothly under a VM is hard.

Overall it's better just to use something like Wine (or its commercial counterpart that's... basically the same except it costs money and comes with some user-friendly tools, CrossOver) or a dual-boot for gaming. Besides, no virtualization solution offers complete 3D support *yet.* You may be able to get some effects like Windows Aero in VMWare and you can play 2D games (that aren't too demanding on hardware) but overall it's best just to dual-boot or go for Wine.

---

### Post by CharlesA on 2011-02-03
> **HermanAB said:**
> It depends...

A VM has only simple 2D graphics support.
The overall performance loss is in the order of 3%, if the host and other VMS are doing nothing.

So for business use, it is OK.  For gaming not.
+1.

If you are gaming, dual boot.

> **Quadunit404 said:**
> If you have a hella powerful PC like Core i5 or above + at least 4GB of DDR3 RAM the performance loss on your physical machine is negligible (and it's even more negligible if you use hardware-assisted virtualization.)

You don't need a super powerful machine to run VMs, a dual core works perfectly fine.

---

### Post by gunnarflax on 2011-02-04
Thanks for all the replies! I guess I will have to continue windows for now then. It would be great to only use Linux someday :)

---

### Post by Quadunit404 on 2011-02-04
> **CharlesA said:**
> You don't need a super powerful machine to run VMs, a **dual core** works perfectly fine.

That's what the Core i5 is though, dual-core. It's definitely more powerful than a Core 2 Duo or Athlon 64 X2, which is why I like it.

And yeah, it'd be great to use Linux exclusively once you get used to how it works, but remember that for now you still need Windows for other things :wink:

---

### Post by CharlesA on 2011-02-05
> **Quadunit404 said:**
> That's what the Core i5 is though, dual-core. It's definitely more powerful than a Core 2 Duo or Athlon 64 X2, which is why I like it.

Ah. I thought there were i5 quad cores around, but perhaps I am mistaken. :)

---

### Post by Quadunit404 on 2011-02-05
> **CharlesA said:**
> Ah. I thought there were i5 quad cores around, but perhaps I am mistaken. :)

The Core i5 is dual-core, yeah. My computer has hyperthreading enabled in the BIOS (and I am pretty sure other Core i5-powered machines have this enabled too) and OSes see these threads as additional cores. Without hyperthreading enabled your OS would only see two cores.

---

### Post by CharlesA on 2011-02-05
> **Quadunit404 said:**
> The Core i5 is dual-core, yeah. My computer has hyperthreading enabled in the BIOS (and I am pretty sure other Core i5-powered machines have this enabled too) and OSes see these threads as additional cores. Without hyperthreading enabled your OS would only see two cores.


Looked up the specs on the intel site and it looks like there are some i5s that are running 4 cores with 4 threads, but they aren't using hyperthreading.

---

