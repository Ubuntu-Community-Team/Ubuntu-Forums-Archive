---
title: "Windows7 =&gt; 32Bit or 64Bit ?"
date: 2015-06-30
forum: Virtualisation
---

### Post by simba4 on 2015-06-30
Ubuntu-64Bit, 8GB RAM, Dell XPS1730

I am debating which version of "Windows7" (32Bit or 64Bit) to put in my Virtual Box. I am a day trader and I need that Win7 environment to run a trading platform.

Naturally, I want power and speed, but would it be noticable considering that the
whole structure is sitting on a 64Bit Ubuntu?

What is the 'real cost' of the UBUNTU system when running a VM of 64Bit vs 
32Bit?

Simba

---

### Post by TheFu on 2015-06-30
How much RAM does the Trading software require?
How much RAM will you give to the VM?

If less than 3.5G, 32-bit would take less resources.
If more, 64-bit will make sense.

Don't forget that the software being run might only be 32-bit, so providing a 64-bit OS won't help. If there are any HW drivers involved, that might be an overriding reason to choose one over the other.  

A few yrs ago, there were many web articles about which was best for any specific system. Those should still be valid and out there.

Hope that helps.

---

