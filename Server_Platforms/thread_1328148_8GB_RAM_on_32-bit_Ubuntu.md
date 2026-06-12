---
title: "8GB RAM on 32-bit Ubuntu?"
date: 2009-11-16
forum: Server Platforms
---

### Post by lodp on 2009-11-16
Hi --

I run 32-bit Ubuntu Server 8.04 on a machine with a 64-bit CPU (AMD Athlon(tm) 64 X2 Dual Core Processor 5600+). It was a stupid decision to go with 32-bit in the first place, but I don't have time right now to re-install.

Now I need to upgrade RAM from 2 GB to 4 GB or 8 GB. Now I'm wondering if the OS will be able to address all that RAM. I read up on it here in the forums archive, and it seems the 32-bit server kernel should be able to cope with the RAM (because PAE is enabled in the server kernel).

Will the fact that I'm running 32-bit Ubuntu on a 64-bit CPU affect memory in any way - such that I wouldn't be able to utilize all the RAM?

I just want to make sure before I shell out the money for the RAM upgrade, I'd very much appreciate your help..

---

### Post by realzippy on 2009-11-16
To address more than 3.5 Gb you need  a 64 bit OS.

installing the Ubuntu server kernel which includes PAE support. PAE stands for Physical Address Extension and it increases the address size from 32bits to 36bits which means you can address up til 64GB.

---

### Post by lodp on 2009-11-16
32-bit Ubuntu Server is supposed to work its way around that restriction, because the server kernel (as opposed to the desktop one) has [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") enabled.

I just looked up /proc/cpuinfo on and saw a PAE flag there, too ... so I'm actually pretty convinced that this will work out. But if somebody knew for sure, that would be great.

EDIT: Sorry realzippy, I was responding to the un-edited post. Do you think the 64-bit CPU + 32 Bit OS combination will cause any problems in this regard?

---

### Post by realzippy on 2009-11-16
No,so you have a "36 bit os" through PAE

---

### Post by insane_alien on 2009-11-16
it'll be fine, but you really should upgrade to 64-bit first chance you get for btter performance.

---

### Post by lodp on 2009-11-16
Thanks for your help guys.. I'll go order the upgrade then.

It was a stupid move not to go with 64-bit in the first place. Maybe I'll do a fresh install when 10.04 LTS is released. 

How much performance do you think I'm wasting with this? And which components suffer the most from it (apache? php? mysql?) ?

---

### Post by Vegan on 2009-11-16
> **lodp said:**
> Hi --

I run 32-bit Ubuntu Server 8.04 on a machine with a 64-bit CPU (AMD Athlon(tm) 64 X2 Dual Core Processor 5600+). It was a stupid decision to go with 32-bit in the first place, but I don't have time right now to re-install.

Now I need to upgrade RAM from 2 GB to 4 GB or 8 GB. Now I'm wondering if the OS will be able to address all that RAM. I read up on it here in the forums archive, and it seems the 32-bit server kernel should be able to cope with the RAM (because PAE is enabled in the server kernel).

Will the fact that I'm running 32-bit Ubuntu on a 64-bit CPU affect memory in any way - such that I wouldn't be able to utilize all the RAM?

I just want to make sure before I shell out the money for the RAM upgrade, I'd very much appreciate your help..

The 32-bit version of Linux can use 64GB of memory, because it uses the segment registers, Windows by comparison does not.

---

### Post by kpholmes on 2009-11-16
> **Vegan said:**
> The 32-bit version of Linux can use 64GB of memory, because it uses the segment registers, Windows by comparison does not.

really? thats pretty sick. i never heard that before

---

### Post by insane_alien on 2009-11-16
> **kpholmes said:**
> really? thats pretty sick. i never heard that before

yes, but its still less efficient than having native large address space capability. and individual processes will still only have 4GB maximum memory allocation.

its a hack and only useful for servers with 32-bit processors.

if you have 64-bit hardware its better to go with 64-bit software than to use an outdated workaround for a problem that should never have existed in the first place.

the only cases where it is a smart idea to use this over native 64-bit disappeared some time in the 90's

---

### Post by sicn on 2009-11-17
I do not completely agree. On an 8GB machine it's not always likely that your processes actually need more than 4GB of RAM, in which case the overhead of 64bit may cost you more than the penalty induced by PAE (which according to Red Hat is no more than 1-10%).

Don't forget, in the 64bit world processes often need twice the RAM (all handles, libs, etc. need twice the amount). However, if we're talking about a machine having >12GB, you definitely should go for 64bit.

Neither is 64bit always faster (even though its a popular believe)... Compare Ubuntu Desktop 64 to Ubuntu Desktop 32... Which one "feels" faster? In my experience the 32bit-version is faster for the normal day to day tasks (not included video editing or file compression).

---

