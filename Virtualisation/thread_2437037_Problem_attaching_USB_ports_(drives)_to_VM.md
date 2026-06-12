---
title: "Problem attaching USB ports (drives) to VM"
date: 2020-02-17
forum: Virtualisation
---

### Post by mn1247 on 2020-02-17
I am running KVM on Ubuntu 18.04 Desktop.  The physical machine has eight USB ports, of which I have three connected to drives.  

I'm having trouble connecting the USB drives to a VM using libvirt/virt-manager.  When I try to add an additional USB through "Add Hardware" in the virt-manager GUI,  I get a message saying "Error adding device: Internal error: No free USB ports".  But, I am not even close to using all the USB ports of the physical machine, so I'm not sure why additional ports can't be added.

Where am I going wrong?  What is the correct way to set this up?

Thanks
Eric

---

