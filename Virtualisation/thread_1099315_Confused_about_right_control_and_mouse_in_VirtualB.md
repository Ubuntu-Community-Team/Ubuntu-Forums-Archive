---
title: "Confused about right control and mouse in VirtualBox"
date: 2009-03-18
forum: Virtualisation
---

### Post by JerryI on 2009-03-18
I have VirtualBox running and am in the process of installing XP.  I am at the point where I have to click on a box to continue, but I cannot figure out this right control (host key) business so that I can gain access to the mouse to click on the box without getting some arcane message about sending keystokes somewhere else.  Can anybody convert this gobbledygook into something I can understand so I can proceed?  It seems tha no matter what I do, I cannot obtain a functional mouse inside the VirtualBox.

Edit.  OK now it is working, but I still don't quite understand how I got it out of the mostly unresponsive mode.  I would still appreciate some enlightenment.

---

### Post by HankB on 2009-03-18
The VirtualBox will normally capture your mouse and keyboard and *all* input then goes to the guest running on the virtual machine. You can return the keyboard to the host OS by pressing the <host> key which defaults to the right control key.

With some guests, the mouse and keyboard can be shared between host and guest in windowed mode. By default VirtualBox warns you whenever it switches to a guest that does this but I think you can suppress further messages. Just remember to hit <right ctrl> to release the keyboard and focus from the guest when it sems to be captured.

Fun with VMs eh Jerry? ;)

-hank

---

