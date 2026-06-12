---
title: "Maverick really slow with decent virtual hardware"
date: 2010-10-26
forum: Virtualisation
---

### Post by wirate on 2010-10-26
My host OS is Windows 7. I have a Core i3 processor and on VirtualBox, I have given Maverick 1 GB of RAM, 1 processor (dont know what that means), 128 MB of video memory, 3d acceleration enabled and still it is really really slow. Any help

And I have installed guest additions.

---

### Post by dcstar on 2010-10-27
> **wirate said:**
> My host OS is Windows 7. I have a Core i3 processor and on VirtualBox, I have given Maverick 1 GB of RAM, 1 processor (dont know what that means), 128 MB of video memory, 3d acceleration enabled and still it is really really slow. Any help

And I have installed guest additions.

Do you have Virtualization enabled in the BIOS?

---

### Post by wirate on 2010-10-27
Dont know. How do I do that?

---

### Post by wirate on 2010-10-27
Virtualization enabled. Faster... but still compiz cannot be enabled

---

### Post by Hatsune Miku on 2010-10-27
> **wirate said:**
> Virtualization enabled. Faster... but still compiz cannot be enabled

Hey! I Think i know whats going on, a i3 Processor only has 2 Cores, the reason there are 4 is because of something called hyper threading, it kinda splits the cores in half. So Enable 2 CPUs for ubuntu, And compiz cannot be enabled because Virtual Box does not support OpenGL 2.0+ because of driver development. Hope this helps!

---

