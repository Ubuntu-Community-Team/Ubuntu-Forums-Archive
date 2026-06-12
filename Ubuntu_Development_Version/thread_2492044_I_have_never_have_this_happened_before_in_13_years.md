---
title: "I have never have this happened before in 13 years (???)"
date: 2023-10-28
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-10-28
I have been using KVM since 2010... My KVM install is up to date.

When starting my 24.04 Noble VM this morning to apply it's daily updates to test... It notified me from the Gnome Notifcation Center, that there are fwupdates available for it. 

My KVM host is 13th Gen Intel, and does not report that are any updates pending. But KVM BIOS is not pass-through, they are image files.

The BIOS for this VM is UEFI and are these KVM file's.
```

  <os>
    <type arch="x86_64" machine="pc-q35-6.2">hvm</type>
    <loader readonly="yes" type="pflash">/usr/share/OVMF/OVMF_CODE_4M.ms.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/noble24.04-00_VARS.fd</nvram>
  </os>

```
I have never seen this notification in a VM before. Is this even possible in a VM? The NVRAM is writable for the persistence...

I have never had this scenario come up before in a VM... None of my many other VM's are reporting this. Not sure if it will blow it out or be successful.

I'm thinking of cloning the VM and seeing what happens if I do this... I'm assuming that it will try to update the NVRAM image. But maybe I should make a copy of the .fd file for the just-in-cases. That "should" be protected from a VM's actions (it's owned by root, and it's tagged as read-only by the VM XML above), but this is new territory...

Thoughts?

---

### Post by MAFoElffen on 2023-10-28
It updaed the UEFI revocation DBX, which then crashed and threw an error. After reboot, it reported that is had updated that successfully(?) and that the firmware was up to date.

---

