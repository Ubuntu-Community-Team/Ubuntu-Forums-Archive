---
title: "VMs do shutdown not restart as expected?"
date: 2009-04-10
forum: Virtualisation
---

### Post by Schorschi on 2009-04-10
Using KVM and Virt-Manager (latest) as part of Jaunty Beta (latest).

Have several Windows 2008 virtual machines, the Windows Installer does its thing, the initial load of the Windows OS goes as expected, but when the first reboot is done, the virtual machines shutdown, not doing a reboot as expected.  This is the the normal behavior?  In fact, every time a restart is requested, a shutdown is actually done.  This does not happen for VMware or XEN but with KVM?  Or is this a quirk of Virt-Manager?

Also, Ctrl-Alt-Backspace and Ctrl-Alt-Del some to be inverted in Virt-Manager.  Is this bug or by design?

---

