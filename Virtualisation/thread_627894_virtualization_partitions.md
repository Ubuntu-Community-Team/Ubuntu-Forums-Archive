---
title: "virtualization partitions"
date: 2007-11-30
forum: Virtualisation
---

### Post by afderrick on 2007-11-30
I don't know anything about virtualization but am wanting to for a few small tasks.  The question I have is when installing Ubuntu do I need to leave 20-ish gigs unformatted to put the virtual windows install on?  Or do I format the entire harddrive?  Dumb n00b question, sorry.

---

### Post by bodhi.zazen on 2007-11-30
When you make a new virtual machine it will make a new a virtual hard drive. The virtual hard drive is a file on your Linux partition, or wherever you put it.

In general virtual machines do not directly access your hard drive, so you do not need raw unformatted space.

When you first access a virtual disk it will appear as raw, unformatted space to your virtual machine.

I give my virtual machines as little space as possible, 20 Gb may be small for windows, but you might be able to trim that down to 10 Gb ?

---

### Post by afderrick on 2007-12-01
Yeah, that was the first number that came to mind, just mostly wanting to know which way to go, I'm just running one program on it, so 10G is probably plenty enough.

---

