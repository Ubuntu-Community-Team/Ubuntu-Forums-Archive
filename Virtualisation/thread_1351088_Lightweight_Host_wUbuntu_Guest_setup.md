---
title: "Lightweight Host w/Ubuntu Guest setup?"
date: 2009-12-10
forum: Virtualisation
---

### Post by kendoori on 2009-12-10
I'm having some issues with my Squeezebox server that's running on an atom-based MSI Wind box, so am ready to rebuild. It occurred to me that building  my setup as a VM would be worth considering. I use VirtualBox extensively, so I'm hoping to get some suggestions on an approach that would have a very lightweight Host setup that automatically runs the VM upon startup. My hardware has 2 GB RAM and 1.6ghz processor. Squeezebox is pretty lightweight, and runs fine on that hardware right now. Other than acting as a limited use file-based NAS and print server, the box would be doing nothing other than running Squeezebox.

---

### Post by BT1 on 2009-12-10
> **kendoori said:**
> I'm having some issues with my Squeezebox server that's running on an atom-based MSI Wind box, so am ready to rebuild. It occurred to me that building my setup as a VM would be worth considering. I use VirtualBox extensively, so I'm hoping to get some suggestions on an approach that would have a very lightweight Host setup that automatically runs the VM upon startup. My hardware has 2 GB RAM and 1.6ghz processor. Squeezebox is pretty lightweight, and runs fine on that hardware right now. Other than acting as a limited use file-based NAS and print server, the box would be doing nothing other than running Squeezebox.
 
I've said this a few times, but if you aren't familiar with it, you should look into linux kernel customization. There's a nifty tutorial here on this site (sorry for not linking it here because I'm at work lol) that explains the process pretty well. The program is KernelCheck and it has a sort of GUI that lets you fully customize your kernel to fit your system specs. I customized my ubuntu 32 kernel for my [AcerOne 1G Ram 1.6GH Processor] netbook and it runs 30-40% faster by default. If you want to run buntu, you should look into that. "Compiling" may seem like a scary word, but it was so easy my mom (literally) did it in 30 minutes (picking her settings, the part where it compiles and installs the kernel takes a bit longer lol) and she has little to no experience with advanced computer stuff.
 
VirtualBox also has a guide on how to compile the program which has a few tweaks available too. If you want *buntu as your base system, then both compiles are a good idea. You could more than likely compile the kernels in your VirtualBox installs to run even faster... but I haven't tried that yet lol.

---

### Post by Druke on 2009-12-10
sounds liek you should make the computer a full vm server, even the NAS and print server stuff could be two other light vms.

that way if you ever want to upgarde the system, you just have to migrate the vms to the new computer and continue like nothing changed.

as for making an install that just installs vm software and networking stuff, aside from looking into compiling your kernal yourself, you could look into [Jeos]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")

jeos's kernel is fine tuned to run as a vm, but you could compile your own and run it within the jeos system.

If you are wanting advice on running/building the vms, I'd be glad to help you. (I've currently got an old laptop running as a kvm server running 3 server vms [torrentflux,wordpress, and a shell box that I use for irssi] .)

---

