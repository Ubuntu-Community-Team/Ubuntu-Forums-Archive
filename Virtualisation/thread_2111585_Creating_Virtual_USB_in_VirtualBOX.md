---
title: "Creating Virtual USB in VirtualBOX"
date: 2013-02-02
forum: Virtualisation
---

### Post by safaa89 on 2013-02-02
I want to create a virtual usb to be seen from all CentOS virtual machines (servers) in the virtualbox using ubuntu .
how can I do that ? ](*,):sad:

---

### Post by SeijiSensei on 2013-02-02
Are you asking about accessing a physical USB port on the host from the guest?  You need to add the extensions pack for that.

Otherwise I do not know what you mean by a "virtual USB," but if you mean creating an emulated USB device on the host that is visible from the guests, I've never seen any option in VirtualBox to enable that.

---

### Post by safaa89 on 2013-02-03
> **SeijiSensei said:**
> Are you asking about accessing a physical USB port on the host from the guest?  You need to add the extensions pack for that.

Otherwise I do not know what you mean by a "virtual USB," but if you mean creating an emulated USB device on the host that is visible from the guests, I've never seen any option in VirtualBox to enable that.
  
my boss asked me to do that and after hours of searching , I found that it's not supported in virtual box .
do you know ant software that emulates virtual USB drivers on Ubuntu ?
If I do this , (create some virtual usbs on my host) so I have to install extensions pack ?
I've already did downloaded it but I want to know before installing if it affects the machines I'm using in my virtual box .
any idea ?

---

### Post by SeijiSensei on 2013-02-03
> **safaa89 said:**
> my boss asked me to do that and after hours of searching , I found that it's not supported in virtual box .
do you know ant software that emulates virtual USB drivers on Ubuntu ?

I'd look into VMWare as an option because it's the most widely used virtualization program in professional server rooms.

That said, I'm dubious you'll find anything like this since USB technologies are [encumbered by various patents]("http://www.usb.org/developers/docs/").

Is this just a wishlist item from your boss, or does he know for sure that such a thing exists?

The extension pack is required to enable the virtual machines to communicate with the host's *physical* USB ports.  I suspect that Oracle cannot make an open-source version of the relevant USB driver available for the same patent issues.  Adding the extension pack will let you use the machine's physical devices, but it doesn't provide anything like a "virtual" USB device.

The only way an extension pack "affects" a virtual machine is by giving it greater functionality that the pure open-source version of VirtualBox can provide because of proprietary hardware or software issues.  Video drivers are another example.  The default open-source video driver in VirtualBox is more limited than the ones in the extension pack, just the same way the default video drivers for Ubuntu are more limited than the proprietary versions from ATI and NVIDIA.

---

