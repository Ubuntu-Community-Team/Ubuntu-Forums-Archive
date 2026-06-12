---
title: "Ubuntu 8.04 vserver kernel"
date: 2008-06-04
forum: Virtualisation
---

### Post by Thomy23 on 2008-06-04
Hi guys


is there a prepackaged vserver kernel available yet? I wanted to install a vserver-host on my ubuntu server 8.04. The packages "util-vserver" and "vserver-debiantools" are already installed, all i still need now is the kernel.


Greets

Thomas

---

### Post by vargadanis on 2008-06-11
Hi!

I built the kernel for X64_86 from the srouces and applied the newest patch to them so full VServer functionality is avaliable. If you are interested in it, I could upload it somewhere.

---

### Post by karlmikaze on 2008-06-23
Hi Vargadanis,

sure - please post the instructions on how to build a correctly patched kernel. Many, many users out there are eagerly waiting for that kind of information.

Thanks & greetings
Chris

---

### Post by Adam Ryczkowski on 2008-07-02
> **vargadanis said:**
> Hi!

I built the kernel for X64_86 from the srouces and applied the newest patch to them so full VServer functionality is avaliable. If you are interested in it, I could upload it somewhere.

How did you managed to do it at all, when I see that the vserver is supported only for kernels older or equal to 2.6.22.19, and current Ubuntu 8.04 kernel is 2.6.24.19...? ([http://linux-vserver.org/Downloads](http://linux-vserver.org/Downloads))

Or do I miss something?

---

### Post by karlmikaze on 2008-07-02
Hi,

have a look at [http://vserver.13thfloor.at/Experimental/](http://vserver.13thfloor.at/Experimental/) - there's the bleeding edge stuff.

That way we compiled a booting kernel for 8.04, based on the vanilla 2.6.25 sources, BUT:
[LIST]
[*]"vserver <name> start" crashes
[*]some patches didn't integrate smoothly (disabled for testing purposes, for now)
[/LIST]

We'll keep on trying.

Chris

---

### Post by skliarie on 2008-07-03
I also was looking for vserver kernel (which I have used in debian), but only found openvz kernel.
After checking openvz technology, I don't want to go back!

Someone wrote nice vserver and openvz comparison [here]("http://www.fsfe.org/en/fellows/rca/from_out_there/from_zero_to_virtualization_linux_vserver_vs_openvz").

---

### Post by vargadanis on 2008-09-07
> **Adam Ryczkowski said:**
> How did you managed to do it at all, when I see that the vserver is supported only for kernels older or equal to 2.6.22.19, and current Ubuntu 8.04 kernel is 2.6.24.19...? ([http://linux-vserver.org/Downloads](http://linux-vserver.org/Downloads))

Or do I miss something?

No you didn't miss anything. Here are some detailed info on how to use a kernel that can be patched... 
[http://hungarydan.com/wp/?p=17](http://hungarydan.com/wp/?p=17)

Regrads...

---

