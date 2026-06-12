---
title: "mouse cursor disappears in kvm guest for some opengl/sdl? games"
date: 2021-08-11
forum: Virtualisation
---

### Post by monkeybrain20122 on 2021-08-11
So I am trying to test some games in my kvm guest (host = ubuntu 20.04, guest = ubuntu 21.04, on xorg) I just more or less randomly grabbed redecclipse from the the repo. When started the mouse cursor disappeared and I had to alt tab out of it and killed the game. Just to make sure it is not the game I installed it on the host and mouse worked with no issue. I tried with -usbdevice tablet and -usbdevice mouse with same result, no cursor. I use the option -vga virtio -display sdl,gl=on to enable virgl, so I reverted to QXL (though games likely won't be playable without virgl) but still get the same problem. The host has a Nvidia gtx1070 card.


Aside: I often find mouse behaves oddly with opengl (sdl?) games where the mouse cursor either gets stuck and becomes unresponsive or just disappears like here and there is no uniform way to get out of it except with alt-tab (some games have special settings to disable mouse grab but not all) but in this case it only affects the VM.

---

### Post by TheFu on 2021-08-11
You probably know much more about this than I do.

Don't most games demand direct access to the GPU?  I'm not on 20.04 for my VM hosts, but the SPICE QXL didn't support the level of OpenGL needed by most games. Has that changed?

The host GPU means nothing, unless you actually pass it through for exclusive access using IOMMU.

I tend to access desktops running inside a VM using SPICE over the network from a laptop using virt-viewer. The performance is pretty great, but not for most graphically intensive games.

---

### Post by monkeybrain20122 on 2021-08-11
> **TheFu said:**
> You probably know much more about this than I do.

Don't most games demand direct access to the GPU?  I'm not on 20.04 for my VM hosts, but the SPICE QXL didn't support the level of OpenGL needed by most games. Has that changed?


You are  correct that QXL doesn't support the level of OpenGL needed, but I have been playing with virgil3d-virtio-gpu (virlgl) it is amazing performance wise, I can play a lot of games with close to bare metal performance. e.g supertuxkart is so smooth that I can't tell I am in a VM with virlgl but it looks like a slide show with QXL.  With QXL unigine-heaven with low quality runs at ~7 fps, with virlgl I got ~80fps with ultra high quality, even very demanding program like x-plane 11 demo is very smooth.

So I tried a few games and a few guest distros the performance is consistent but this mouse problem for some games appears to have nothing to do with virlgl since QXL exhibits the same problem (though game is not playable with QXL, I could see the mouse has disappeared)

[https://www.collabora.com/news-and-blog/blog/2019/08/28/virglrenderer-state-of-virtualized-virtual-worlds/](https://www.collabora.com/news-and-blog/blog/2019/08/28/virglrenderer-state-of-virtualized-virtual-worlds/)
[https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration](https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration)
[https://www.dedoimedo.com/computers/qemu-virgil.html](https://www.dedoimedo.com/computers/qemu-virgil.html) (I don't think qemu-kvm package shipped with Ubuntu 20.04 works since it doesn't support sdl, but I don't want the snap so I compiled qemu myself)


Edited: I mentioned the host GPU because it appears that you get a black screen if you try to set up VM and enable opengl with virt-manager, at least I couldn't do it and I have to use the qemu cli, but with intel (and probably AMD) GPU you can set it up with just changing the display settings in virt-manager and it appears that has to do with Nvidia not playing well with opengl + gtk, so it needs to use opengl+sdl instead for virgl (and Ubuntu's qemu is not compiled with sdl)  so while the GPU doesn't get passed through, the host GPU being nvidia might have something to do with odd graphic and opengl artifacts in the guest because of the options used in running the vm.

---

### Post by MAFoElffen on 2021-08-13
You are using the compiled Qemu/KVM 6.x and I anm testing the Ubuntu packages of Qemu/KVM 6.0 on Dev 21.10...

Both off us figured ouyt that there was a problem with NVidia... And I get SDL in the Ubuntu packaged 6.0, but... that doesn't help with what you are describing. i also lose the mouse and sometimes the keyboard in some games. I think it might still be related to NVidia, but I'm not sure it may be related all to using SDL fixing it, because I still get those problems using SDL.

On some of those, I reconfigured whether the VM saw the mouse as PS2 or USB. Neither made a difference.

I just bought an extra mouse tonight, to see if passing through a mouse physically fixes that, but have been busy with another project before I get back to that. 

I am excited about LTS 22.04 and what I think Qemu/KVM will work out to be on that.

---

