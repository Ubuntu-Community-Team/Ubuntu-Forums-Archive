---
title: "Linux windowed GPU passthrough"
date: 2015-11-12
forum: Virtualisation
---

### Post by simon89 on 2015-11-12
I've read that GPU passthrough on linux (ubuntu/mint) is possible with the correct types of hardware. I'm looking for a specific use case of passthrough and I'm wondering whether technology has advanced enough to allow for it to happen.


I have a linux mint host, and wanting a windows 8/10 guest. CPU/motherboard support vt-d (i7-5820k, asus x99-a). gpus are a pair of gtx970s. I want to:
1) Set up the guest so that it runs within a window on the host, thus allowing me to use something like a unity mode
2) Pass 1 of the GPUs through to the guest
3) When I shut down the guest VM, I want the passed through GPU to return to the host so I can use the pair of GPUs for compute/cuda heavy tasks


There are times where I'd like to game (hence the passthrough), but when I'm actually doing work I often need access to the cuda cores on both GPUs. A lot of the old threads I've read about this suggest that 1 card completely disappears from the host, is there a way to bring it back into action without a reboot?


Normally you'd need 2 monitors for this type of thing, plugging each into a separate GPU. But is it possible to use the second GPU to render a windowed VM within the host, instead of to a 2nd monitor?


Regarding windowed mode, I did see this on the virtualbox site, but I'm not sure if the VM is still windowed in this case: [https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough)


I've searched for this and have come up short, but having said that, most of the search results are quite a few years old so it doesn't speak to any advancements in technology since then. The only thing I've found is a video on youtube that suggests it might be possible as it looks like a passed through GPU on a VM running in windowed mode: [https://www.youtube.com/watch?v=XY1zDgCxARw](https://www.youtube.com/watch?v=XY1zDgCxARw)

---

### Post by darthrevan13 on 2015-12-13
What you're trying to do is almost impossible with the hardware you have or with the software that is available. I don't think you truly understand what GPU passthrough means.

To be able to passthrough a GPU your host system has to disregard it. If you let Linux initialize it then it's extremely hard, because of the way the kernel and drivers take control of it. You will most likely have a broken VM or a fatal error in the user space if you try to do this with a consumer graphics card. This is because the VM is secured in such a way that it should not be able to access anything on the host except for it's virtual container.

Because you are giving a virtual machine full access to to GPU (that's what passthrough means) your host can't use it, thus you can not have a window of the client in the host. VMWare Workstation emulates a video card thus something like Unity mode is possible because both system share the same card through the same output. Besides this VMWare Workstaion dose NOT support PCI passthough. The only product form VMWare to support this is ESXi.

If you want to see the display output of a VM with a display connected to a GPU that is passed through then you can through something like Remote Desktop, VNC or even Steam In-Home streaming.

The only solution to start and stop VM using the native performance of the GPU is to have a professional card (Quadro/FirePro). You can even run multiple virtual machines from one of those cards if you so desire.

If you are really interested in GPU passthrough I recommend reading [Alex Williamson's blog]("http://vfio.blogspot.ro/2015/05/vfio-gpu-how-to-series-part-1-hardware.html"). He goes into a lot of detail regarding the hardware and software of it including what I've mentioned above.

---

