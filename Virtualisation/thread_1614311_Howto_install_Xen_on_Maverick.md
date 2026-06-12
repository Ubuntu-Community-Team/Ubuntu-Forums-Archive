---
title: "Howto install Xen on Maverick?"
date: 2010-11-05
forum: Virtualisation
---

### Post by fouadatmeh on 2010-11-05
Hello,
I have upgraded to Ubuntu 10.10 64bit with kernel v2.6.33-25 lately and I am trying to install Xen on it (v.3.3 or v4) and run it as Dom0. my problem is that i cannot seem to fing that kernel patched for xen.
Since I am fairly noob, I tried to compile the kernel but i wasn't able to do it...

My questions are:
1- can I find a kernel of the above version patched with xen that works with Ubuntu?
2- If I install an older version of Ubuntu which there is already a kernel for it, can upgrade it to 10.10 and xen keeps working?
3- My final target is to try to run 3D games on a windows guest as I found that someone has already done it on the internet, is that straight forward (after installing xen) or is it difficult?

Thanks and regards

---

### Post by fouadatmeh on 2010-11-16
Hello,

Just a small note of what I have discovered if anybody is interested:

I was able to finally install it (don't ask me for details coz I don't understand most of what I did :) ) and run it in Ubuntu using their suggested kernel version.
The only thing is that GPU sharing needs Intel VPro (or vt-d) to be able to be done.. which I don't have on my Mobo :(

But on another hand, I have tried XenClient on a PC with VPro and it does GPU forwarding!!!

Hope the above helps someone.

---

