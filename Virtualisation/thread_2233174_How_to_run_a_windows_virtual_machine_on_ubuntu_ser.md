---
title: "How to run a windows virtual machine on ubuntu server"
date: 2014-07-06
forum: Virtualisation
---

### Post by ssaththiyan on 2014-07-06
Hi 

I need to run a windows virtual machine on a ubuntu server using QEMU, how do i do this? i have tried several times and got failed. Please some one guide me how to do this task?

Thank
sathi

---

### Post by KillerKelvUK on 2014-07-07
Why does it need to be QEMU?

---

### Post by ssaththiyan on 2014-07-14
As i have to match that and test , i need to use KVM and QEMU.

---

### Post by TheFu on 2014-07-14
Uh ... either kvm or qemu. Not both.

Am I confused or didn't your hardware lack VT-x support so KVM wasn't possible?  

To run Windows under KVM is really easy. What are you stuck on?  What have you tried?  There are at least 50 how-to articles on this topic. [http://virt-manager.org/](http://virt-manager.org/) is the easiest way that I know. It is what I use. That tool is in the ubuntu repos.

---

