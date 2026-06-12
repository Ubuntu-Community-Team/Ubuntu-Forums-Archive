---
title: "Qemu x86_64 doesn't work"
date: 2009-12-24
forum: Virtualisation
---

### Post by recentconvert on 2009-12-24
I'm trying to test out different Ubuntu Variants to see which one I'd like better. But I'm having trouble trying them out with qemu. The distros are 64bit versions as my cpu is a 64bit processor. I'm using Qemulator as the front end. When ever I trying running a VM I get this message...
> 
The Kernel requires an X86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU                      .
Is there something I'm missing or need to install?
Running Ubuntu 9.10

---

### Post by insane_alien on 2009-12-24
do you have a 64-bit OS installed?

post the output of 'uname -a'

---

### Post by recentconvert on 2009-12-27
I should have mentioned I'm running Ubuntu 9.10 32-bit. But I'm surprised that matters. When I used qemu from a 32-bit copy of windowsXP I could run virtualized copies of 64bit OS's. That actually has me surprised that I need a 64bit os in order to run one virtualized in ubuntu.

---

### Post by inclusivedisjunction on 2009-12-29
Are you sure you have x86_64 selected in qemulator, and not x86? Using x86_64 works fine for me in Kubuntu 9.10 with Slamd64 as a guest. My Kubuntu x86_64 ISO seems to work as well, although it takes a ridiculously long time to boot, so I have not tested it past the boot splash.

Try this test from the command-line to double-check:

qemu-system-x86_64 -m 512 -cdrom yourimagehere.iso

---

### Post by recentconvert on 2010-01-12
> **inclusivedisjunction said:**
> ... so I have not tested it past the boot splash.

Try this test from the command-line to double-check:

qemu-system-x86_64 -m 512 -cdrom yourimagehere.iso
I have tested past the bootsplash and that is the message I get. And yes I have selected x86_64 in qemulator. And this is why I'm asking if I'm missing something.

---

### Post by ikem.krueger on 2013-02-18
I got them working with:

```
qemu-system-x86_64 **-no-kvm** -m 512 -cdrom yourimagehere.iso
```

---

### Post by wildmanne39 on 2013-02-20
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

