---
title: "Forced to recompile Kernel Modules Everytime"
date: 2010-10-18
forum: Virtualisation
---

### Post by twjolson on 2010-10-18
I downloaded and installed VMWare Workstation 7, like I have many times.

However, everytime I run Workstation, it has to recompile the kernel modules.

Running 'sudo vmware-modconfig --console --install-all'
it ends saying 'Unable to install vsock'.  I get the same error regardless of whether I have run 'sudo apt-get install gcc build-essential linux-headers-$(uname -r)' or not.

Running the recompile from the GUI gives me a Caution icon next to VMCI Sockets.

Once that is done, Workstation seems to run as normal.

I have downloaded and reinstalled the current version, to no avail.

I have not dug into the guts of VMWare before, so any help would be great.

I am on Ubuntu 10.10, kernel version 2.6.35-22-generic, using Workstation 7.1.2 build-301548.

---

### Post by twjolson on 2010-10-18
I googled my brains out, and I finally found the answer.

It's at [http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10](http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10)

---

