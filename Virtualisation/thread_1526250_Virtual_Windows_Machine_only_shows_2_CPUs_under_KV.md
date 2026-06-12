---
title: "Virtual Windows Machine only shows 2 CPUs under KVM"
date: 2010-07-07
forum: Virtualisation
---

### Post by pmb@novodynamics.com on 2010-07-07
Hello:

I'm trying to run a multiple CPU MS Windows virtual machine using KVM. Though I've selected 8 cpu's on my multi-core hyperthreaded machine, I can only ever see 2 cpu's under windows. I'm a bit perplexed on what I need to do to fix this. I haven't been able to find any solution on the web either. Does anyone have any suggestions?

Thanks.

pmb

---

### Post by sh1ny on 2010-07-08
What windows version ?

---

### Post by pmb@novodynamics.com on 2010-07-08
Thanks for your reply. I've tried both 32-bit Windows 7 and 32bit XP SP2. Neither one shows more than two cpu's.

---

### Post by sh1ny on 2010-07-08
Try professional 64bit versions.
I am not really sure if it matters tho, haven't ran a windows guest in a while, but i might try just for kicks.
I am pretty sure microsoft puts some limits in each edition of windows ( home/pro/enterprise etc. ). So you might be facing this, but don't quote me on it :D

---

### Post by naelq on 2010-07-08
hi,
according to this: [http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/970c999c-8ffc-4611-968c-7d0ceffbedd4](http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/970c999c-8ffc-4611-968c-7d0ceffbedd4)
the limit is on the number of "CPU Sockets", & if i'm not mistaken, every single virtual CPU you assign for the guest is considered a socket.. makes any sense?

---

### Post by TheFu on 2010-07-09
I'm fairly certain that all versions of WinXP are limited to 2 CPUs. [https://www.microsoft.com/licensing/about-licensing/multicore-processor-licensing.aspx](https://www.microsoft.com/licensing/about-licensing/multicore-processor-licensing.aspx)

---

