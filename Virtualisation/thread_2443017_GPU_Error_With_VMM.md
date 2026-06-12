---
title: "GPU Error With VMM"
date: 2020-05-10
forum: Virtualisation
---

### Post by rookie2987 on 2020-05-10
Hello, I'm somewhat new to linux, this is my first main PC which runs linux,

I have made a simple virtual windows machine in VMM with KVM. Anytime I add my GPU to this by adding a PCI host device, when I start the virtual system my host machine becomes mainly unresponsive. I have also found that running game on my RTX 2060 doesn't give the expected performance on my host machine. I'm thinking it may be an error with my host machine and the GPU and not the GPU and the virtual machine.

Any help will be appreciated,
- rookie2987

---

### Post by TheFu on 2020-05-10
How many GPUs does the host system have?

When we use GPU passthru, that leaves the hostOS without a GPU.  That's bad.

---

### Post by rookie2987 on 2020-05-13
I only have one GPU but do not have a GPU that could run games on the VM neither the money for one. My main GPU still does not run games to the performance I expect either

---

### Post by CelticWarrior on 2020-05-13
> **rookie2987 said:**
> I only have one GPU but do not have a GPU that could run games on the VM neither the money for one. My main GPU still does not run games to the performance I expect either

Well, then let me rephrase this nice piece of advice > When we use GPU passthru, that leaves the hostOS without a GPU.  That's bad. 				 for you: You need TWO GPUs for that!

---

### Post by TheFu on 2020-05-13
> **CelticWarrior said:**
> Well, then let me rephrase this nice piece of advice  for you: You need TWO GPUs for that!

Exactly.  People can get the iGPU on their Intel CPUs for the hostOS and their hot new $450+ AMD/Nvidia GPU to passthru to 1 guest VM.

Passthru means exclusive access to only 1 OS. That OS can be either the host or the guest, but not both.

Intel has been working on a way to share iGPUs for multiple VMs.  gVT 
[https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide)  It never seems to be production ready. It is intel GPU-only.

---

