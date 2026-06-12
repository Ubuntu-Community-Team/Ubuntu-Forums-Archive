---
title: "How to upgrade a xen  vps kernel?"
date: 2011-06-18
forum: Virtualisation
---

### Post by L1234 on 2011-06-18
Hi, all i have vps xen server (kernel 2.6.32-305-ec2)and i want to upgrade kernel. I used  this guide [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) , for me it works in virtualbox ,but in xen vps, compiled kernel doesn't boot at all and after 5secs server turns off. So what exactly should i do to upgrade kernel in xen vps? Thanks for any help.

---

### Post by Dedoimedo on 2011-06-18
Any meaningful message on the console?
Dedoimedo

---

### Post by L1234 on 2011-06-19
> **Dedoimedo said:**
> Any meaningful message on the console?
Dedoimedo

No , when i try to connect to node, putty drops. Don't know what to do.

---

### Post by Dedoimedo on 2011-06-19
Can you reach the physical machine? Serial console?

What's your grub kernel line?
Can you try verbose output (no silent)?
Maybe turn on/off features, like acpi, vga modes, etc.

Dedoimedo

---

### Post by jonathanross on 2011-06-23
I've had these problems with Xen too - any fix for your issue ?

---

