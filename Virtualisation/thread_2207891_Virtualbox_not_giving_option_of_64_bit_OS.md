---
title: "Virtualbox not giving option of 64 bit OS"
date: 2014-02-25
forum: Virtualisation
---

### Post by aspidistra on 2014-02-25
Recently got virtualbox image creation with option for '64 bit' or '32 bit'

now it's just 'linux', 'ubuntu'

you try to install the 64bit image iso (xubuntu 12.04 64 bit in this case)

and upon that - get 64 bit installation cannot be performed on 32 bit architecture

Tried with the virtualbox from the sun website and the one from synaptic

---

### Post by Bucky Ball on 2014-02-25
*Thread moved to **Virtualisation**.*

---

### Post by SeijiSensei on 2014-02-25
Are you trying to install a preconfigured VM as a guest on an existing VirtualBox host?  What is the host's architecture?  Why not just install from the regular [Xubuntu ISO image]("http://cdimage.ubuntu.com/xubuntu/releases/precise/release/xubuntu-12.04.4-desktop-i386.iso")?

You cannot install 64-bit VMs into a VirtualBox host running on a 32-bit platform.  You can only install 32-bit guests.

---

### Post by aspidistra on 2014-02-25
> **SeijiSensei said:**
> Are you trying to install a preconfigured VM as a guest on an existing VirtualBox host?  What is the host's architecture?  Why not just install from the regular [Xubuntu ISO image]("http://cdimage.ubuntu.com/xubuntu/releases/precise/release/xubuntu-12.04.4-desktop-i386.iso")?

You cannot install 64-bit VMs into a VirtualBox host running on a 32-bit platform.  You can only install 32-bit guests.

I am running a 64 bit xubuntu 12.04

I use the sun virtualbox 4.3.6

It won't allow me to use the xubuntu iso image "xubuntu-12.04.4-desktop-amd64.iso"

it says cannot run 64 bit system on 32 bit virtualbox

previously you had two options after selecting linux (when setting up a virtualbox machine to subsequently mount the iso onto) 

"64 bit" or "32 bit" now it's just select 'linux' and 'ubuntu' .. was looking for a way to change to 64 bit in the settings - can't see any

---

### Post by QIII on 2014-02-25
Hello!

Have you made sure AMD-v (if you have an AMD processor) or VT-x (if you have an Intel processor) is enabled in your BIOS? Your Virtualbox will need that to be set to virtualize a 64 bit OS.

---

### Post by CharlesA on 2014-02-26
> **QIII said:**
> Hello!

Have you made sure AMD-v (if you have an AMD processor) or VT-x (if you have an Intel processor) is enabled in your BIOS? Your Virtualbox will need that to be set to virtualize a 64 bit OS.

I ran into this recently at work where a 64-bit host OS running virtualbox (or hyperv) couldn't run a 64-bit guest because the BIOS didn't allow you to enable VT-x/AMD-v.

Not fun.

---

### Post by aspidistra on 2014-02-26
ok .. suspected it was something in the bios

will try and report back at some stage

---

### Post by Pi_Ke on 2014-11-16
By default, 64 bit OS is not supported on VritualBox. To install 64 bit OS, you need to have a 64 bit processor and it should support hardware virtualization. 
Then you can go to BIOS and enable the hardware virtualization. For details, you can refer to [http://www.pixelstech.net/article/1415440305-Want-to-install-64-bit-OS-on-VirtualBox](http://www.pixelstech.net/article/1415440305-Want-to-install-64-bit-OS-on-VirtualBox)

---

