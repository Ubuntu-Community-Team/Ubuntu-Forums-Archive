---
title: "Linux Mint 17 Cinnamon only runs in software rendering mode in KVM"
date: 2014-09-05
forum: Virtualisation
---

### Post by Remten on 2014-09-05
When trying to run Linux Mint Cinnamon 17 as a guest in KVM, the following warning is displayed:
> Cinnamon is currently running without video hardware acceleration  and, as a result, you may observe much higher than normal CPU usage.

There could be a problem with your drivers or some other issue. For the  best experience, it is recommended that you only use this mode for  troubleshooting purposes.
I don't get this warning if I run a Linux Mint 17 Mate guest or an OpenSUSE 13.1 guest.
I've turned off desktop effects and windows effects in the guest's internal system settings.

I've also tried to enable acceleration in the kvm settings
```

<video>
   <model type='qxl' ram='65536' vram='65536' heads='1' 7>
   <address type='pci' domain= ...
   <acceleration accel3d='yes' accel2d='yes' />
</video>
```(edited)

but that entry doesn't seem to be supported for qxl. (When I re-define the settings, the acceleration entry gets wiped out.)

---

### Post by TheFu on 2014-09-06
Local or remote desktop connection?  Are you sitting ON the KVM host?

---

### Post by Remten on 2014-09-06
The host is a laptop. The guest is on the same machine. Nothing remote.

---

