---
title: "Higher idle power consumption after removing cloud-init"
date: 2021-01-17
forum: Server Platforms
---

### Post by tecfreak2 on 2021-01-17
Hello,

after removing the cloud-init package from my 20.04.1 Ubuntu Server installation I have noticed a higher power consumption in idle.

My hardware is as follows:

Biostar J3060NH
Crucial BX500 120GB SATA SSD
2x 2GB DDR3L-1600
PicoPSU-80 + APD DA30E12 12V 2.5A

With the cloud-init package installed the idle power consumption is around 4.6-4.8 watts. Removing the cloud-init package results in a power consumption of 6.1 watts.
I know this isn't much, but why this difference at all?

I could reproduce this behavior several times installing, removing cloud-init and rebooting the system with exact the same results every single time.

Any ideas?

---

### Post by LHammonds on 2021-01-17
Do you get the same behavior if you use the [legacy installer](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/) which does not include cloud-init?

LHammonds

---

### Post by tecfreak2 on 2021-01-17
After a fresh installation I am getting exactly the same results. Higher power consumption and just after installing cloud-init and rebooting the idle power consumption goes down again.

---

### Post by LHammonds on 2021-01-18
So higher power consumption with legacy installer (which does not include cloud-init) and then manually installing cloud-init lowers the consumption?

I am curious now what cloud-init does regarding power.

LHammonds

---

### Post by tecfreak2 on 2021-01-18
> **LHammonds said:**
> So higher power consumption with legacy installer (which does not include cloud-init) and then manually installing cloud-init lowers the consumption?

Exactly.
> **LHammonds said:**
> I am curious now what cloud-init does regarding power.

Me too.

---

