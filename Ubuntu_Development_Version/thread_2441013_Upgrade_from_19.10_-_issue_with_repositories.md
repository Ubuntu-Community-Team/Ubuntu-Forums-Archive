---
title: "Upgrade from 19.10 - issue with repositories"
date: 2020-04-17
forum: Ubuntu Development Version
---

### Post by pablosquared on 2020-04-17
Hi all. I recently upgraded from 19.10 to 20.14 beta. All was well, except GNOME Extension settings didn't work - I've seen some people reporting that. I couldn't install the recommended GNOME settings prefs file, it wasn't found. After a couple of weeks  hoping it would be fixed, I investigated further. I found, in synaptic, that the distro repos were un-ticked. See 1st image.

On ticking these repos and reloading, I was presented with a large set of updated packages, including the GNOME Extensions prefs file, an updated NVIDIA driver and a new kernel. Installed, rebooted and all is well, and I can change extension settings.  I also note that Settings staes that the version of Ubuntu is 20.04, not development branch (see 2nd image) - which would seem to suggest we may be at the final version already. Don't quote me..

So, if anyone is unable to configure GNOME extensions / settings after upgrading from 19.10, check the selected repos.

---

