---
title: "&quot;kvm: disabled by bios&quot; despite /proc/cpuinfo showing vmx flag"
date: 2008-08-30
forum: Virtualisation
---

### Post by Limnologist on 2008-08-30
Hello!

I'm attempting to set up kvm, and despite having virtualization enabled in my bios, I cannot load the kvm-intel kernel module. In the rest of my forum searching, I've only found people who have not turned on virtualization receiving this error, which is not my case. I'm not sure how to proceed on this one.

Kernel uname -a:
Linux epiphyte 2.6.24.19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Dmesg error line:
[   34.727695] kvm: disabled by bios

I am attaching the output of 'cat /proc/cpuinfo' as well as the full dmesg output. 

Preemptive thanks!

--Lim

---

### Post by vishalrao on 2008-08-30
if you just now enabled it in the bios i think you have to shut down completely and power off, then restart, (cold boot) only then the change works.

plus, you might need to add yourself to the kvm and/or libvirt groups (i forget the actual group name but you can search around)... HTH

---

### Post by Limnologist on 2008-08-30
> **vishalrao said:**
> if you just now enabled it in the bios i think you have to shut down completely and power off, then restart, (cold boot) only then the change works.

plus, you might need to add yourself to the kvm and/or libvirt groups (i forget the actual group name but you can search around)... HTH

Oh, forgot to mention I saw those things suggested during my search for more info, I restarted the machine several times (in the course of messing with it), and also added myself to the 'libvirtd' group.

---

### Post by Limnologist on 2008-09-02
Now I'm thinking that despite the flag being reported in /proc/cpuinfo, the bios still has the VMX extension disabled.

Since the damn bios doesn't support turning it on, I guess I'm going to have to hunt for the bit to flip manually. I hate Sony. I'll report here if I find it.

---

### Post by zong1 on 2010-06-26
Sony, on many notebooks, including my Vaio SZ, have disabled ACPI and the VT-x extensions even though the Intel chips support these.  Even when the system reports it, it cannot use it. This also applies to NCQ on SATA controllers on some Sony Vaio's as I have found out.  


There are some threads on a forum somewhere about how to manually flip the bit to enable this and it has been successful on many notebooks.  

My advise it not to buy Sony notebooks, and I offer this advise to myself :(
Thank-you Sony.

---

