---
title: "domain u configuration in xen hypervisor on ubuntu 18.04"
date: 2019-02-22
forum: Virtualisation
---

### Post by siddharthav on 2019-02-22
hi,
By referring [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)  I have installed xen on my laptop (intel quadcore processor)  with ubuntu 18.04. and configured domu1.


> The output of is as in the image-1.( the domu1 is in the blocked(-b) state )



> when I tried to open the guest its not booting am facing the below problem.
   --> if I use " $: sudo xl console domu1" its  taking me to xen guset installation process from the beginning"


  --> If I use "$: sudo xl create -c /etc/xen/domu1.cfg" its giving me the error as in the image2.


> I have also attatched my domu1.cgf file also.

Also when I restart the system the Domain- U is not available for me.
please anybody help me on this kind request.

---

