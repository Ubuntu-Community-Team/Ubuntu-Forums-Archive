---
title: "Virtual Machines and drivers"
date: 2017-12-10
forum: Virtualisation
---

### Post by chrislw324 on 2017-12-10
In the computer I'm just about done building, i'm going to be running Windows 10 Pro and Ubuntu on top of that. Will I need to reinstall all the drivers for my keyboard, mouse, and other components for Ubuntu? If so, since I'll have them installed in Windows, is there a quicker way to install them other than manually installing each one with the cds?

---

### Post by deadflowr on 2017-12-10
*Thread moved to **Virtualization** *

> Will I need to reinstall all the drivers for my keyboard, mouse, and other components for Ubuntu?
No, Ubuntu has drivers built into it.

What virtualization program are you going to use?
I ask because different virtual machines have different added sub packages that provide enhancements to give better overall performance.

---

### Post by chrislw324 on 2017-12-10
I'm going to use virtual box

---

### Post by deadflowr on 2017-12-10
You can install guest additions: [https://help.ubuntu.com/community/VirtualBox/GuestAdditions]("https://help.ubuntu.com/community/VirtualBox/GuestAdditions")
And extension packs: [https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")
For some added enhancements and functionality.

---

### Post by &amp;KyT$0P# on 2017-12-10
> **chrislw324 said:**
> I'm going to use virtual box
You only need install the VirtualBox Guest Additions in your virtual Ubuntu.  In the menus on top of the running VM, go to Devices > Insert Guest Additions CD Image.  If you are not prompted to run something, open a Terminal in the CD's directory and run
```
sudo ./VBoxLinuxAdditions.run
```

* oops, collided posting with deadflowr.  Extension Pack is something you would install in your VirtualBox on your Windows host, not inside the VM.

---

### Post by ian-weisser on 2017-12-10
> **chrislw324 said:**
>  Will I need to reinstall all the drivers for my keyboard, mouse, and other components for Ubuntu?

No.
A Guest does not *share* hardware with the Host.
The Host allocates resources. The Host VM application uses the Host drivers on the Host OS.
The Guest sees a generic set of virtual "hardware" presented by the Host VM application. "generic" in this case means "does not need additional drivers".
This requires a bit of processing overhead, and is a big part of the difference between a full Virtual Machine and a mere Container.

Example: You may use a special Foo 1.35 mega-ethernet card that requires special drivers.
Your Windows Host has the special drivers installed. All your Windows applications can use special mega-ethernet features.
Your Ubuntu Guest sees only a Generic Ethernet Port. Your Guest can happily use default networking, but generally cannot use special features...unless the VM application is programmed to present them to the guest.

Some of that pass-through is part of Vbox Guest Additions...but all hardware interface is still handled by the Host OS, not Ubuntu.

---

