---
title: "VirtualBox with mainline (upstream) kernel - how to?"
date: 2019-03-05
forum: Virtualisation
---

### Post by dinkidonk on 2019-03-05
My system has a Raven Ridge APU (Ryzen 2400G) as it's brain and due to this I have to use newer amdgpu firmware (18.50) + a newer kernel (4.20) to get (K)Ubuntu 18.04 to run stable. But this combo will not allow me to run VirtualBox from repos because it depends on the stock kernel. What are the steps - if possible - to mitigate this?

---

### Post by lammert-nijhof on 2019-03-05
Download the deb file from the Oracle Virtualbox site and install that one by double clicking it. Virtualbox 6.04 has been adapted to Linux 4.20. Virtualbox will warn you if there are new versions available or you can set the ppa as specified by Oracle. Don't forget to load the extension pack too.

---

