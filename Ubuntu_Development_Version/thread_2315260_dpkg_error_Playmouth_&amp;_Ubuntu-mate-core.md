---
title: "dpkg error Playmouth &amp; Ubuntu-mate-core"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by kc1di on 2016-02-27
Keep getting error messages on upgrades that 
```
dpkg: error processing package lightdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-mate-text:
 plymouth-theme-ubuntu-mate-text depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-mate-text (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-mate-core:
 ubuntu-mate-core depends on lightdm; however:
  Package lightdm is not configured yet.
 ubuntu-mate-core depends on plymouth-theme-ubuntu-mate-text; however:
  Package plymouth-theme-ubuntu-mate-text is not configured yet.

dpkg: error processing package ubuntu-mate-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-mate-logo:
 plymouth-theme-ubuntu-mate-logo depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-mate-logo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.9.2-3ubuntu10); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth (= 0.9.2-3ubuntu10); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-8-generic
Errors were encountered while processing:
 plymouth
 lightdm
 plymouth-theme-ubuntu-mate-text
 ubuntu-mate-core
 plymouth-theme-ubuntu-mate-logo
 plymouth-label
 plymouth-theme-ubuntu-text

```

anyone have fix yet?
Thanks

---

### Post by zika on 2016-02-27
```
sudo apt install -f
```

---

### Post by kc1di on 2016-02-27
Thanks Zika,
That did not clear the error :(
Had tried that before

---

### Post by v3.xx on 2016-02-27
4.4.0-8-generic ??

Do you have xenia-proposed enabled?

Edit
Just did my updates and there was a kernel upgrade out there, so never mind.

---

### Post by zika on 2016-02-27
What gives```
sudo dpkg --configure --simulate plymouth
``````
sudo dpkg --configure --simulate -a
```? Be carefull when answering any possible question, but, since dry-run is invoked there should be none...

---

### Post by kc1di on 2016-02-27
> **v3.xx said:**
> 4.4.0-8-generic ??

Do you have xenia-proposed enabled?

Edit
Just did my updates and there was a kernel upgrade out there, so never mind.

Thanks - I have it enabled and have the latest kernel update. :)

---

### Post by kc1di on 2016-02-27
Zika - Dry run looked good but still errors when trying to upgrade or install.  will wait a while see if it gets sorted out .

---

