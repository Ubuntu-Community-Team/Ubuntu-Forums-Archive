---
title: "Best virtualization software for Windows"
date: 2011-03-04
forum: Virtualisation
---

### Post by CCO Makoto on 2011-03-04
Hi,

I need a fully functional Windows 7 (64-bit) inside my Ubuntu 10.10 (64-bit).

I've tried Virtualbox and VMware Player and I can't seem to get proper 3d graphics. I'm am willing to buy proprietary software such as VMware Workstation or Parallels, however I want your input first.

Specs:

i3 M370 @ 2.4Ghz
4GB RAM
Intel HD Graphics

Basically, what I want, is the closest to a native installation.
Thanks.

---

### Post by divergex on 2011-03-04
Someone correct me if I'm wrong, but I don't think you will ever get full performance 3D through emulation. You really should set up a dual boot system. If you just use Windows 7 for limited apps, then the partition for it could be relatively small.

---

### Post by CharlesA on 2011-03-04
> **divergex said:**
> Someone correct me if I'm wrong, but I don't think you will ever get full performance 3D through emulation. You really should set up a dual boot system. If you just use Windows 7 for limited apps, then the partition for it could be relatively small.
This is correct.

If you are using stuff that needs 3d graphics, you'd be better off to dualboot.

---

### Post by Hedgehog1 on 2011-03-04
I have managed to get 3D to work on Vbox in a Ubuntu Guest system, but the performance suffers.  It is acceptable as Ubuntu uses less resources the Windows.

I have not been able to get 3D to work for Windows as a guest OS at all in either VMware Player or Vbox.

If you want to run Windows Games that need 3D, dual boot really is your best option.

***The Hedge***

:KS

---

### Post by CCO Makoto on 2011-03-05
Thanks for your input. I'll consider the dual-boot option.

@Hedgehog1: Ubuntu inside windows works really well in VirtualBox. Recently they made an upgrade I believe that allows for better 3d performance, I tried the Compiz desktop effects and they worked.

---

### Post by bigcreturns on 2011-03-09
I tried the same thing. Windows 7 x64 running as a guest OS on Ubuntu 10.10 using VMware Player 3.1.3 build-324285 will not function properly for 3D for Win 7. Win 7 would just lock up, so I had to kill VMware player. I did test this numerous times and I made a multitude of changes for my Virtual Machine settings in VMware player. 

 As the other forum members had stated, a dual boot would be your best choice.

---

