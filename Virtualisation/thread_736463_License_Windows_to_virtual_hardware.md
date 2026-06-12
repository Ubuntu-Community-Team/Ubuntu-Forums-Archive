---
title: "License Windows to virtual hardware"
date: 2008-03-26
forum: Virtualisation
---

### Post by xtreme- on 2008-03-26
Hi,

I have another one of those questions regarding virtual machines and Windows license, and I have tried to find answers to this for a while now.

I have one not-activated (legal) retail license (number) for Windows XP and want to use it in a virtual machine. I don't mind that it "binds" to a virtual machine (I'm not planning to use it outside a virtual machine).

But I want to be able to move this virtual XP to a virtual machine monitor running on another physical machine (not running i parallel). That is, install XP in e.g. Virtualbox on PC1, run it there for a while, shut it down, and then move the virtual disk to PC2 and start it up there in Virtualbox again.
Is this possible without reactivating and violating the EULA?

I have installed XP in Virtualbox, but in the "Device manager" in XP it detects my CPU and chipset. So it seems as it will bind to this hardware if I activate it, which is not good if we're planning to move the virtual machine...

So, is it possible to make e.g. Virtualbox tell the guest OS (XP in this case) that some specific hardware is used? This would make it impossible for the guest OS to tell which physical machine it is running on, and hence the activation would still be valid on different physical machines.
And would this violate the EULA?

If the EULA is violated it is not a really big concern, since there is no way to tell that it is actually violated; it is not possible to determine which physical computer windows was activated on.

Thank you for any help on this.

---

### Post by veloce on 2008-03-27
I've had variable results with this with vmware.

The key difficulty I had was with the actual processor.  A centrino was considered too different from a xeon by windows hardware detection.

So the vmware hardware abstraction layer isn't complete - not sure what it's like in virtualbox.

---

### Post by xtreme- on 2008-03-28
Thanx for the reply.

If the only (or most critital) problem is with the processor, maybe it is possible to fix it...
I remember in the 'old days' when I was overclocking and using Windows  then my processor was not detected by the OS, but just reported as "Unknown CPU of XX MHZ".
And overclocking did not require a new license (at least not back then), but maybe that's because the diffrenece in speed is quite small?

Is it really neccessary for the guest OS to know which CPU that is used?
It should maybe know of SSE, SSE2, 3DNOW etc. support for speed...

Anyone know how to hack this in e.g. Virtualbox or quemu (assuming it is possible since we can change the source code)?

---

