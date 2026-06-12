---
title: "Universal virtual OS on a USB stick"
date: 2009-12-12
forum: Virtualisation
---

### Post by wobat on 2009-12-12
I've been looking for a solution to a problem I've had for a while:

I use computers at university and at work which are locked down, so I can't install any software.
Uni use linux (CentOS).
Work use Windows XP.
I don't have administrator/root access in either system.

What I would like is linux in a VM that can be launched from within linux or windows, without rebooting (Uni network will only allow internet access if logged in to their system :( ), and for changes to be persistent.

I've looked around a bit and all I can find is for how to use linux in windows, but not linux in linux.

Is it possible? If so how?

---

### Post by fouadatmeh on 2009-12-12
Hello,

The solution I can think of is to use two portable versions of virtualbox or any other virtualization software (one for windows and one for linux) on the same usb and use the same virtual harddrive in both...

* I have tried to run the same guest in two host environments and it works fine as long as I shutdown the guest before switching to the other hst, but it gave me problems when I tried to save its state.

---

### Post by wobat on 2009-12-12
Thanks! I didn't know you could get VirtualBox as a portable app :)

I just looked on google for portable VirtualBox on linux, but only got results for running in windows.
Is there a version somewhere for linux? Or is it something that needs to be compiled from source?

At least this has solved half the problem, I can use VBox portable at work and open the same VM at home in my installed VBox.

Your help is much appreciated :D

---

