---
title: "Ubuntu Server (lucid) on Hyper-V anyone got it stable?"
date: 2011-02-25
forum: Virtualisation
---

### Post by kofi2 on 2011-02-25
Hi

At work we have Hyper-V since R1 now at R2 but have never been particularly happy with the stability of any Ubuntu-provided Kernel in Lucid LTS. Has anyone ever got a configuration where you can toss on load on a Ubuntu VM without getting any of the following symptoms:


[LIST]
[*]VMBus Network looses connection under certain circumstances (poweroff of VM required)
[*]Random hangs - can't even log in, console writes output about saying something about /proc
[*]Sometimes loosing storage (mounted as ro)
[/LIST]

What confuses me, is the fact, that with no RHEL 5.x or RHEL-clone I got into such trouble by using the LIC 2.1 from Microsoft (which essentially are older hv drivers than what is in staging).

I have been compiling also my own Kernels starting from 2.6.33 up to 2.6.37.1 - with similar results, even with very minimalistic Kernel configurations and on different Processors (Opteron 8218 and Xeon L5420 machines)

I have tested and experienced these problems with Hyper-V 2008 SP2 as well as on 2008 R2 RTM.

Anyone got a working configuration with Ubuntu. This is really a show-stopper for me since the emulated devices are working stable but are well - just dead slow.

---

