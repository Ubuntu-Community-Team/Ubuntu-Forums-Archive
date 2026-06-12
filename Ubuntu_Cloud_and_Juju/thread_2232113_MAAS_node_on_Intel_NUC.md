---
title: "MAAS node on Intel NUC"
date: 2014-06-29
forum: Ubuntu Cloud and Juju
---

### Post by l1fe on 2014-06-29
I've setup my main MAAS server on a non-NUC machine and everything went swimmingly. However, I can't seem to get Trusty installed correctly on any of my Intel NUC nodes. A few things:

1. Booting into PXE, I'm able to see the node try to register. I am able to accept the node.
2. Once it is accepted, the box actually shuts down. I have to start the NUC and again tell it to boot from PXE.
3. Commissioning the node initially seems to work - it downloads the files, goes to the login prompt, and seems to initiate an install - except the final step it, again, shuts down the NUC.
4. During this time, the MAAS server reports the NUC node as being "ready."
5. I try to install Juju and during the bootstrap process, it basically times out trying to connect to the node.

Anyone else have any experience working with MAAS on Intel NUCs? If it makes a difference, these are the latest Haswell i3s, and I have set the nodes as wake on lan...

---

### Post by l1fe on 2014-07-03
Guess I should respond with what I did to resolve my issues of getting MAAS installed on Haswell NUCs. It turns out I misinterpreted the lifecycle and instead should look something like this:

First PXE boot: Get enlistment image and enlist with MAAS. Shutdown.
Second PXE boot: (you must first accept the node in MAAS and then commission it) Download installation media. Shutdown.
Third PXE boot: (in MAAS, you must START the node) Perform installation. Reboot.
Fourth PXE boot: Checks in with MAAS, nothing to be done, normal boot.

Hope that helps someone else since the documentation makes it seem automagical, which I'm sure it would be if the wake on lan actually worked.

---

