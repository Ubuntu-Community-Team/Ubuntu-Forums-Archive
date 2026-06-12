---
title: "Display Error"
date: 2013-02-26
forum: Virtualisation
---

### Post by XK15 on 2013-02-26
Hi,
I'm using VMware Player for Ubuntu. The photo will show that i cannot use/see any controls basically. They are all blacked out. Any Help?

---

### Post by TheFu on 2013-03-01
I stopped using Vmware player many years ago, when VirtualBox became FOSS, so I do not **know** the answer, but here are a few ideas:
* Did you enable 2D/3D graphics accelleration to the VM?
* Did you install the Guest Additions inside the VM?
* Is there enough video RAM provided to the VM?  I do not know what the defaults are for Player, but in VBox, the default video-RAM is much, much, much too low for Unity (the normal Ubuntu DE) to work.

---

