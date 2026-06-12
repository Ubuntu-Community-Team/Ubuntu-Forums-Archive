---
title: "Any how-to on how to install virtualbox on hardy 64?"
date: 2008-07-30
forum: Virtualisation
---

### Post by cristo-father on 2008-07-30
Hi.
I would really appreciate any instructions on how to install vb and a tutorial or guide on how to use its features.
Thanks.

---

### Post by bodhi.zazen on 2008-07-30
Download the Ubuntu deb from here :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

```
sudo dpkg -i virtualbox*.deb
sudo apt-get install -f
sudo dpkg -i virtualbox*.deb
```Add yourself to the vboxusers group

Log out and back in

Then : [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

