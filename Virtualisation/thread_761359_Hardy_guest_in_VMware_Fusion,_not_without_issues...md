---
title: "Hardy guest in VMware Fusion, not without issues..."
date: 2008-04-21
forum: Virtualisation
---

### Post by hajk on 2008-04-21
I'm running VMware Fusion on my new 15" MacBook Pro, with 4GB RAM, and just installed the AMD64 Hardy Release Candidate in a VM (with 1.5GB RAM, 128MB video RAM, single virtual CPU). Most of the installation was straightforward, with the Ubuntu installer correctly identifying the virtual graphics system and loading the Xorg "vmware" video driver for it.

However, screen resolution seemed stuck at a disappointing 800x600, instead of the native 1440x900@60Hz. This required editing /etc/X11/xorg.conf with```

HorizSync     30.0 - 70.0
VertRefresh   50.0 - 75.0
```The installer had also loaded the "synaptic" touchpad driver, not recognizing that VMware itself takes care of that. As an aside: the Debian testing installer got these things right in a parallel install in another identical VM. 

VMware Tools, as downloaded from VMware, does not compile in Hardy or for any other 2.6.24 kernel. An alternative is to compile the "open-vm-source" package and to use the "open-vm-tools" package with it. Problem: the Hardy repositories don't have these packages (not even in universe/multiverse). But Debian testing does have these packages: just download the debs manually, in my case for AMD64. They install/compile perfectly in Hardy as well:```

sudo aptitude install debhelper dpatch
sudo dpkg -i open-vm-source........deb
sudo aptitude install module-assistant
sudo m-a prepare
sudo m-a a-i open-vm
sudo dpkg -i open-vm-tools.........deb
```and you can check with lsmod that some of the vm-modules are loaded, and that the VMware toolbar apears when hitting the top of the screen with the mouse.

The good news is that Hardy uses Xorg 1.4.0, which makes for smooth movements of windows across the virtual screen; Debian testing, on the other hand, still uses Xorg 1.3.x, where such movements are rather jerky. Naturally, the VMware virtual graphics system is only SVGA, not the Nvidia 8600GT of the underlying MacBook Pro, so don't expect dazzling graphics performance.   

Apart from the problems noted, I am well-pleased with this installation of Ubuntu Hardy. It feels snappy, behaves as if installed natively, and when I really need dazzling graphics performance, I just switch to Mac OS X where I also run things like VLC... Best of all: no worry about hardware incompatibilities of MacIntel hardware.

---

