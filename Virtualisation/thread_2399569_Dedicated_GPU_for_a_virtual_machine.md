---
title: "Dedicated GPU for a virtual machine"
date: 2018-08-27
forum: Virtualisation
---

### Post by Rainersxd on 2018-08-27
Greetings!

My monitor, 3840x2160 . My previous GPU died ( AMD Radeon HD 7870) but I don't think it would have been the best weapon for this system anyway. I am forced to go with the integrated GPU right now, and to not make the computer suffer too much I am using HDMI with 30hz refresh rate right now.
I can put a card in this system but the problem is that it supports only up to qHD so here I am asking this question:
Can I have vmware virtual machine in which I say that this GPU is only for it? In this scenario I'd plug the monitor to the integrated GPU via DisplayPort so I can have 60hz refresh rate, put up a virtual machine with a qHD resolution and make the card work only for this virtual machine.

Thank you for stepping by!
Best regards,
rainersxd

---

### Post by slickymaster on 2018-08-27
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2018-08-27
It depends.
The motherboard matters.
The GPU matters.
The hypervisor matters.  "vmware" is too vague to know.
The way the kernel is compiled and options chosen matter.
While not as hard as it was 5 yrs ago, it is still a non-trivial effort.

It is best to search by the current motherboard for a how-to guide, then use identical GPU (or extremely well supported GPU) with your solution.

---

### Post by Rainersxd on 2018-08-27
Pardon me for not being clear here.
What I was looking for is: you can remove USB devices from the host and connect them to the guest system, can you do the same with the hardware?
I was expecting the same way you can add a physical disk or a virtual one you can add hardware. I am not sure about this and that's why I am asking.

---

### Post by TheFu on 2018-08-27
> **Rainersxd said:**
> Pardon me for not being clear here.
What I was looking for is: you can remove USB devices from the host and connect them to the guest system, can you do the same with the hardware?
I was expecting the same way you can add a physical disk or a virtual one you can add hardware. I am not sure about this and that's why I am asking.

It depends. What is this hardware you hope to add?  Some USB stuff works, but you'll need to setup USB passthru.  Other USB stuff doesn't work.

But you were asking about GPUs, I thought based on the thread title, which is why I concentrated on that answer. It depends.

---

### Post by Rainersxd on 2018-08-27
It's GTX 560ti here. I don't know. I hoped that it's as easy as that, you have the settings and you check that you want to use this hardware.

---

### Post by TheFu on 2018-08-27
> **Rainersxd said:**
> It's GTX 560ti here. I don't know. I hoped that it's as easy as that, you have the settings and you check that you want to use this hardware.

You'd need to talk to vmware about that. They will ask which product, since they make 6 different hypervisor products, each with different capabilities for different purposes.

For Xen or KVM, it isn't a checkbox. 

Google found this for ESXi : [https://forums.servethehome.com/index.php?threads/help-esxi-6-5u1-passthrough-gtx560ti-successfully-but-fail-on.19089/](https://forums.servethehome.com/index.php?threads/help-esxi-6-5u1-passthrough-gtx560ti-successfully-but-fail-on.19089/)
and
[https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough](https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough) which should help you figure out which version of vmware you actually have.

Regardless, the host machine needs to have a GPU connected - 2 video cards are necessary for exclusive use by the host and the VM.

---

### Post by Rainersxd on 2018-08-28
As I mentioned, I will have the integrated GPU to handle the system itself but I want the GTX 560ti to be exclusively for the guest system.
Also I should mention that GPU passthrough is something completely different than I have. I can't connect this gpu directly to my system: it won't work.

---

