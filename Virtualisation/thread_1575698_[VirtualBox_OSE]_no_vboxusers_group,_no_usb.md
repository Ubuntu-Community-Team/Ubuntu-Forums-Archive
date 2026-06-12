---
title: "[VirtualBox OSE] no vboxusers group, no usb"
date: 2010-09-16
forum: Virtualisation
---

### Post by m4lte on 2010-09-16
Hi there,
I'm running a Win XP guest on Ubunutu 10.4. I installed VirtualBox OSE 3.1.6 from the repos.
I want to use USB devices from the Windows guest. I read that therefore I need to be member of the vboxusers group. However, no vboxusers group was set up during installation. I already tried reinstalling the package virtualbox-ose but still have no vboxusers group.
Does anyone know what could be the reason? Is there a way to manually set up the user group?

thanks for your help!

```
sudo usermod -aG vboxusers xxxx
usermod: group 'vboxusers' does not exist

```

**EDIT: I found out that USB is not supported in the Open Source, but only in the PUEL edition.**

---

