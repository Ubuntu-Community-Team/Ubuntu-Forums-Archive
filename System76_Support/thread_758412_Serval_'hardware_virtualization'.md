---
title: "Serval 'hardware virtualization'?"
date: 2008-04-18
forum: System76 Support
---

### Post by Vadi on 2008-04-18
I'm trying to get KVM installed on 8.04 (the upgrade worked flawlessly on 8.04 btw), but the first step is to check if the hardware supports it. Apparently mine doesn't:

> vadi@vadi-laptop:~$ egrep '(vmx|svm)' /proc/cpuinfo
vadi@vadi-laptop:~$

And I'm a bit surprised because this is quite a new laptop. Is this something that can be fixed later, or you need to get a special CPU for this or something?

---

### Post by Vadi on 2008-04-18
Nevermind that, my CPU is just too cheap and doesn't support virtualization. I'll be upgrading it :)

(for those looking, here's a chart ([click]("http://www.intel.com/products/processor_number/chart/core2duo.htm")) which mentions virtualization).

---

### Post by thomasaaron on 2008-04-18
To be honest, I'm not all that familiar with KVM. I know it is kernel based virtualization but needs hardware that supports hardware-level virtualization.

That is really not part of our testing process for Hardy, so I'm not sure of the compatibility level there. But, I could do some one-off testing for you.

In the past, I've tested hardware virtualization capabilities by running some commands from the XEN live CD. Is that what you need? I'd be very surprised if the Serval hardware did not support virtualization.

---

### Post by Vadi on 2008-04-18
Nono it's just that the CPU I got (cheapest dualcore) doesn't have the "Intel® Virtualization Technology (Intel® VT)± 	Enhanced Intel SpeedStep®" thing, which is required my KVM. The better CPU's that you offer for serval do have it, and you can find it in this chart:

[http://www.intel.com/products/processor_number/chart/core2duo.htm](http://www.intel.com/products/processor_number/chart/core2duo.htm)

Anyhow Virtualbox-OSE is working just fine for me, and I'll be upgrading my CPU soon to one that can support it.


Though... looking at the wiki page here ([https://wiki.ubuntu.com/KvmVirtManagerEtc](https://wiki.ubuntu.com/KvmVirtManagerEtc)), it says that this option can be enabled in bios. I checked, but didn't see any options. Strange and I'm confused myself now.

---

### Post by thomasaaron on 2008-04-18
Right, but it might already be enabled.
The only way to know is to test it.

Do you have the SerP4?

---

### Post by Vadi on 2008-04-18
No serp3

Here's what the command says:
> vadi@vadi-laptop:~$ egrep '(vmx|svm)' /proc/cpuinfo
vadi@vadi-laptop:~$[

---

### Post by thomasaaron on 2008-04-18
What's the model number on the bottom of the machine?
And what cpu do you have in it?

---

### Post by Vadi on 2008-04-18
It says "Model: FL90", and sysinfo reports my CPU as "Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz".

---

