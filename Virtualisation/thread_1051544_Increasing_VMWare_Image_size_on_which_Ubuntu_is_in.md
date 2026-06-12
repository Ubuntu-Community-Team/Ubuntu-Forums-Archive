---
title: "Increasing VMWare Image size on which Ubuntu is installed."
date: 2009-01-26
forum: Virtualisation
---

### Post by exoid on 2009-01-26
Hello,

I created a Ubuntu VMWare instance on my VMWare Server 2.0 however the allocated space that was assigned is not large enough and was wondering if there is a way to expand this without having to re-create the vmware image and re-install Ubuntu 8.0X.

Any help would be appreciated; thank you.

---

### Post by Dedoimedo on 2009-01-27
A safeway of doing it:

Image the guest. Create a new virtual machine with bigger disk. Image back into the guest.

Another way, assign a second hard disk and mount certain partitions, like /home to this new disk ...

Dedoimedo

---

