---
title: "You are subscribed to this thread kernel booting errror in virtual ubuntu serve"
date: 2010-03-09
forum: Virtualisation
---

### Post by savin on 2010-03-09
Hello Friends help me in this- Am getting tis error after installing and trying to first time boot ubuntu server8.10


"This kernel requires following features not present on the cpu
pae
unable to boot please use the appropriate kernel for your cpu."

currently am using ubuntu desktop edition 9.04. on d top of it i installed virtual ubuntu server8.10




booting recovery mode (single user mode) also giving same error...

---

### Post by kiranmurari on 2010-03-09
Hi,

If you are using VirtualBox, you need to enable the PAE option, by checking the option available from the VM's Settings -> System -> Extended Features (Enable PAE/NX)
   
Hope this helps.

---

### Post by savin on 2010-03-09
ya fine it works...
thanks bro............

---

