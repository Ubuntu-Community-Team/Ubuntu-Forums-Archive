---
title: "Improving Ubuntu's Autoinstall/Cloud-Init"
date: 2023-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by faldrich on 2023-06-07
Hello all,

I've been diving into Ubuntu's autoinstall and Cloud-Init as we're starting to use Ubuntu alongside Red Hat Enterprise Linux (RHEL) in our operations. And let me tell you, it's been an unpleasant few days.

I see the potential of Cloud-Init, but it seems its implementation in Ubuntu needs work to make it more reliable and admin-friendly. From what I've read on forums and blogs over the past week, I'm not alone in this sentiment.

The Debian-installer (preseed) was mature, pretty well-documented, and while it wasn't perfect, it was predictable.

The documentation for Autoinstall seems to be geared for people working with QEMU, KVM, and similar. But it doesn't seem to work very well for real-metal systems; at least, I've not gotten it working reliably.

I appreciate that Cloud-Init has a lot to offer, but right now it feels like the transition from Debian-installer might be premature. Is there a reason we can't have Debian-installer stick around while Cloud-Init gets polished up?  Or even keep the preseed process, as an alternative?  What are the technical issues involved?

I appreciate all the hard work put into integrating cloud-init with Ubuntu. I just feel the implantation "right now" is a big of dumpster fire.


_F

---

### Post by QIII on 2023-06-07
Moved to Ubuntu, Linux and OS Chat.

---

### Post by ian-weisser on 2023-06-07
> **faldrich said:**
> it feels like the transition from Debian-installer might be premature

On Ubuntu Server, that transition completed over three years ago (20.04). Six releases ago, and working on a seventh.

---

### Post by faldrich on 2023-06-07
I see.  Makes me wonder why, after all this time, there are apparently problems with it still.

---

