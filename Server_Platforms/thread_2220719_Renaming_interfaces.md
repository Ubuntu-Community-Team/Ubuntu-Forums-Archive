---
title: "Renaming interfaces"
date: 2014-04-29
forum: Server Platforms
---

### Post by Sout on 2014-04-29
Hello

I am having some issues with Server 14.04 and the renaming of interfaces.

I have made peace with the idea of my interfaces being named em1 - 4 and no long eth0 -3, but now my second server I am trying to install has his interfaces all over.

All I want to accomplish is to rename the the interfaces to have them in order ether em1 - 4 or eth0 - 3, but it does not seem that /etc/udev/rules.d/70-persistent-net.rules exists anymore.

Any help would be appreciated.

Thanks

---

### Post by bab1 on 2014-04-29
> **Sout said:**
> Hello

I am having some issues with Server 14.04 and the renaming of interfaces.

I have made peace with the idea of my interfaces being named em1 - 4 and no long eth0 -3, but now my second server I am trying to install has his interfaces all over.

All I want to accomplish is to rename the the interfaces to have them in order ether em1 - 4 or eth0 - 3, but it does not seem that /etc/udev/rules.d/70-persistent-net.rules exists anymore.

Any help would be appreciated.

Thanks

See here: [http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/]("http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/")

---

