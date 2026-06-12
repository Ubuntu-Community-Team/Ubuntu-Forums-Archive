---
title: "Do you really need 'x86 virtualization'?"
date: 2009-11-19
forum: Virtualisation
---

### Post by Vostrocity on 2009-11-19
I'm very new to virtualization. My question is: do you need [this]("http://en.wikipedia.org/wiki/X86_virtualization")? As you can [see]("http://ark.intel.com/ProductCollection.aspx?familyID=26547"), a good fraction of mainstream processors doesn't support this. The weird thing is that I don't see this aspect listed as a system requirement on Sun's site nor do Virtualbox tutorials say anything.

---

### Post by Aubergines on 2009-11-19
You mean the hardware AMD-V and Intel VT extensions? It's not absolutely essential. Virtualisation comes in many forms, you have operating system-level virtualisation like OpenVZ where it runs multiple linuxes within containers (think chroot) but they all share a common kernel.
Then you have para virtualisation where the guest OS knows it's running within a virtual environment, however it requires heavy patching. Xen is a para virtualisation product.
Yet another form is full virtualisation where the guest OS is not patched, does not know it's a virtual machine. The guest OS executes on the VM exactly as it would on a physical system. Vmware and Virtualbox can do this.

There's advantages and disadvantages in all forms. To run full virtualisation AMD-V and Intel VT extensions are required.

---

### Post by Vostrocity on 2009-11-19
Ok my Core 2 Duo doesn't happen to have Intel VT, so where should I start? I was planning to have Windows 7 inside Virtualbox running over Ubuntu, but I might have to change that.

---

### Post by insane_alien on 2009-11-21
you should  still be able to install and run it fine. spped might not be as fast as otherwise though.

---

