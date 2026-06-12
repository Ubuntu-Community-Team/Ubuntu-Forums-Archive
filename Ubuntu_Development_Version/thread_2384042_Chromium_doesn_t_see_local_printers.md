---
title: "Chromium doesn t see local printers"
date: 2018-02-01
forum: Ubuntu Development Version
---

### Post by geolab on 2018-02-01
Hi. While firefox does it, chromium doesn t see local printers and neither I am able to set up google cloud pint with the local printers either.. any idea ?

---

### Post by tinylagarto on 2018-02-01
Are you sure you looked into the print settings in Chromium?

Can you post more information about your hardware and also the printer?

Is the package cups installed?

```
apt policy cups
```

The command above will show if cups is installed and which version. 

If it is an HP printer then you have to see that you also have hplip.

```
apt policy hplip
```

---

### Post by geolab on 2018-02-04
Thanks for advice but as I said, it s chromium that doesn t see local printers , that are already working with firefox and gnome etc. Problem was that Software app has two versions of chromium (maybe the regular and the snap version, I don t know) : i installed the one not working. The other one is working

---

### Post by deadflowr on 2018-02-04
> **geolab said:**
> Thanks for advice but as I said, it s chromium that doesn t see local printers , that are already working with firefox and gnome etc. Problem was that Software app has two versions of chromium (maybe the regular and the snap version, I don t know) : i installed the one not working. The other one is working

You can see if it's the snap version by running
```
snap list
```
that will list all installed snap packages.
fwiw

---

