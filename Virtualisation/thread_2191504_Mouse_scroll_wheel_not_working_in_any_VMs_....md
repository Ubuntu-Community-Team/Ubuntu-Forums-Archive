---
title: "Mouse scroll wheel not working in any VMs ..."
date: 2013-12-03
forum: Virtualisation
---

### Post by Bucky Ball on 2013-12-03
Hi all,

Title says it all. Any ideas? I'm using all Ubuntu based VMs and Virtualbox.

---

### Post by QIII on 2013-12-03
Did you install the extension pack and guest additions?

---

### Post by Bucky Ball on 2013-12-03
Ha! Coincidentally I was just looking at how to do that. ;)

---

### Post by QIII on 2013-12-03
And somehow I think you'll figure it out!

;)

---

### Post by Bucky Ball on 2013-12-04
Just a note on this: I am currently typing this from Porteus using the Razor desktop environment in a VM and the scroll wheel works without issue. Go figure. It's the only VM it's worked in without guest additions (haven't played around with that yet but have done the research). And I've tried a heap! ;)

* Update: Works ok with Linux Mint Cinnamon also.

---

### Post by sorceror171 on 2014-01-22
> **QIII said:**
> Did you install the extension pack and guest additions?

I'm having the same problem, but I'm using command-line Qemu. I'm running a Xbuntu 13.10 guest on a Xubuntu 13.10 host. (I use it as an isolated browsing environment.)

With 13.10, suddenly the scroll wheel input doesn't get passed in. The scroll wheel works in the host but not the guest. On 13.04, it "just worked", I didn't need to install any "guest additions".

The command I use to launch the VM is:

   qemu-system-x86_64 -m 2048 -soundhw all -hda ubu.qcow2 -usbdevice tablet 

Is there some option I'm missing?

---

### Post by Bucky Ball on 2014-01-22
*Thread solved and closed.*

Guest additions works for me.

@sorceror171: You'll have much better luck getting support by posting a new thread rather than tagging on to and resurrecting a two month old stagnant one. Good luck. ;)

---

