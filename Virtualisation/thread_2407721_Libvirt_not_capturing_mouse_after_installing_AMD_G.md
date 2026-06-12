---
title: "Libvirt not capturing mouse after installing AMD GPU Drivers"
date: 2018-12-08
forum: Virtualisation
---

### Post by ytterbious on 2018-12-08
I have successfully set up GPU passthrough on my VM, but for some reason, when I install the GPU drivers on my 64-bit Win 10 guest OS, my mouse isn't captured at all. Whenever I mouse over the viewer, the cursor disappears completely and I cannot click in the guest at all. The GPU drivers are for a R9 290 GPU, driver version 18.12.1.1-dec5 .

---

### Post by springshades on 2018-12-10
I think there is some important information missing from your description. If you followed the standard KVM method of GPU passthrough, your Linux video should be going out through one video card and your Windows video should be going out to another. You probably have one of the following situations: (1) 2 monitors (2) 1 monitor with 2 input channels (3) Looking Glass (4) the old Qemu way of doing a sort of remote desktop thing. In the first two cases, you shouldn't have a "viewer" of any type to click into. If you're using one of the other methods, it's entirely possible that they are the cause of the problem. In particular, I don't know if the remote desktop method was ever very stable. I've only ever seen it in older youtube videos that seemed like more of a proof of concept. It's hard to help without knowing which set up you're using.

On the other hand, if you're doing GPU passthrough the standard way and you're still seeing the OS in a viewer, there is a chance that you don't actually have GPU passthrough working in the first place.

---

