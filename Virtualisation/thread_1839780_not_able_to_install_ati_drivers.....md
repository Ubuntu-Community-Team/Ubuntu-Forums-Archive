---
title: "not able to install ati drivers...."
date: 2011-09-06
forum: Virtualisation
---

### Post by abhiiceman on 2011-09-06
hav installed ubuntu 11.04 os guest os on vmware workstation in win 7...problem is even after installing ati drivers the ccc or ubuntu nt able to detect ati drivers..when i open ccc it shows drivers not installed and if i type aticonfig in terminal it shows adapter not found......plz help me guys im fed up googling nd trying diff methods frm months so plz reply ASAP....

---

### Post by 2F4U on 2011-09-06
I don't know much about VMWare, but in VirtualBox all the hardware and therefore also the graphics card, is virtualized. This means that the guest OS doesn't see the ATI card from the host machine but instead sees a generic graphics card.

---

### Post by CharlesA on 2011-09-06
Running an OS inside a VM presents that OS with virtual hardware. What are you trying to accomplish?

---

