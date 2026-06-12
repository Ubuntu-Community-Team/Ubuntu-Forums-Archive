---
title: "Enterprise virtualization"
date: 2008-10-31
forum: Virtualisation
---

### Post by allspiritseve on 2008-10-31
I am currently dual-booting xp and ubuntu, solely so that I can run Photoshop CS3. I've tried CS2 through wine, but it's just too buggy for me. I would like to find another solution that doesn't involve dual-booting.

What is the most robust, enterprise-level virtualization software out there? I've only heard of VMWare and Virtualbox, but I don't know that much about either. I want something that WORKS.

What system specs would be ideal to run this without any noticeable performance decrease? If I were to buy a laptop, what should I be looking for? 

Thanks,

Cory

---

### Post by Weissbier on 2008-10-31
I can suggest you the KVM hand-compiled together with QEMU. 
I have seen NO performance difference according to Various Processor Benchmarks, between a native Windows-XP and one running as Virtual "Guest" System inside my Ubuntu 8.04-1. I was quite impressed to be honest. :)

Disadvantage when using the default emulated Cyrrus-Logic graphics-card is only 16Bit when using max resolution of 1280-1024. But you can switch to a VESA capable "Virtual" Graphics-Card (haven't tried it yet)

Hardware:
Use any actual Intel/AMD Processors which are capable of "Hardware-Virtualization".

I used this tutorial: [http://redbrain.co.uk/?page_id=29](http://redbrain.co.uk/?page_id=29)

But actually this line: ```
./configure –prefix=/usr
```
should be rather this:```
./configure -–prefix=/usr
```

I hope this helps you a little bit.

---

### Post by allspiritseve on 2008-10-31
Don't you need two computers for KVM?

Edit: Never mind, thinking of KVM Switch. KVM looks like its still pretty underdeveloped compared to vmware and virtualbox

---

### Post by Weissbier on 2008-11-01
> Don't you need two computers for KVM?
No.....:)
> KVM looks like its still pretty underdeveloped compared to vmware and virtualbox 
Thats because KVM isn't a emulator like the others. KVM is only a interface providing advanced hardware virtualization to your system-kernel (As far as i have understood it - other may correct me).
To "use" the KVM capabilities you can use either the "emulator" QEMU (like i suggested it) or the Method with Ubunuts "libvirt" described here:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by allspiritseve on 2008-11-02
Is KVM significantly better than VirtualBox? What are the +/- of each?

---

