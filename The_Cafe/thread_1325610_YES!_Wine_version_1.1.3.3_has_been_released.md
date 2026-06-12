---
title: "YES! Wine version 1.1.3.3 has been released"
date: 2009-11-13
forum: The Cafe
---

### Post by Goldline on 2009-11-13
:p

1.1.3.3 list of changes:

What's new in this release (see below for details):
  - Gecko now installed at wineprefix creation time.
  - Better support for certificates in crypt32.
  - Improved sound support in mciwave.
  - Some more Direct3D 10 functions.
  - Many cleanups for issues spotted by Valgrind.
  - Various bug fixes.

FOR THE FULL LIST OF CHANGES PLEASE VISIT:
[http://www.winehq.org/announce/1.1.33](http://www.winehq.org/announce/1.1.33)

---

### Post by bodhi.zazen on 2009-11-13
Moved to the cafe.

Is there not a new "version" of wine released every two weeks (there was the last time I looked).

---

### Post by blueshiftoverwatch on 2009-11-13
Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

---

### Post by SunnyRabbiera on 2009-11-13
> **blueshiftoverwatch said:**
> Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

Well I can give a good reason, memory load, as virtual machines need a certain amount of memory, linux needs a certain amount of memory, and windows needs a crapload of memory.

---

### Post by perce on 2009-11-13
> **blueshiftoverwatch said:**
> Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

Because it doesn't need a Windows licence

---

### Post by chris200x9 on 2009-11-13
> **blueshiftoverwatch said:**
> Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

because it's not emulating windows?

---

### Post by AllRadioisDead on 2009-11-13
Nothing to be too excited about.. it happens every 2 weeks.

---

### Post by blueshiftoverwatch on 2009-11-13
> **chris200x9 said:**
> because it's not emulating windows?
How exactly is a compatibility layer different from an emulator?

---

### Post by kavon89 on 2009-11-13
> **blueshiftoverwatch said:**
> Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

Does your processor have virtualization extensions?

---

### Post by toupeiro on 2009-11-13
> **blueshiftoverwatch said:**
> How exactly is a compatibility layer different from an emulator?

Emulation, by function, generally has to mimic processor instruction (e.g. DOSBox, MAME, UltraUAE etc etc, SNEX9x, etc etc.)  Wine does not need to perform CPU emulation, and interprets the native instructions delivered to the Host OS.  Thus, no emulation is taking place.  simply, an x86 compatibility layer that can run within the same environment as the parent environment.

---

### Post by oldgeekster on 2009-11-13
Let me know when they have overcome the problem detecting usb devices and I will be impressed....

---

### Post by Matthewthegreat on 2009-11-13
> **blueshiftoverwatch said:**
> Why is WINE faster/better at running Windows apps than Windows running in Virtualbox?

Have you tried running 3D games in Virtualbox? ;)

---

### Post by NickJones on 2009-11-13
VirtualBox is the equivalent of running over VNC, Wine adds a layer of compatibility to decode the ".exe" into a file Linux understands and can run.

---

### Post by blueshiftoverwatch on 2009-11-13
> **kavon89 said:**
> Does your processor have virtualization extensions?
Yes.

---

### Post by MaxIBoy on 2009-11-13
New WINE releases come out every two weeks. I'd be surprised if there wasn't a release today.












I think the following is correct, but if I'm wrong, don't hesitate to let me know...




WINE is a "compatibility layer." With WINE, the Windows .EXEs run natively as Linux programs. It just uses a different dynamic linker, and system calls are "caught" by WINE and translated to ones the Linux kernel can understand. If a Windows program uses no System calls, it will start up slower but after that run at native or faster speeds under WINE.


Virtual machines still run "on the bare metal" of the host CPU, but programs inside virtual machines cannot use the host OS, instead they see a "virtual" computer made out of parts of the resources of the host. Since the programs you run in a VM have no access to the host OS, so a guest OS must run within the VM for the VM to be useful. So when running Windows programs in VirtualBox, you have the overhead of the Linux OS, then the overhead of the VM, then the overhead of Windows itself.


Emulators are distinct from VMs and Compatibility Layers. They keep an entire software simulation of a CPU with its own RAM and so on. 


Note that in some cases, a VM may need to *use* an emulator internally; this is done if the host OS uses a different architecture than the guest. For example, when running Windows in a VM on an old PPC Macintosh, the VM sometimes needs to emulate an x86 CPU. On the other hand, more advanced VMs will "translate" the machine code accross CPU architectures *and then store the translated version for future use*, in which case it's not using an emulator. I think VirtualBox does this.

---

### Post by toupeiro on 2009-11-13
> **oldgeekster said:**
> Let me know when they have overcome the problem detecting usb devices and I will be impressed....

Which USB devices?  I've had it properly recognize flash drives, web cams, smart card readers and other things which were all USB.

---

