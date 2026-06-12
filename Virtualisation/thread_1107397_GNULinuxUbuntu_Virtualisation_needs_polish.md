---
title: "GNU/Linux/Ubuntu Virtualisation needs polish"
date: 2009-03-26
forum: Virtualisation
---

### Post by freakalad on 2009-03-26
Been immersing myself in virtualisation for some time now, with a strong focus on the FOSS varieties.

KVM seems to be the Ubuntu platform of choice, and I can see why. It's pretty simple, but at the moment is is seriously lacking in polish and simple & straight-forward management tools.
virt-manager does go some way towards addressing this, but it has it's own flaws.

Xen/Xen-Source is emerging as the dominant player, with strong backing from many players, including RH, and management tools that are far superior that those of KVM.

Much of KVM & Xen's stuff are getting blended (like virt-manager being somewhat of a universal GUI tool), which kinda makes sense.

I'll try & list some tools & resources I've come across in my quest to find tools to simplify my life (I pop a lot of little VM's in my line of work. "VM farmer"?). Of paramount importance it intuitive & ease of use.
Please note that I've been unable to get many of these working without significant tweaking, which, IMO, does not make them ready for widespread use

* virt-manager
* proxmox
* eucalyptus
* ubuntu-vm-builder
* convirt
* {more to be added}

I dearly wish for some sort of web-based tool that would simplify the creation (aka provisioning) & management of vm's & the server; KVM, Xen (VirtualBox & others?). the way that VMWare v2 does this is an absolute shining example (keeping it simple & straight-forward). Some WebMin module?

I'm going out on a limb here and guessing that Jaunty may actually address many of these issues in the upcoming release, since it's positioning itself to be very "cloud-centric", and therefore by extension would have to address virtualisation at it's core.

Please feel free to add comments, critiques & suggested tools & resources to this thread

---

