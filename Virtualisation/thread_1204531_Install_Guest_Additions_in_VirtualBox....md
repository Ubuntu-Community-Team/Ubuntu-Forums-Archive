---
title: "Install Guest Additions in VirtualBox..."
date: 2009-07-04
forum: Virtualisation
---

### Post by RadarBat on 2009-07-04
I have installed Eeebuntu 9.04 on VirtualBox as a VM. After searching high & low, I located the VBoxGuestAdditions.iso and mounted it in the VM. I am stuck with the error "Please install the build and header files for your current kernel (2.6.28-11)."
How do I do this?

EDIT: What are those files called and are they available through Synaptic PM?

---

### Post by aesis05401 on 2009-07-04
Easiest way is to pop synaptic (launch with root permissions ie: 'gksu synaptic').

Typing 'build-essential,' into the Synaptic search box brings the package right up... and 'header' in the search field also brings that file up.. Should be pretty straightforward.

---

### Post by RadarBat on 2009-07-04
Thanks

---

