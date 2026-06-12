---
title: "Min specs for 1080p"
date: 2009-10-04
forum: The Cafe
---

### Post by bear24rw on 2009-10-04
I'm looking to build the cheapest possible ubuntu box that can pump out 1080p over hdmi, What would you say is the min specs are for doing this? I'm thinking at least a 9600GSO

I already have 400W psu and harddrive so i just need mobo, cpu, ram, video card.

What do you guys recommend?

---

### Post by Bachstelze on 2009-10-04
My 8400GS plays 1080p fine when using CUDA/VDPAU. It's very bad for gaming, though.

---

### Post by bear24rw on 2009-10-04
> **Bachstelze said:**
> My 8400GS plays 1080p fine when using CUDA/VDPAU. It's very bad for gaming, though.

Does ubuntu (or the nvidia drives actually) support cuda acceleration out of the box??

---

### Post by fela on 2009-10-04
Possibly something like a 9600GT or Radeon HD 3850 will do it just fine, coupled with a good Intel C2D E6600 or AMD Athlon II CPU and 1GB RAM (2GB is a waste for most things).

---

### Post by Bachstelze on 2009-10-04
> **bear24rw said:**
> Does ubuntu (or the nvidia drives actually) support cuda acceleration out of the box??

CUDA on Windows, VDPAU on *NIX. I think the Linux drivers support CUDA too, but there's no application using it yet.

---

### Post by bear24rw on 2009-10-04
> **Bachstelze said:**
> CUDA on Windows, VDPAU on *NIX. I think the Linux drivers support CUDA too, but there's no application using it yet.

lol that's what I thought.

Single core 2.7GHz should be enough to decode right?

---

### Post by Bachstelze on 2009-10-04
> **bear24rw said:**
> lol that's what I thought.

Single core 2.7GHz should be enough to decode right?

Yeah. If you're using VDPAU, the CPU matters very little, since it's the GPU that does the decoding work.

---

