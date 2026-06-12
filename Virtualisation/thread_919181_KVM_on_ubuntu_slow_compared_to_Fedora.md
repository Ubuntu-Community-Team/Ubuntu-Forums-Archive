---
title: "KVM on ubuntu slow compared to Fedora"
date: 2008-09-13
forum: Virtualisation
---

### Post by mosestruong on 2008-09-13
Does anyone know the reason for KVM running slowly on Ubuntu Hardy compared with running on Fedora 9?

Also, on Ubuntu I can't shutdown a virtual machine, I had to Destroy it in order to get it to shutdown.

---

### Post by mosestruong on 2008-10-01
I'm wondering whether it is using the virtualisation hardware or whether its trying to use qemu - does anyone know how I can check what KVM is using???

---

### Post by Yann2 on 2008-10-01
Very fast here - for the shutdown to work you may need to install the acpid package (which should really be installed by default). Are you sure you are running your vms in accelerated mode?

---

### Post by Greettat on 2008-10-01
it is better to fight for good than to fail at the ill.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

### Post by mosestruong on 2008-10-02
I've already got acpid installed. But pressing shutdown still doesn't do anything - need to use destroy to shutdown...

How do you check what mode it is running on?

---

