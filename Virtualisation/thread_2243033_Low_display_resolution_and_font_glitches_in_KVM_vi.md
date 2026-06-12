---
title: "Low display resolution and font glitches in KVM virtual guests"
date: 2014-09-05
forum: Virtualisation
---

### Post by Remten on 2014-09-05
I haven't really seen this topic discussed much in recent posts on this board or elsewhere, so I will offer my experience in case anyone else is having trouble.

For running linux desktop guests in KVM hosted on a linux desktop and viewed using the Console built into virt-manager, when creating the guest you are offered the following video choices:
- default  (cirrus)
- cirrus
- vga
- vmga
- qxl
- xen

I initially tried running Linux Mint 17 Cinnamon guests, but there were multiple issues with the display -- characters were not fully displayed, some letters dropped, various other graphical artifacts that made the display unusable.

I found that Linux Mint 17 Mate and OpenSUSE 13.1 caused far fewer problems. So there is something peculiar about Cinnamon. (Even after trying additional setting, discussed in a moment, Cinnamon still would only run in "Software Rendering Mode," even though most of the other graphical issues were resolved.)

(1) [COLOR=#0000cd]The best display results by far were obtained with qxl[/COLOR], regardless of whether the display VNC server type was set to VNC or to spice. The number of display resolutions offered was very large, and cursor movements in the guest were snappy.

- **vmga** gave the second best results, with a wide range of resolution choices, and somewhat responsive cursor movements.

- **cirrus** gave a much more limited choice of display resolutions, although it did get at least to about 1024 x 768 IIRC. But there was a marked cursor lag in the guest.

- **vga** was horrible. The sole resolution type offered (in virt-manager) was 800x600. And cursor lag was very severe.

- **xen** wasn't supported at all. Choosing that setting resulted in a failure of the console display, so that loading of the iso via the gui couldn't proceed at all.

(2) [COLOR=#0000cd]Increasing the ram reserved for video above the default setting also improved display performance.[/COLOR] Before I made the increase, there were frequent freezes of the guest, or displays of screens with artifacts like dropped characters, and in some cases the guest would completely stop responding and have to be rebooting. As far as I have been able to tell, however, it is not possible to increase the video ram from within virt-manager itself. I made the changes by using virsh dumpxml, followed by editing the xml file and then re-defining the settings file with virsh.
For qxl (as opposed to vga or cirrus), you need to increase not only the ram but also the vram in the video settings.


virt-manager 0.9.5-1ubuntu3
qemu-kvm 2.0.0+dfsg-2ubuntu1.2
libvirt-bin 1.2.2-0ubuntu13.1.2

---

### Post by Doug S on 2014-09-06
Thanks for your posting. I had never heard of qxl as a video option before, so I tried it. It doesn't work properly for me, so I have gone back to vmvga.
 I do not use virt-manager, and only communicate with my VM's via VNC (well, ssh also).

---

### Post by Remten on 2014-09-07
I only posted that info in case someone else is experiencing similar problems. If things are already working well, I wouldn't change.

I did notice that qxl with the default video ram settings was a bit sluggish. It improved when the ram settings were increased.

Despite the improvements I obtained with the changes I mentioned in the previous post, I'm still having some video problems with Mint in both Cinnamon (especially) and Mate. Trying to load the Youtube main page, for example, freezes the guest.

---

