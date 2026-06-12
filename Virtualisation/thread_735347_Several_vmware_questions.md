---
title: "Several vmware questions"
date: 2008-03-25
forum: Virtualisation
---

### Post by StOoZ on 2008-03-25
A-Hoy vmwaers and ubuntuers!!! :KS

I have several questions,regarding the setup and use of vmware on ubuntu 7.10.
1) is there any way to install the nvidia 6600gt drivers on a virtualized windows xp?
2) at the moment im using the NAT for internet connection on the vm'd xp, which shares the same IP as the ubuntu guest.
is there any way to give it a different IP ?

---

### Post by fjgaude on 2008-03-25
> **StOoZ said:**
> A-Hoy vmwaers and ubuntuers!!! :KS

I have several questions,regarding the setup and use of vmware on ubuntu 7.10.
1) is there any way to install the nvidia 6600gt drivers on a virtualized windows xp?
2) at the moment im using the NAT for internet connection on the vm'd xp, which shares the same IP as the ubuntu guest.
is there any way to give it a different IP ?

1) no way, the vm uses a virtual piece of software to simulate your video card. No other way at present.

2) sure, by using instead of NAT, use Bridged... do a little reading and you will see how it is done. The vmware manual is a good place to start.

Let us know how you are doing.

---

### Post by tribaal on 2008-03-25
1) Not at the moment... 3d acceleration isn't supported.
2) Sure! Just set your guest VM's virtual ethernet to "bridged". 

Enjoy :)

- Trib'

---

### Post by StOoZ on 2008-03-25
thank you both!
will do a search on 'bridged'!

---

### Post by StOoZ on 2008-03-25
well tried digging the 'bridged' thingy, but to no avail... :(

---

### Post by veloce on 2008-03-27
In the vmware console edit the guests settings.

select the virtual network card and you will see a selection of connection types including NAT and Bridged.  Just select bridged.

---

