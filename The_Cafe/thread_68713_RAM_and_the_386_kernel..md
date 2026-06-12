---
title: "RAM and the 386 kernel."
date: 2005-09-24
forum: The Cafe
---

### Post by BoyOfDestiny on 2005-09-24
Hi, I'm wondering how many new users have 1 gig of ram on their machines, but aren't using it all with the default kernel...

Please note, I'm not trying to start a thread of why are things i386 etc...

I just think there should be an easy way to let newbies know, (or maybe include another kernel or pick the meta packages based on what CPU is detected... etc)

I'm willing to bet a lot of people might not even notice their machine has a handicap...

---

### Post by GoA on 2005-09-24
That's why you have to use newer kernel or compile the high memory support to 386 kernel.

---

### Post by drizek on 2005-09-24
IIRC, breezy chose the i686 kernel for me automatically.

---

### Post by Ubunted on 2005-09-24
Just a matter of swapping kernels to k7/686 in Synaptic.

Search for "linux" in Synaptic, and wherever you see "386" selected, select the 686/k7/smp counterpart you want and install them. Reboot into the installed kernel, remove the 386 modules and be happy - you should be using the full 1GB of RAM.

---

### Post by Keffin on 2005-09-24
The point is that you shouldn't have to install a new kernel to use all your RAM, especially now 1 gig is a common amount. I've been using a 386 kernel on hoary for a while without noticing until a post in the forums, then I switched to 686.

Installing the breezy preview however gave me access to all my RAM. I don't know if this was by auto-choosing the 686 kernel or just an improvement in the 386 package, but I just saw that and was happy.

---

