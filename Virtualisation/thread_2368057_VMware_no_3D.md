---
title: "VMware no 3D?"
date: 2017-08-06
forum: Virtualisation
---

### Post by Donnut on 2017-08-06
I installed Windows 10 to play some Windows games(easier to get them running in a virtual machine then wine), I used VMware Player, and it tells me "No 3D support is available from the host" and "Hardware acceleration is unavailable". I have updated my graphics card(Intel HD integrated Iris 6100), Steam for Linux runs beautifully, but still no 3D support in VMware. Thoughts?

---

### Post by #&amp;thj^% on 2017-08-06
See if this helps: [https://askubuntu.com/questions/537787/enable-3d-hw-acceleration-on-vmware-workstation-10-on-ubuntu-14-04](https://askubuntu.com/questions/537787/enable-3d-hw-acceleration-on-vmware-workstation-10-on-ubuntu-14-04)
The post by Charles Green

---

### Post by Donnut on 2017-08-06
Thanks the line: ```
mks.gl.allowBlacklistedDrivers = "TRUE"
``` solved it perfectly.

---

### Post by #&amp;thj^% on 2017-08-06
Cool...and happy gaming! :)

---

### Post by miqrojamie on 2017-08-08
I had the same issue with Intel HD Graphics too, the blacklisted drivers thing fixed it. Ironically, running Windows in a VM on VMWare on Ubuntu actually works better than on Windows itself, at least from my general testing with Windows XP and Vista (the former has garbled sound, the latter is extremely slow, neither of which happens with Ubuntu as the host)

---

