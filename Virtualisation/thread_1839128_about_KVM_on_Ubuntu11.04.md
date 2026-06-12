---
title: "about KVM on Ubuntu11.04"
date: 2011-09-05
forum: Virtualisation
---

### Post by node2network on 2011-09-05
I installed KVM(Kernel Virtual Machine), and I installed Ubuntu10.04 on KVM.
It was successfuly installed. But I can't change current monitor resolution to higher resolution(1920*1200).

How should I do to change to higher resolution ? reinstall with some options?

And when I login Virtual Machine with VNC viewer, I want to adjust VNC viewer's window size to VM's monitor resolution dynamically.

Could you help me?

---

### Post by bodhi.zazen on 2011-09-05
The best option, imo, is to use spice.

Unfortunately Fedora is more cutting edge on KVM then Ubuntu and so while spice is working in Fedora seamlessly, it has not yet been fully ported to Ubuntu (or Debian).

I do not think there is a solution for what you want using Ubuntu, or if there is one it is going to be so slow to be unusable.

You can take a look at this : [http://blog.bodhizazen.net/linux/how-to-improve-resolution-in-kvm/](http://blog.bodhizazen.net/linux/how-to-improve-resolution-in-kvm/)

The problem I had with that is with high resolutions, such as what you want, performance drops.

AFIK either you use Ubuntu and accept a lower resolution and wait until spice is ported or try Fedora - sort of a rock and a hard place.

You could try Freenx, not sure if it will give the resolution you want.

---

