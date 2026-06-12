---
title: "cannot display graphical console type 'spice' no module named spice client gtk"
date: 2012-05-12
forum: Virtualisation
---

### Post by jmarcedwards on 2012-05-12
I am using Ubuntu Precise.

Have a RHEL 6.2 VM using kvm.  I am trying to get the Spice graphics adapter to work.

I have installed:

[LIST=1]
[*]qemu-kvm-spice package
[*]python-spice-client
[/LIST]

I've looked all over for solutions to this issue, with no success.

Any help would be appreciated.

---

### Post by rwh on 2012-05-15
You probably need to change the emulator to /usr/bin/kvm-spice.  So try something like this:

virsh dumpxml vmname > vmname.xml
# open vmname.xml in a text editor and change the emulator to /usr/bin/kvm-spice from /usr/bin/kvm
virsh create vmname.xml

Then open up virt-manager, change the VNC device to spice, etc.  Note however that the spice-enabled version has some bugs that mean that it doesn't display bios messages.  You won't see any video until the OS boots and loads the spice driver.  For this reason I uninstalled it and went back to the non-spice enabled version of KVM.  I use xrdp to covert the VNC root console into RDP for remote admin.

Cheers,

Rob

---

### Post by btkm on 2012-05-18
After following the steps described at [https://wiki.ubuntu.com/SergeHallyn_spice](https://wiki.ubuntu.com/SergeHallyn_spice) I encountered the same problem. Since it looked like a missing python module I installed python-spice-client-gtk package. VM starts now but it results in a black screen. As rwh already told, this could indeed be a "spice" problem.
So xrdp looks like the best option. On host I used remmina and on guest system I installed xrdp package. Hope this helps.

---

