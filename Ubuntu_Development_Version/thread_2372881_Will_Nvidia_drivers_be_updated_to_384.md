---
title: "Will Nvidia drivers be updated to 384 ?"
date: 2017-09-29
forum: Ubuntu Development Version
---

### Post by fthx on 2017-09-29
Hi,

We are running 375 now but 384 is the new LTS driver. Will it be updated ?

Thanks !

---

### Post by Bashing-om on 2017-09-29
fthx; Hummm ..

Running 16.04.3 ? I would not expect to see 384 in the repository . The aim is stability. if the 384 version driver is needed there is our trusted PPA that contains the latest drivers .
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) <- Fresh drivers from upstream, currently shipping Nvidia.

But, if it ain't broke, do not fix it.

[INDENT]hope this helps
[/INDENT]

---

### Post by cariboo on 2017-09-29
The driver you are looking for is in the Proprietary GPU Driver PPA located here:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by fthx on 2017-09-29
I'm running 17.10 and I know (and was running) 384 from ppa.
But it does not answer my question. ;-)

---

### Post by mc4man on 2017-09-29
I would think it may. Ubuntu lts releases certainly do (16.04 got 361 > 367 > 375
As far as the 9 month releases for ex. zesty did (367 > 375
So wouldn't be unexpected if 17.10 did get one newer.

---

### Post by fthx on 2017-09-30
That's what I think too, but even if graphics/languages updates are often close to the release, I feel we are very close to the end ?

Talking about Nvidia, could you tell me if it's normal ? :
- when I use Nvidia proprietary, I can only choose a X session (but I can use Wayland if I select Intel mode in prime) ;
- when I use Nouveau, I can only choose a X session.

---

### Post by mc4man on 2017-09-30
> **fthx said:**
> That's what I think too, but even if graphics/languages updates are often close to the release, I feel we are very close to the end ?

Talking about Nvidia, could you tell me if it's normal ? :
- when I use Nvidia proprietary, I can only choose a X session (but I can use Wayland if I select Intel mode in prime) ;
- when I use Nouveau, I can only choose a X session.
Currently there is no support for using hybrid (optimus) devices in a wayland session, users with a desktop Gpu should be able to get/use a wayland session

---

### Post by fthx on 2017-10-01
Well...
I do use a Dell Precision laptop with Nvidia Quadro M1000M optimus, Artful up to date.

[B]Nvidia proprietary 375, switchable graphics enabled in BIOS

[/B]No noticeable bugs, only X session

[B]Nvidia proprietary 375, switchable graphics disabled in BIOS (Nvidia on, Intel off)

[/B]No access to brightness keys, only X session

[B]Nouveau, switchable graphics enabled in BIOS

[/B]No noticeable bugs, poor performance, only X session

**Nouveau, switchable graphics disabled in BIOS**[B][B] (Nvidia on, Intel off)
[/B]
[/B]Very buggy : no access to brightness keys, dead black screen when I connected a second display, X or Wayland session

---

### Post by fthx on 2017-10-04
Well done, closed :
[https://lists.ubuntu.com/archives/artful-changes/2017-October/011550.html](https://lists.ubuntu.com/archives/artful-changes/2017-October/011550.html)

---

### Post by mc4man on 2017-10-04
> **fthx said:**
> Well done, closed :
[https://lists.ubuntu.com/archives/artful-changes/2017-October/011550.html](https://lists.ubuntu.com/archives/artful-changes/2017-October/011550.html)
It's in proposed as you've seen though there could be an issue with the proposed gcc  or something that breaks nvidia- install  so I wouldn't blatantly use -proposed to get
(- the ppa is much safer atm

---

