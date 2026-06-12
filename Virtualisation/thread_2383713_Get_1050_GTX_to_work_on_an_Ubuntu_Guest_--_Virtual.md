---
title: "Get 1050 GTX to work on an Ubuntu Guest -- VirtualBox"
date: 2018-01-28
forum: Virtualisation
---

### Post by kolt-real on 2018-01-28
Hi everyone.
I just set up an Ubuntu Vbox on my Windows laptop. This Vbox's purpose is to run an implementation of the TensorFlow framework.
Find the project here : [https://github.com/cysmith/neural-style-tf](https://github.com/cysmith/neural-style-tf)
Since this works much faster on GPU I'd like to make my hosted Ubuntu get to know my Nvidia graphic card.


I've installed the guest additions provided by Oracle, this does not help at all (I would have been really surprised).


Does anyone have a hint to make pop my graphic card up in a nice return of lspci ??

---

### Post by cruzer001 on 2018-01-28
Hello

I have not used passthrough, but I can point you at this:

[https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough)

[https://forums.virtualbox.org/viewtopic.php?f=7&t=83661](https://forums.virtualbox.org/viewtopic.php?f=7&t=83661)

---

### Post by kolt-real on 2018-01-30
Thank you, I tried many things but since VirtualBox uses its own driver it seems really hard to get this work properly...
I think this is far beyong my skills. I'm considering setting up a dual boot instead of virtualising Ubuntu.

---

### Post by simosx on 2018-01-30
Since it is for use with Tensorflow, then just don't use Virtualbox and use LXD instead. 
In that way, you will save some processing power as LXD is much more light to the resources. 

See [https://stgraber.org/2017/03/21/cuda-in-lxd/](https://stgraber.org/2017/03/21/cuda-in-lxd/) for instructions.

---

