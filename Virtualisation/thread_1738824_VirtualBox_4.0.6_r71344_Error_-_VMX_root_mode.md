---
title: "VirtualBox 4.0.6 r71344 Error - VMX root mode"
date: 2011-04-25
forum: Virtualisation
---

### Post by jaezcurra on 2011-04-25
Hi,  I have just upgraded to VB 4.0.6 (Ubuntu 10.04 64 bits) and each time that I try to launch either Ubuntu 11.04 Beta 2 or Windows XP I get this Error message: "VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE)" (see attached files).

I reinstalled VB from their website and same problem.

Any suggestion?

Everything was working great until the upgrade :(

---

### Post by CharlesA on 2011-04-25
Did you have KVM installed before?

---

### Post by jaezcurra on 2011-04-25
Cannot answer.  Just upgraded as I always did.  The fact is that VB does not work as it used to do.

---

### Post by CharlesA on 2011-04-25
Search for kvm in synaptic or software center and see if it's installed.

---

### Post by jaezcurra on 2011-04-25
Thanks for your quick reply.  I will have to wait until tomorrow morning, when I arrive at work (it's about my work computer)

---

### Post by jaezcurra on 2011-04-26
KVM is not definitely installed in my computer (only qemu-kvm) :confused:

Any hint?

---

### Post by CharlesA on 2011-04-26
qemu-kvm is probably what is causing the problem then.

---

### Post by jaezcurra on 2011-04-26
> **CharlesA said:**
> qemu-kvm is probably what is causing the problem then.

I guess you think that I'd rather uninstall it ...

---

### Post by CharlesA on 2011-04-26
The same thing was posted [here]("http://forum.virtualbox.org/viewtopic.php?f=1&p=156122").

I would suggest checking to see if those kernel modules exist.

---

### Post by jaezcurra on 2011-04-26
> **CharlesA said:**
> The same thing was posted [here]("http://forum.virtualbox.org/viewtopic.php?f=1&p=156122").

I would suggest checking to see if those kernel modules exist.

I'll be checking tomorrow morning and let you know.

Anyway, I can't understand why is this happening just now with VB 4.0.6, and never before.

---

### Post by jaezcurra on 2011-04-27
Fixed!!!

I did not understand why VirtualBox had always worked, but not now; just with version 4.0.6.

I uninstalled qemu-kvm as well as qemu and Synaptic proposed to uninstall some other software too.  And I could see what had happened: meanwhile I had installed MultiSystem ([http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)), an excellent app to create multiboot USB sticks.  It happens that MultiSystem installed Qemu with it and enabled KVM mode ...

---

### Post by CharlesA on 2011-04-27
Ah hah!

Glad you got it working. :)

---

