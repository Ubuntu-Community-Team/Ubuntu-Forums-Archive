---
title: "Ubuntu 10.10 in VirtualBox 3.2.8"
date: 2010-10-07
forum: Virtualisation
---

### Post by noorez on 2010-10-07
Hi,

I wanted to try ubuntu 10.10rc in a virtualbox 3.2.8 PUEL. I did manage to install it but when I tried to install the guest additions, it told me that the X versions did not mach, so the drivers would not be installed. However, I found this workaround:

Within the virtual machine do this:
sudo apt-get install virtualbox-ose-guest-x11
which also installs virtualbox-ose-guest-utils

If I install OSE versions of the guest additions, will I no longer be able to use the utilities that are included in the PUEL version and not the OSE version even though I am using the PUEL edition to host ubuntu?

---

### Post by P4man on 2010-10-07
I doubt it. The guest additions are just an ISO with drivers. It doesnt look like it will install virtualbox ose itself.

---

