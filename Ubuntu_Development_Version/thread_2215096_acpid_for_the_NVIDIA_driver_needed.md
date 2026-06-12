---
title: "acpid for the NVIDIA driver needed?"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-04-04
I'm using nvidia-331-updates 331.38-0ubuntu7 and it has acpid as dependency but if I'm making a look into /etc/acpi I'm seeing only a power button rule that comes directly from acpid. Now I'm wondering why acpid is needed if nvidia-331-updates gets installed. Does the driver get some other benefits if acpid is running. If there are no/less benefits I will open a ticket on Launchpad requesting to remove acpid as dependency/declare it as recommends for the nvidia-331-updates package.

Edit: I have now opened a ticket for this: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1314378](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1314378)

---

