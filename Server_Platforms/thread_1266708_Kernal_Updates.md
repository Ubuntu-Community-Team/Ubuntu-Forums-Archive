---
title: "Kernal Updates"
date: 2009-09-14
forum: Server Platforms
---

### Post by FZR_Rider on 2009-09-14
Does anyone know how to update the kernal in Ubuntu Server 9.04?  I've tried apt-get update and then apt-get upgrade.  It definitely updates some packages, but I'm still running on the .11 kernal. Is the latest kernal for the server edition the same as the desktop edition?  Thank you!!

---

### Post by windependence on 2009-09-15
First find out what kernel you are running:

```
sudo uname -r
```

Then, find the available kernel images:

```
sudo apt-cache search kernel-image  
```

Now, install the image you want to upgrade to:

```
sudo apt-get install kernel-image-x.x.x-xx
```

Good luck!

-Tim

---

### Post by sherl0k on 2009-09-15
After you upgrade the kernel you need to reboot, unless you're using ksplice. If you never reboot after upgrading the kernel, the upgraded version won't take effect.

---

### Post by confusedstingray on 2009-09-15
i don't know if this is any help but here is the lastest kernel 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/)

---

### Post by FZR_Rider on 2009-09-15
I finally got my kernel updated!!  Thanks to everybody for their help!!

---

