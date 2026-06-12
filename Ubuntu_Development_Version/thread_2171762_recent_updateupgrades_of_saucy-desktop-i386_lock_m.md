---
title: "recent update/upgrades of saucy-desktop-i386 lock mouse in lightdm"
date: 2013-09-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-09-01
I have two machines now (three installs of saucy) that , after update/upgrade will display a locked mouse cursor in lightdm. In some instances I can get to terminal. At other times it will stay locked until hard-boot.

 These 2 machines are running graphics adapter nVidia 210 (nouveau-unity-system-compositor). One , AMD dual Core Athlon and the other , Intel 3.4GHz.

  Please note this  is happening in "Ubuntu" as I had not tested the other flavour installs as of yet.

---

### Post by ventrical on 2013-09-01
This update/upgrade also affects Intel SandyBridge graphics. Mouse is delayed with intermittent sparky mouse effect in lightdm and in Password dialog field.

I am assuming it must be unity-system compositor or one of the drivers.

```


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

---

### Post by ventrical on 2013-09-01
This fixed on Intel based graphics by commenting out:
 type=unity.

 edit-   etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf

```

[Seat Defaults]
#type=unity

```

edit:

This fixed as well with nVidia graphics and nouveau.  Unity -system compositor must be temoprarily borked.

Regards..

---

