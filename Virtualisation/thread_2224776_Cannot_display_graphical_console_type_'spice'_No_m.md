---
title: "Cannot display graphical console type 'spice': No module named SpiceClientGtk"
date: 2014-05-18
forum: Virtualisation
---

### Post by amiyourdream on 2014-05-18
Hello,

On a fresh install of Ubuntu 14.04 64 bit, I installed KVM, created a VM using an existing Windows XP disk image and set display to spice. I get the following error when I start the VM in virt-manager:

Cannot display graphical console type 'spice': 
No module named SpiceClientGtk

I have run into this in the past (in Ubuntu 13.04, 13.10 and OpenSUSE 13.1) and upon installing the spice-client-gtk package the problem went away. But not this time, I'm clueless and would appreciate your help.

Hypervisor Details
Hypervisor: kvm
Architecture: x86_64
Emulator: /usr/bin/kvm-spice
Firmware: Default

I am able to connect to it by running in a terminal:

spicec -h 127.0.0.1-p 5900

This launches a new window with the VM display (I'm unable to resize it though).

Thanks

---

### Post by KillerKelvUK on 2014-05-23
have the same setup, I use remote-viewer which is a much better console for spice connections which allows you to resize & scale the remote desktop to the window etc.  If you want a console inside the Virt-Manager window add an additional VNC Display to your KVM guest config alongside the Spice Display.

If you want to use Spice within Virt-Manager then you need the 'python-spice-client-gtk' package installed.

---

### Post by amiyourdream on 2014-05-23
> **KillerKelvUK said:**
> have the same setup, I use remote-viewer which is a much better console for spice connections which allows you to resize & scale the remote desktop to the window etc. 

Thanks will give remote-viewer a try some time.
 
> **KillerKelvUK said:**
> 
If you want a console inside the Virt-Manager window add an additional VNC Display to your KVM guest config alongside the Spice Display.

If you want to use Spice within Virt-Manager then you need the 'python-spice-client-gtk' package installed.

I already had python-spice-client-gtk installed but still was getting the error. I had only one display type which was set to Spice. But guess what.. **I just set the video device type from VGA to QXL and now its all working..** no more the same aforementioned error. It seems all I had to do was that! But thanks for the tip about adding an additional VNC display alongside the spice display, I was about to try that before it occurred to me to change the video device type from VGA to QXL! Note that originally I had just changed the existing display type from VNC to SPICE.
Note that I also had the spice guest tools module installed in the Windows XP guest. However the error "No module named spice-client-gtk'  is misleading in this context!

---

### Post by KillerKelvUK on 2014-05-26
> **amiyourdream said:**
>  However the error "No module named spice-client-gtk'  is misleading in this context!

Agree, glad you got it working :popcorn:

---

### Post by TheFu on 2014-05-26
Please mark this thread "SOLVED"

BTW - I just tested spice between a 14.04 kvm server running a 14.04 openbox VM from a 14.04 desktop over a GigE LAN and compared to x2go, it sucks. There is a huge lag  - like 10+ seconds for a mouse click.  Mouse select/paste isn't working well either.  x2go *just works* and includes ssh so all the connections are tunneled, secure.

I've seen spice work well when used over a VPN connection to RHEL systems (all proprietary RHEL management stuff). For the last 3 yrs, I've been watching spice on Ubuntu and it isn't really usable yet, IMHO.  Perhaps it is just that I always run remote and never local. As my KVM servers don't have a desktop, so no local access through any GUI is possible.

---

