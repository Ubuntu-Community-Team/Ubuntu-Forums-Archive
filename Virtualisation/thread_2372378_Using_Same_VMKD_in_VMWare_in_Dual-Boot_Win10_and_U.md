---
title: "Using Same VMKD in VMWare in Dual-Boot Win10 and Ubuntu Setup"
date: 2017-09-24
forum: Virtualisation
---

### Post by jaydub868 on 2017-09-24
I have my PC setup in a dual boot configuration with Win10 and Ubuntu running natively.  I also want to create one Win10 VMDK and one Ubuntu VMDK, so that when I'm natively in either OS, I can use VMware Player (free) to access either VMDK.  The virtual machine folder and VMDK's are to be stored on a separate disk to provide common access and to provide better responsiveness.  This seems to be a challenge in VMware Player as the VMDK disc image is housed in the same folder as configuration files.  So, if I create a working directory in Win10 of F:/VirtualMachines/Ubuntu to create an Ubuntu VMDK, then I can't use that location to establish the working directory in the Ubuntu host. When I do so, VMware says it can't use that address because there are files in it.  Do I need Workstation Pro to do this?

---

### Post by jaydub868 on 2017-09-24
I see the error I was making.  Once the VMDK is established in one host, in the other host I don't "create", I "open" the existing VMDK.  Kind of basic.

---

### Post by ajgreeny on 2017-09-24
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

