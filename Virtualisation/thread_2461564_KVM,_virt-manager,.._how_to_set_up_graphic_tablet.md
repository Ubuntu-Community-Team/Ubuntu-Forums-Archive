---
title: "KVM, virt-manager,.. how to set up graphic tablet"
date: 2021-05-03
forum: Virtualisation
---

### Post by mlocik97 on 2021-05-03
Hello,

my problem is guest doesn't detect presure from graphic tablet,... cursor move correctly, but presure not.

I tried to use this setting:

```

<qemu:commandline>
    <qemu:arg value='-device'/>
    <qemu:arg value='usb-wacom-tablet'/>
  </qemu:commandline>

```

but it doesn't work,... when I pass graphic tablet to guest, presure work, but problem is, mouse cursor doesn't move as I move pen above tablet. I would rather let guestOS take presure from hostOS then passing tablet to guest.

Can someone help?

---

