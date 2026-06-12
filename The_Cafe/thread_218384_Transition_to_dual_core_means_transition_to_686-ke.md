---
title: "Transition to dual core means transition to 686-kernels?"
date: 2006-07-18
forum: The Cafe
---

### Post by mostwanted on 2006-07-18
As more and more people get dual (or more) core x86 processors, more people will want to switch to a 686 kernel since symetric multi-processing isn't available for 386-kernels. Without SMP, your system will not use both processor cores and there is thus no point in having a dual core chip. 

It's a pretty big issue for a one-CD distro like Ubuntu, since there probably isn't enough free space on the CD for an extra kernel. The developers will have to choose whether they want to support old computers more than they want to support new computers; forcing every user with a dual core processor into downloading a new kernel + the SMP package, would be a most regrettable way to deal with this.

What are your thoughts on this approaching issue?

---

### Post by tseliot on 2006-07-18
If I'm not wrong kernel 2.6.17-x have SMP enabled by default. Therefore 386 kernels might support SMP by default.

---

### Post by prizrak on 2006-07-18
Why just 686? What about K8-SMP kernels not everyone runs Intel :) 
They could just have an SMP version of Ubuntu.

---

