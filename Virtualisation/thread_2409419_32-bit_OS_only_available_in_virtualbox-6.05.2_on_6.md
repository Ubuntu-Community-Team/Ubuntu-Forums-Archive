---
title: "32-bit OS only available in virtualbox-6.0/5.2 on 64-bit Ubuntu 18.04 LTS host?"
date: 2019-01-02
forum: Virtualisation
---

### Post by smith73 on 2019-01-02
Hello,

I installed a .deb package virtualbox-6.0 (amd64) from  Virtualbox Linux_Downloads on Ubuntu Mate 18.04.1 Bionic 64-bit host (HP  notebook)
and noticed that for new Windows and Linux guests there  are only 32-bit versions available. The same 32-bit guest versions only  were available
also after installing virtualbox-5.2 on the same host via Software Boutique.

I  have also an Ubuntu Mate 16.04 LTS 64-bit host installed earlier on an  Asus notebook and an Oracle virtualbox v. 5.2.18 (r124319 Qt5.6.1)
installed  there which allows 64-bit Windows and Linux guests to be created. A  Windows 8.1 64-bit guest was successfully created and used there.

What's  the issue of only 32-bit guests available to create in amd64 vIrtualbox  on Ubuntu 18.04.1 64-bit host? Is it possible to enable Virtualbox
with the option for 64-bit Linux and Windows guests?
(I basically need at least a one 64-bit Windows (8 preferentially) guest).

Can there be any danger of installing virtualbox for 64-bit Ubuntu 16.04 Xenial (which seems to allow 64-bit guests) onto 64-bit Ubuntu 18.04 host?


Thanks

---

### Post by SeijiSensei on 2019-01-02
Make sure you have VT-x enabled in the system BIOS.

---

