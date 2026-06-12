---
title: "GPU passthrough VMM kills second monitor."
date: 2022-06-12
forum: Virtualisation
---

### Post by rmjohnson144 on 2022-06-12
OK, I have setup my rig with dual monitor and dual graphics (iGPU (5700G) and dGPU (5500 XT))

I then passthrough the 5500 XT and use the 5700G for linux.

But when I do the vfio stuff and reboot, my 5700 XT monitor goes blank.  Which seems to make sense as I have reserved for VM only.

But when I set up the VM and use the 5500 XT GPU and Audio, then launch the VM, I get nothing on the second monitor and no VM pops up at all.

I even did it a second time and I installed virtual manager and made a windows VM first. before doing the GPU passthrough VFIO stuff. to make sure windows wasn't the issue, as it worked flawlessly, except it was stuck in 800x600 resolution.

I've used several guides and followed this one on this try.  even though he had an nvidia card and I skipped the virsh setup for the nvidia gpu.

GPU passthrough guide for Ubuntu 20.04 by Pavol Elsig
[https://www.youtube.com/watch?v=tDMoEvf8Q18](https://www.youtube.com/watch?v=tDMoEvf8Q18)

I'd appreciate any help I can get, I am a noob and started this project just after x-mass, so it has been frustrating at the least.

My current rig: GigaByte B550 Aorus Elite AX V2  * Ryzen 5700g * 32GB (4x8 G.Skill F4-3200C16D-16GIS) * ASRock 5500 XT * Ubuntu 22.04 64-bit

---

