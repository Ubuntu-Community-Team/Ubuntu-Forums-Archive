---
title: "64 bit guest OS inside 32 bit host? (VirtualBox OSE)"
date: 2009-05-20
forum: Virtualisation
---

### Post by Vunutus on 2009-05-20
I'm wanting to test some server/client setups with an array of virtual machines. I run 32 bit ubuntu on this machine (my home machine). My processor, however, is a 64bit AMD processor. I downloaded the 64 bit ubuntu server ISO and tried to install it inside virtualbox, but it reported that I had the wrong kernel and would not proceed with installation.

Is it possible to have a 64 bit guest inside a 32 bit host. or do I need to use 32 bit ubuntu server for my tests?

---

### Post by Keithhed on 2009-05-20
I had a similar issue.  I tried to install 64bit Debian and it wouldn't work.  Every other distro works perfectly (as long as its 32 bit)  It could be that the VirtualBox doesn't support 64 bit computing.

---

### Post by caver1 on 2009-05-21
Are you running VB 2.0 or higher?
They do support 64bit. the earlier versions don't.
caver1

---

### Post by Keithhed on 2009-05-21
I'll look into that.  Thanks!

---

### Post by Cheesemill on 2009-05-21
As far as I'm aware you can only install a 64-bit guest OS if you're also running a 64-bit host OS.

Cheesemill

---

### Post by caver1 on 2009-05-22
> **Cheesemill said:**
> As far as I'm aware you can only install a 64-bit guest OS if you're also running a 64-bit host OS.

Cheesemill



If you have a 64 bit capable system running a 32 bit OS I think you can.
I may be wrong but I thought It was the hardware that determined 
if you can run a 64bit host.
caver1

---

### Post by bodhi.zazen on 2009-05-22
Background info / FYI : Virtualbox will run 64 bit guests so long as you have the proper hardware.

You need a 64 bit CPU with virtualization technology :

INTEL-VT and AMD-V

To see if your cpu can do , run this command in a terminal :[FONT=monospace]

```
[/FONT]egrep '(vmx|svm)' --color=always /proc/cpuinfo
```

If you get an output with either vmx or svm in run you can run 64 bit guests in Virtualbox (or better consider KVM).

You will need to activate hardware virtualization both in your bios and in Virtualbox.


====

In answer to your question re : 64 bit guests in a 32 bit host, that I do not know.

---

