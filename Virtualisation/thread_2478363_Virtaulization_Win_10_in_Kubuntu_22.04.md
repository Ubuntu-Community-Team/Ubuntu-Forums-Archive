---
title: "Virtaulization Win 10 in Kubuntu 22.04"
date: 2022-08-24
forum: Virtualisation
---

### Post by kunzhut on 2022-08-24
[COLOR=#232629][FONT=-apple-system]Good afternoon!

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I have Kubuntu 22.04 on good hardware: i7-12700f, GeForce 3060 Ti 8 Gb, 32 Gb RAM[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The question is: is it possible to install some kind of VM with Windows 10 so that the video card is fully used in it and that, in terms of ease of use, it would end up like with VirtualBox: I launched Windows on the neighboring desktop into Kubuntu when I needed to switch there for a while and returned to my usual working env.?[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-24
You'll need 2 GPUs, so that 1 can be passed through to Windows for exclusive use.  If your Core i7 has an iGPU, then you are good.  Just need to follow the 10 pages of setup to get it working.  I don't know if virtualbox can do GPU passthru, but I know that KVM and Xen can. There are lots of how-to guides.  "core i7 gt 3060 kvm passthru for Windows" is the google search that I used to find some.

None of my systems have 2 GPUs, so I've never attempted it.

There are always new video capabilities being worked on to make virtual machine GPU performance better. For most uses, the default SPICE protocol is more than sufficient, but for gaming it most definitely is not.     "virtio-gpu" is the google search term.  [https://www.phoronix.com/news/VirtIO-GPU-QEMU-2021-H1-State](https://www.phoronix.com/news/VirtIO-GPU-QEMU-2021-H1-State) is a short situation report. Good overview for that method.
[https://www.phoronix.com/news/Linux-6.0-VirtIO](https://www.phoronix.com/news/Linux-6.0-VirtIO) has the changes in the 6.x kernels, which aren't used in Ubuntu yet.

It is good that you have 22.04, since video performance improvements are constant.

Lots of other people here have direct experience with this. Hopefully, they will post.

---

