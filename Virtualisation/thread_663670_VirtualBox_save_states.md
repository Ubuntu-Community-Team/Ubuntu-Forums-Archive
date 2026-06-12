---
title: "VirtualBox save states"
date: 2008-01-10
forum: Virtualisation
---

### Post by deepee111 on 2008-01-10
Hi:

My question pertains to loading the guest OS with particular apps open. Ideally, I'd like to be able to load a save state that would skip the boot up process and have a suite of apps I normally use together ready for use. I guess I interpreted "snapshots" incorrectly, in that they don't seem to serve this function.  I know that if you close VirtualBox it gives you the option to save the state, but I would like to do this for multiple groups of apps and be able to create launchers for each one. Is there a way to do this without creating a virtual machine for each grouping? Thanks in advance.

---

### Post by popch on 2008-01-10
According to the manual, you can keep a succession of snapshots, but you can always only run the latest one. You can revert to an earlier one by discarding all which followed that snapshot.

So it appears that you can not use VirtualBox as you described in your post.

With VMWare workstation you can store a tree of snapshots. As far as I remember, you can revert to any of the former snapshots and restart from there. That would possibly support the kind of solution you envision.

VMWare workstation is, however neither open source nor free of charge.

---

### Post by deepee111 on 2008-01-10
Thanks!

I seem to remember seeing VMware do this at work. Alas I don't own it at home.

---

### Post by fjgaude on 2008-01-10
With VMware Server, the free one, you can have only one snapshot. You can revert to it at anytime. You can take many snapshots but the last one will be the only one that is saved.

---

