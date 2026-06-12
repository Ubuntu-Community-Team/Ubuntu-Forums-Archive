---
title: "Cycles blender rendering completely black"
date: 2024-08-23
forum: Ubuntu/Debian BASED
---

### Post by dorian0604 on 2024-08-23
So I've recently tried Ubuntu and Pop and I'm just getting my feet wet. Right now I'm on the latest Pop version and decided I'd try blender for a project. I've modelled everything and done the preparations to render as I've done it before (on win11). Cuda is working and I've put the system to gpu compute with experimental settings. When I hit render image it's 1) painfully slow despite me having an RTX 3070ti and ryzen 7 5700 g cpu, and 2) in the first seconds of render I see my scene with a messed up aspect ratio and then the render is completely black. I've checked and despite neofetch not displaying the name of my gpu the other (idk the name) command shows that my gpu is on and working (well I know fs because I play war thunder on max setting so it def. is working). Could it be a driver problem or something with the software? I've never ran into this.

---

### Post by currentshaft on 2024-08-23
What does "nvidia-smi" report?

---

### Post by dorian0604 on 2024-08-24
it now says my gpu is on (well not really apparently I have to switch it to  "on" on every boot. how do I make it to just stay on??)

---

### Post by currentshaft on 2024-08-24
It should never be "off". If it is, run "sudo dmesg" to see why it fell off the bus.

---

### Post by dorian0604 on 2024-08-24
I saw error 71, and this: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID (ID here)] Failed to grab modeset ownership
and after refreshing (ie reinstalling) Pop these exact problems stayed idk why. I feel like I shouldn't be having this problem sice I'm using the official nvidia version

---

