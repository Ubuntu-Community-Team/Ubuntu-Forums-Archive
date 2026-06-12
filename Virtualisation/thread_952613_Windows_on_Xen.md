---
title: "Windows on Xen"
date: 2008-10-19
forum: Virtualisation
---

### Post by vainov on 2008-10-19
Finally! It is time to abandon the Windows prison entirely!
For many years now me and my company have used Linux (and some MacOS). The sole exception is for our laptops.
A current switch to ThinkPad T61 has made it possible to convert even those machines.

There are two issues (of which the first is the most pressing):
1) We still need some of our Windows application (general ledger etc). Therefore we want to migrate our Windows disks to Virtual images. Our preference for virtualization is Xen, but we also use VirtualBox and VMWare (for now).
Question: Has anyone any pointers to how to migrate the entire disk image of the Windows laptops to a suitable virtualization technology under Ubuntu? (We have tried to use VMWare Converter, but that is not to our satisfaction, since it wants to validate the Windows installation on first re-boot, and does not accept the key that is on the sticker under the laptops; possibly because you can't validate keys that belong to bundled Windows licenses). NB! We are NOT interrested in re-installing Windows from scratch. We simply want to make vorking clones of the Windows disks, for which we have valid licenses.

2) We have experimented with Xen on the laptops, but the Xen kernel does not want to run correctly. (Quite apart from the problems that arise when one wants to install the xen-desktop packages). A WiFi configuration that works out-of-the box on 8.04.1 Desktop fails miserably on the DomO, so we can't use WiFi after switching to Xen. Any pointers to how to do this right?

---

