---
title: "Re: AMDGPU not working anymore on 18.10"
date: 2018-11-22
forum: Virtualisation
---

### Post by DaveMiller on 2018-11-22
I have a zoostorm box with Radeon R5 Kaveri graphics onboard. I'd like to use more than 1024x768 but neither Settings/Screen nor xrandr see any higher.
I've installed  Ubuntu 18 LTS
The packages xserver-xorg-video-amdgpu 18.0.1-1 and libdrm-amdgpu1 are installed. (also -radeon packages)
There is a 10-amdgpu.conf

I have done dmesg | egrep 'drm|radeon' and it seems to be happy with VGA/DVIHDMI connectors, last line says "amdgpu kernel modesetting enabled"
The internet is full of references to all kinds of gibberish abut rebuilding the world.
Is there a simpler way to just give me more pixels??
I don't need and fancy graphics.

Yes, the monitor handles higher res. It's on a KVM with my elderly fedora boxes which do higher res.....
I've been around the block in computing and these days I just want stuff to work.
I want to love linux more but this stuff really makes it a pain for the general masses.

---

### Post by QIII on 2018-11-22
Moved to Virtualization from [this thread]("https://ubuntuforums.org/showthread.php?t=2406211").

Your issue appears to be associated with KVM and not a bare metal installation.  In that case, unless you are using GPU passthrough, the hardware GPU and driver don't matter to your VM.  KVM supplies a driver for using Spice.

[Here]("https://stafwag.github.io/blog/blog/2018/04/22/high-screen-resolution-on-a-kvm-virtual-machine-with-qxl/") is a fairly simple suggestion for getting higher resolution in QEMU/KVM.  I've never found it necessary to add a new modeline to xrandr.

---

