---
title: "Picking a virtualization solution"
date: 2015-07-31
forum: Virtualisation
---

### Post by euphoria42 on 2015-07-31
Hey guys, as my title suggests I need help picking a virtualization solution. Right now I am running Ubuntu Gnome 15.04 64bit as a host and Windows 7 64bit as a guest in VirtualBox. But its been brought to my attention that there are better performing options out there. I don't think I can to VGA pass-through, my CPU (i7 3770k) only supports VT-x and not VT-d (and my GPU is the GTX 770), but that would be a cool option. However, I'm not entirely sure I need that for what I use my VM for, which is currently just using Photoshop since its more familiar to me than GIMP is (but hey, if I could do gaming in it, that would be cool too!). So I probably only need 3D acceleration. Long story short, thats my current setup and im trying to see if there is a better virtualization option for what I use my VM for.

Thanks for any help!

---

### Post by TheFu on 2015-07-31
Stay with virtualbox for GUI stuff.
Be certain to tune the VM since the default settings often are sub-optimized for performance.

The only other real option is to use KVM + SPICE for the display, but that works much better on CentOS/Fedora than on Ubuntu systems. I've never gotten it working better than x2go which doesn't support 3D accel needs at all. OTOH, x2go is a remote desktop that works, securely, from anywhere in the world you can use ssh. Trade-offs.

Spice does support 2D stuff and 3D is planned. [http://www.spice-space.org/features.html](http://www.spice-space.org/features.html)

---

### Post by euphoria42 on 2015-07-31
Thank you for the input, ill stick with VirtualBox for now then. KVM seems to be more than I need and doesn't support 3D Acceleration.

---

