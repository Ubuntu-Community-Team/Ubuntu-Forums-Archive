---
title: "Ubuntu keeps freezing"
date: 2017-11-29
forum: Virtualisation
---

### Post by ubunutuisslooooowwww on 2017-11-29
I am running Ubuntu 17.10 in my VMWare with 8GB ram and 8 logical processors at 2.00 GHz. It was fine at first but now it keeps freezing a few times a minute and it is awful to work with. Super frustrating because I am barely able to do anything. I've already increased the specs and it didn't help at all. The system performance monitor shows no indication of any of the components hitting 100%, yet it still happens. Any ideas?

---

### Post by DuckHook on 2017-12-02
Firstly, my&#8212;by now&#8212;standard reply to anyone, but especially to new users. Don't run standard releases unless you need bleeding-edge drivers for bleeding-edge HW. If you are running Ubuntu inside a VM, this automatically means primitive emulated HW and you don't need Aardvark (17.10). **Stick to LTS. This means Xenial (16.04).**

Secondly, a resource hog like Ubuntu is the wrong flavour to run in a VM no matter what resources you set aside for it. The VM's emulated video card is a primitive one and Ubuntu simply expects a much higher end video subsystem to run well. There are other resource issues too. Therefore, run one of the lighter flavours instead. There's Lubuntu, Xubuntu, Mate and Budgie. Stay away from Kubuntu which suffers from the same resource requirements as Ubuntu.

---

### Post by vasa1 on 2017-12-02
I'm trialling Kubuntu 17.10 and 18.04 (no Wayland) in VirtualBox. Both are running pretty decently with just under 4GB RAM and 1 CPU (of two) allocated on a Dell i_3_ laptop. So I suspect there's something else at play. Of course, I'm not doing anything intensive like video editing.

Maybe OP can share some details like the output of *inxi -Fxz* and, when things are slow, the output of *top -n1 -o %MEM*, *top -n1 -o %CPU*, and *inxi -Cxx*.

Maybe OP can fine-tune the VM? What is the host?

---

