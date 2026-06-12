---
title: "Video Card problem...."
date: 2007-11-25
forum: Virtualisation
---

### Post by poot on 2007-11-25
I run windows bye default and i really like linux but my mom won't let me install it, so i use a virtual machine to run it instead.  I use VMware Workstation for my virtual machines, and it runs great..cept i can't get it to pick up my nvidia card. I have already installed vmware tools on ubuntu and i hit ctrl + alt + backspace to restart x...but when i go to turn my advanced desktop effects on it says that they can not be enabled. I have a nvidia 7600 gs. Any help would be really great :D thanks in advance!! ^_^

---

### Post by snaileater on 2007-11-25
As all virtualization software, VMWare doesn't give access to the real video card of the host system. Instead, a virtual video card is presented to the guest system, which is probably a different type, than the real one.

The reason is, that the host operating system would get confused, if an external instance would have a chance to modify the hardware state.

---

### Post by poot on 2007-11-25
I figured out this much...in the screens and graphics window under administration it says linux is using vmware- vmware virtual video cards.  Thanks anyways though ^_^ 

Is there a way i can set the virtual card to act as my nvidia or at least let me enable the advanced desktop effects?

---

### Post by snaileater on 2007-11-25
No.

---

