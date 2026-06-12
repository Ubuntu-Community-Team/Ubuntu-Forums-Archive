---
title: "Seeking paid assistance with VMWare + Ubuntu"
date: 2008-11-09
forum: Virtualisation
---

### Post by tjm5501 on 2008-11-09
Hello,

I am running VMWare Workstation in Windows XP, and have Ubuntu 8.10 installed as a virtual machine.

It seems to be working wonderfully, however the only thing I can't get going is compiz. I have it installed, and the control panel runs, but none of the effects actually work. I have a top of the line nvidia video card, but I think there is a communication problem between vmware & ubuntu, possibly that ubuntu doesn't see the nvidia directly, but rather some kind of vmware driver instead.

If someone can remotely connect to my computer and get this working, I'd be willing to pay $40 USD.  Any takers?

---

### Post by ghost_ryder35 on 2008-11-09
i do not belive vmware's video driver supports 3D.

---

### Post by tjm5501 on 2008-11-09
Oh man, really? lame

---

### Post by ciscosurfer on 2008-11-09
I came [across this]("http://ubuntuforums.org/showthread.php?t=152941") while searching the forums.  Maybe it can get you started.  You can also try searching on [B]mks.enable3d = "TRUE"

[/B]You may also [find this]("http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d.html") useful.  :-)

edit: [one more link]("http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d_enabling_vm.html")

---

### Post by veloce on 2008-11-11
> **ghost_ryder35 said:**
> i do not belive vmware's video driver supports 3D.

Ghost Ryder is correct about most versions of vmware (and all free versions) but not workstation.  Workstation has "experimental" implementation of 3D so it may or may not work as you expect.

The Mac version of vmware (fusion?) has 3d implemented properly, so I expect that the next version of Workstation will also fully implement it.

---

