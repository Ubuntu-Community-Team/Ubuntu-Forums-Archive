---
title: "How is Amazon running Windows guest (with high performance) on Xen?"
date: 2009-07-07
forum: Virtualisation
---

### Post by spiked on 2009-07-07
Hey guys,

   There have been reports that Amazon is able to run Windows as a guest on Xen with pretty fast performance. My question is, what have they done for that? 

Are they running a modified Windows?

Are they providing hardware support to the machines that run these Windows images?

Have they actually rewritten Xen to run Windows faster even without HW support for virtualization?

I'm contacting some people there, let's see if I find something out, but does anyone have any info for now?

Any opinions/info will be highly appreciated.

Thanks a lot.

---

### Post by veloce on 2009-07-07
Why do you think this would be difficult?  

Windows works well virtualised under vmware - without hardware support - can't see why it wouldn't under Xen.

---

### Post by spiked on 2009-07-08
Hi Veloce, Thanks for your reply.

So are you saying that because VMWare runs Windows fast, Amazon must have modified Xen to make Windows run fast as a Guest? Because I've used Xen 3.4 running an XP guest on an Ubuntu 8.04 host, and it's very slow. Whatever little changes I've made for the XP image so far haven't really helped the performance much.

Thanks a lot.

---

### Post by spiked on 2009-07-08
Hey, 

 Also, does someone know about the Windows GPL PV drivers available for use with Xen? Specifically, can they be used to increase the performance of Windows when used **without** HW Virtualization support? That last bit is very significant.

Thanks a ton, guys.

---

