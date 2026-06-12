---
title: "MAAS causing nodes to reinstall themselves every time i start them"
date: 2014-06-03
forum: Ubuntu Cloud and Juju
---

### Post by redDragon128 on 2014-06-03
Almost every time I start a node, it reinstalls ubuntu on the node. It says booting under MAAS direction, then it grabs the PXE ROM and then decides to run the ubuntu installer. What could I be doing wrong to make it reinstall itself every single time? I've only randomly been able to boot it from the console without it deciding to reinstall itself...

---

### Post by redDragon128 on 2014-06-04
nodes are still commissioning themselves (reinstalling ubuntu) over and over and over and over...

---

### Post by chris240 on 2014-06-13
Just n reminder every-time you press start on the MAAS admin panel it allocate to the user you setup on MAAS and install Ubuntu OS same as if you bootstrap your instances so i would not pref to press start button if its allocated and the Ubuntu OS is installed and ready to deploy any juju service. The MAAS admin panel stop button kills the machines of MAAS. I would rather use your power management that was configure on your MAAS what ubuntu OS version do you use?

---

