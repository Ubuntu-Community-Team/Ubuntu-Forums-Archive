---
title: "Mac OS X Lion host, Latest VirtualBox, Pangolin Guest 32 or 64 bit?"
date: 2012-04-26
forum: Virtualisation
---

### Post by mlepage on 2012-04-26
I've got a 2011 MacBook Air running Lion, and the latest VirtualBox. I'm looking to perform a new Ubuntu install using 12.04 (Pangolin). I'm just wondering, should I go with 32-bit or 64-bit in the guest? I know VirtualBox will do both, but I confess I still don't understand the practical issues/differences/tradeoffs.

Really I just use the Ubuntu VM for light development-type stuff (say scripting, like Lua or Python) now and then. I'm probably more concerned about battery usage than raw performance.

Advice? Is there a big page somewhere that will explain all the trade-offs to me?

---

### Post by TBABill on 2012-04-26
If you're not giving it a huge chunk of RAM, and since you have a 4GB RAM machine I suspect you are not, it would probably be better using 32 bit in that instance.

---

### Post by mlepage on 2012-04-27
So that's the main concern, using 64-bit if you have more RAM? (I don't on this machine, as you said.) No big differences in battery life or performance running?

---

### Post by TBABill on 2012-04-27
I have never run Ubuntu on my MB Pro so I can't attest to it, but I've never experienced a difference in battery life on other machines based on 64 or 32 bit. If I only have 1-2GB I generally stick to 32 bit, but on machines with 3+ I stick with 64. In a VM you will dedicate part of your 4GB, which is why I figured 32 would probably work best as far as resources.

---

### Post by lukeiamyourfather on 2012-04-27
> **mlepage said:**
> So that's the main concern, using 64-bit if you have more RAM? (I don't on this machine, as you said.) No big differences in battery life or performance running?

If you have a 64-bit processor then use the 64-bit version. Regardless of how much memory you have or don't have the 64-bit version is significantly faster.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_3264&num=1)

---

### Post by mastablasta on 2012-04-27
64 bit should be faster on 64bit maschine. the question is is it that much faster than a 32bit? particulary if you run 32 bit applicaitons?

---

### Post by lukeiamyourfather on 2012-04-30
> **mastablasta said:**
> the question is is it that much faster than a 32bit?


Did you see the link comparing the two? The differences in some areas are small but are significant in others. Overall, yeah, it ***is*** that much faster.

> **mastablasta said:**
> 
particulary if you run 32 bit applicaitons?

Who cares? They'll still work. Everything else that isn't 32-bit (which is pretty much everything on the system) will perform better. There's no good reason for the overwhelming majority not to use a 64-bit operating system these days.

---

