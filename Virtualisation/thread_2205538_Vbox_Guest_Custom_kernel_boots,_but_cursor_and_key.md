---
title: "Vbox Guest Custom kernel boots, but cursor and keyboard frozen"
date: 2014-02-14
forum: Virtualisation
---

### Post by chris.curry on 2014-02-14
Running 12.04.3 as host and 12.04.3 as guest.  Compiled a 3.2.0 ubuntu-precise custom kernel on guest to patch a DVB media driver.  Patched, compiled, installed without complaint.  It boots and I can logon, but at that point the desktop appears with a cursor frozen in the middle of the pane, while the host cursor is free to mover around outside the pane.  Capturing and uncapturing doesn't help.  The keyboard doesn't work on the guest system either.  Booting back into the original 3.8 guest kernel everything works as it should.

I'm using Vbox 4.3.6. on an HP 15-N028US laptop.  AMD A-6, Radeon HD 8400.

Any help would be much appreciated.

Chris

---

### Post by jdeca57 on 2014-02-15
The obvious answer is that you failed to compile some elements in order to have a workable system. The fact that you compile without errors or that you can install it doesn't mean every functionality is added to the new kernel. In Virtualbox the mouse emulation is usb so look at that. I don't know about the keyboard, but it may be related. And of course, using the old kernel gives you a working system. There is nothing wrong with Virtualbox or your host...

---

