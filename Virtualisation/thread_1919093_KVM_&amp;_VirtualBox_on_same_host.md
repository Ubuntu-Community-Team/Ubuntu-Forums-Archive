---
title: "KVM &amp; VirtualBox on same host?"
date: 2012-02-02
forum: Virtualisation
---

### Post by Nick_C on 2012-02-02
Has anyone tried running both KVM and VirtualBox on same Ubuntu host?  Just wondered if this was possible to allow for easy testing and comparison.

Thanks,
  Nick

---

### Post by CharlesA on 2012-02-02
They will conflict with each other.

---

### Post by Dangertux on 2012-02-02
HOWEVER

You can in fact (if you have an AMD processor with the nesting flag and support for full hardware virt) Run a Virtualbox host inside a KVM guest ;-)

So...

Ubuntu Host (with KVM) - > Virtualized Fedora (running Virtualbox) -> Virrtualized Debian (running under Vbox)

Crazy huh?

---

### Post by CharlesA on 2012-02-02
I've actually done that before, except in my case it was VirtualBox on Ubuntu inside VirtualBox on Debian. It's kinda cool, but just remember not to google "google" from inside the nested VM..

---

### Post by japzone on 2012-02-03
> **Dangertux said:**
> HOWEVER

You can in fact (if you have an AMD processor with the nesting flag and support for full hardware virt) Run a Virtualbox host inside a KVM guest ;-)

So...

Ubuntu Host (with KVM) - > Virtualized Fedora (running Virtualbox) -> Virrtualized Debian (running under Vbox)

Crazy huh?

It's not just AMD's AMD-v but it'd also work with Intel's VT-x hardware virtualization Technology.

> **CharlesA said:**
> I've actually done that before, except in my case it was VirtualBox on Ubuntu inside VirtualBox on Debian. It's kinda cool, but just remember not to google "google" from inside the nested VM..

I'm curious, What Happened? :)

---

### Post by TheFu on 2012-02-03
> **Nick_C said:**
> Has anyone tried running both KVM and VirtualBox on same Ubuntu host?  Just wondered if this was possible to allow for easy testing and comparison.

No I haven't, but I did ask the same question here last year.
In the end, it was easier to dual boot and place the different hyper-visors on different 10G partitions.

I was looking for server virtualization.  KVM is what we decided to use, when LXC wasn't possible. LXC will run with KVM and VirtualBox on the same host.

VirtualBox is great too, but for desktop virtualization. At the time I found VBox to not be as stable as KVM. It crashed the entire hostOS.  The other issue is that VirtualBox needs X/Windows libraries for the GuestAdditions. That isn't acceptable for server virtualization, IHMO.

---

### Post by Dangertux on 2012-02-03
> **japzone said:**
> It's not just AMD's AMD-v but it'd also work with Intel's VT-x hardware virtualization Technology.



I'm curious, What Happened? :)

Cool didn't know the part about Intel

---

