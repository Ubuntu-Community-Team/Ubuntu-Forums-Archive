---
title: "GPU passthrough &amp; error 12? Ubuntu 18.04 host, Windows 7 guest, KVM."
date: 2019-03-05
forum: Virtualisation
---

### Post by watashiwaaustin on 2019-03-05
I've been using this guide to setup GPU passthrough in KVM with Virt-manager: [https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/](https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/)

It has worked well and the GPU is recognized by the windows guest. I was able to use NVIDIA Geforce Experience to autodetect and update my drivers.

However, the devices section of settings shows Error Code 12: Not enough free resources. If I try to repair it, Windows suggests I may have two devices using the same PCI Bus. This is when using the spice graphics console. If I remove that hardware and only leave the card I get no video at all.

My hardware is a Gigabyte z97mx-gaming 5 motherboard, a NVIDIA Geforce GTX 760 graphics card, and an Intel i5 4690k cpu.

Is anybody familiar with this situation? Or does anybody know where I might be able to get help with it?

---

### Post by auroraskyes on 2019-05-19
My system has a very similar setup that was giving me the same code 12 error. I have been able to able to get it working with the following setting in virt-manager:
CPUs -> Model -> Haswell-noTSX-IBRS
Using the "Copy host CPU configuration" appeared to give me issues.

---

