---
title: "Xen GPU passthrough"
date: 2012-08-26
forum: Virtualisation
---

### Post by JacobBrown1000 on 2012-08-26
Hay anyone know if the Xen GPU passthrough or HDX works in the Xen Hypervisor kernel and if this kernel can be compiled to use Ubuntu as the host.

---

### Post by Cheesemill on 2012-08-26
Have you read the documentation?
[http://wiki.xen.org/wiki/Xen_PCI_Passthrough](http://wiki.xen.org/wiki/Xen_PCI_Passthrough)

PCI passthrough is a standard feature of Xen, so should work fine with a standard Xen setup.

The first question is do your CPU and motherboard actually support PCI passthrough?
Your CPU needs to either have VT-d (Intel) or IOMMU (AMD) extensions as well as a motherboard that supports them.

---

### Post by JacobBrown1000 on 2012-08-26
I have a dual procsessor quad core Intel server, a Acer aspire laptop with a core two from Intel and a Zotac with a quad core Intel. All have NVIDEA graphics cards. I don't know if they sopport PCI passthrough ore not.

---

### Post by Cheesemill on 2012-08-26
Look up your specific Intel processors on the Intel Ark site and see if they support the VT-d extension.
[http://ark.intel.com/](http://ark.intel.com/)

Then look up your specific motherboards on the relevant manufacturers site and see if they support the VT-d extension.

I'm pretty sure that PCI passthrough is only supported on the later Xeon processors though.

---

### Post by JacobBrown1000 on 2012-08-27
The server looks OK for VT-D but not the others. Do I have any options? I was hoping to install Windows for some games that don't work on Wine, I have heard of some virtualization software's that use the CPU as a GPU rather then pass through to real hardware. Is that an option with Xen? I know the passthrough offers more transparency to hardware and faster speed but by how much compared to others?

And thanks for your promptness by the way.

---

