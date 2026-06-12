---
title: "Portability of VMWare VMs?"
date: 2008-11-05
forum: Virtualisation
---

### Post by 3strandchords on 2008-11-05
Hi all...

These forums are so helpful, I thought I'd post this here to see if I get a response.

Q:  How "portable" are VMWare virtual machines between different platforms (running VMWare server), or even different products?

Background:  I'm running VMWare Server 2.0 on a fully-patched Ubuntu 8.04 machine.  I built a WindowsXP VM to serve as a source for imaging our Windows clients.

I've now got several users thinking about running VMWare Desktop (I assume) on MacOS X and Windows Vista clients.  I was hoping there might be a way to just grab the .vmx and .vmdk files from the VMWare server and import them onto the new machines.

Anyone played with anything like this who could provide some guidance or gotchas?

If not, anyone interested who wants me to post follow-ups after we experiment with it?


Thanks  3Strand

---

### Post by PilotJLR on 2008-11-07
It's generally quite easy to move these VM's about from platform to platform. One possible issue would be going from Intel to AMD or vice-versa, though that does work.

Depending on how your XP license was required, it may require activation after moving hardware. OEM licenses certainly will complain - VLK will not.

Note that there are more than one version of VM, though... moving Server vm's is easy. In making a VM in the Workstation product, use the "Custom" mode to specify which version of VM you want to use. Workstation will even list (in the custome dialog) what products are supported under a given version. If you dial it down to v5 guests, then it works on basically anything new (except for ESX, but that's what Converter is for).

---

