---
title: "Help! VirtualBox Install Error"
date: 2007-11-15
forum: Virtualisation
---

### Post by Malh on 2007-11-15
I need to install VirtualBox with USB support because I had the OSE version but it lacks USB support.  When I attempt to install VirtualBox, I get the same error every time:

```
E: /var/cache/apt/archives/virtualbox_1.5.2-25433%5fUbuntu%5fgutsy_i386.deb: trying to overwrite `/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.22-14-generic
```

---

### Post by maybeway36 on 2007-11-15
Uninstall the OSE version first. You VMs are in ~/.VirtualBox so they will stay.

---

### Post by Malh on 2007-11-15
> **maybeway36 said:**
> Uninstall the OSE version first. You VMs are in ~/.VirtualBox so they will stay.

I already uninstalled the OSE version.

---

### Post by Malh on 2007-11-15
Wow, wicked stupid mistake, I completely forgot to uninstall the OSE modules.

---

### Post by qamelian on 2007-11-15
> **Malh said:**
> I already uninstalled the OSE version.

Did you also uninstall the package that is being complained about:
> virtualbox-ose-modules-2.6.22-14-genericThe problem appears to be that you only uninstalled the Virtualbox application and not the Virtualbox kernel module(s).

EDIT: Not quick enough I guess. You figured it out while I was still typing!

---

