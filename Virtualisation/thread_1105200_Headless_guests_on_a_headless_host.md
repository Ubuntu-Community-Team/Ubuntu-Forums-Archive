---
title: "Headless guests on a headless host"
date: 2009-03-24
forum: Virtualisation
---

### Post by decoherence on 2009-03-24
Hi all,

What's the best way of doing headless guests on a headless host? I tried doing it with VirtualBox but the OSE version won't let you run in "vrdp" mode, which you evidently need to do to get a guest to start up headless (@#$@# I just want to send video to /dev/null!! I don't care from RPD!)

I know this is easy to do with VMWare. Unfortunately VMWare demands I recompile its kernel module every time I update, which I want to avoid (I don't really mind but my co-workers are not savvy to this.)

So... looking for either some way of getting it to work with VBox (which I know and love) or I'm looking at KVM or Xen?

Suggestions and pointers to how-tos are much appreciated! If I find anything I'll update the thread.

---

### Post by fno on 2009-03-24
I would use kvm, which is included in the standard kernel and is designed to run headless. Then just install a ssh daemon in the guest and you're done...

---

