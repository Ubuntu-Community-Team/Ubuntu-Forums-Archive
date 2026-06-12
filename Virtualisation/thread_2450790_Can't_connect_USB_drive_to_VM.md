---
title: "Can't connect USB drive to VM"
date: 2020-09-21
forum: Virtualisation
---

### Post by unicorn989 on 2020-09-21
Hello

I am running KVM on Ubuntu 18.04 Desktop, The physical machine has  three USB ports. But I can't connect USB drive to a VM. When I tried "Add  Hardware", it said "Error adding  device: Internal error: No free USB ports". How can I fix this?

Thanks

---

### Post by Dennis N on 2020-09-21
Start the VM guest. Plug in the USB. Leave full screen in order to access the VM window menu (where it has 'File', 'Virtual Machine' 'View' and 'Send Key'). 
Choose **Virtual Machine > Redirect USB Device > Check the desired USB** and the USB should become accessible from the VM guest.

---

