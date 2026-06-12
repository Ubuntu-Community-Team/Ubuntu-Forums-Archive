---
title: "Paravirtualization how to?"
date: 2011-03-28
forum: Virtualisation
---

### Post by Nemus on 2011-03-28
I am trying to do a Paravirtualization install of ubuntu on a xen centos server and I don't understand the media url for the install tree

how would I setup a install tree for ubuntu that xen could use to install a paravirtualized server. 

I would like to get the performance of the paravirtualized kernel

thank you

---

### Post by falko on 2011-03-30
Do you use virt-install to create guests? In this case, I think you can just insert the Ubuntu CD into your CD-ROM drive and specify /dev/cdrom when virt-install asks

*What is the virtual CD image, CD device or install location?*

---

