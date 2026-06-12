---
title: "Linux within Linux"
date: 2011-02-27
forum: Virtualisation
---

### Post by 3602 on 2011-02-27
I am running 64-bit Ubuntu Maverick, 2.6.35-25. So I got VirtualBox (from Sun/Oracle, not Software Center) and am installing Mandriva (2009) within it. I have allocated a 8GB virtual drive according to the VB guide.
Here's the question. Once I reboot (the entire frame, not just Mandriva itself), would the Mandriva's "virtual" installation bleed-through into GRUB? Or is the Mandriva installation fully isolated and is only accessible though VB in Ubuntu?
Oh and any installation/modifications within the VB does *absolutely no changes* to my *existing disk/system*, correct?
Thank you very much.

---

### Post by CharlesA on 2011-02-27
Anything that is running in a virtual machine is confined to the virtual machine.

You won't see anything changed on the host system.

---

### Post by pafufta503 on 2011-02-28
virtualbox creates a virtual harddrive.  the entire virtual machine will be contained in a file, and will not affect the host OS.  it is safe to use, have fun.

---

### Post by 3602 on 2011-02-28
Alright, thanks guys.

---

