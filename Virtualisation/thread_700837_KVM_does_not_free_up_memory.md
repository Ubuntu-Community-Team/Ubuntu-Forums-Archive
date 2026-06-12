---
title: "KVM does not free up memory"
date: 2008-02-18
forum: Virtualisation
---

### Post by gecka on 2008-02-18
Hello,

When running windows xp with kvm it memory get fill to 544Mo and never frees up (for KVM process)

Here is how I launch it: kvm -no-acpi -m 512 -cdrom /dev/cdrom "/media/Data/Virtual machines/Windows XP professionnal/windows.img"

Did I miss something?

Reagrds

---

### Post by dendrobates on 2008-02-21
-m 512 tells kvm to use 512MiB of memory for the VM.  It is dedicated to the VM.  This is exactly how it is supposed to work.

All of the memory in your VM is considered used and will not be free while the VM is running.

---

