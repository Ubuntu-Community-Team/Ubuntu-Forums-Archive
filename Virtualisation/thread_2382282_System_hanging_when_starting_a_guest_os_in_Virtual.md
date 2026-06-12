---
title: "System hanging when starting a guest os in Virtualbox"
date: 2018-01-11
forum: Virtualisation
---

### Post by biz122 on 2018-01-11
Hey,

So today I upgraded my system and there was a kernel upgrade in there. Perhaps to prevent the Spectre & Meltdown exploits (4.13.0-26-generic).

Unfortunately it seems as if this has caused Virtualbox to potentially lock my system completely.

If I launch a VM (any kind, linux, windows etc), the whole system freezes and I can not bring it back to working state again - unless I do a forced reboot by holding the power-button.

I have re-installed Virtualbox, recompiled the kernel drivers (for Virtualbox) and even re-installed the system. Nothing has helped so far, and I do rely on some of these VM's..

Has anyone experienced the same issues, perhaps with the same hardware? Might you have a solution?

My system is:

Dell xps 13, 9360
Ubuntu 16.04
Linux 4.13.0-26-generic
Secure boot is on (I sign my kernel drivers)

---

### Post by Alistair_Grant on 2018-01-11
Yep, same problem (only tested with a Win10 guest).

Dell XPS13 9333
Ubuntu 16.04
Linux 4.13.0-26-generic

And no solution, unfortunately.

Cheers,
Alistair

---

### Post by Alistair_Grant on 2018-01-11
Upgrading to VirtualBox 5.2 solved it for me, see: [https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26/994320#994653](https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26/994320#994653)

---

### Post by biz122 on 2018-01-11
Mr Grant,

This worked for me as well.

Thanks man!

---

### Post by aboulhassan on 2018-06-20
> **Alistair_Grant said:**
> Upgrading to VirtualBox 5.2 solved it for me, see: [https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26/994320#994653](https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26/994320#994653)

What to do if the same happens with VirtualBox 5.2!
I work on Ubuntu Budgie 18.04, virtualBox works fine.
When I switch to GNOME desktop the system freezes, the mouse pointer still moves, but no response whatsoever, and the only solution is to power off using the power button.

---

### Post by robertdmunn on 2018-06-27
I have a similar situation. Running 18.04 with kernel 4.17.0 with a WIndows guest OS. Twist for my setup is that I am running on an Envy x360 Ryzen laptop. Ryzen/AMDGPU support is new and not completely stable.

My guest runs for awhile and then everything except the pointer on my host system freezes. Sometimes even the pointer freezes. 

Mostly I am waiting for kernel 4.18 to provide more robust support. 

> **aboulhassan said:**
> What to do if the same happens with VirtualBox 5.2!
I work on Ubuntu Budgie 18.04, virtualBox works fine.
When I switch to GNOME desktop the system freezes, the mouse pointer still moves, but no response whatsoever, and the only solution is to power off using the power button.

---

