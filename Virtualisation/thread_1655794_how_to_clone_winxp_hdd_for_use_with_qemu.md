---
title: "how to clone winxp hdd for use with qemu"
date: 2010-12-30
forum: Virtualisation
---

### Post by produnis on 2010-12-30
Hi folks, 
I am trying to clone my Windows-HDD in order to run the system using qemu.

I booted my Win-Laptop using the Ubuntu-Live CD. The original HDD (which I want to clone) is located at /dev/sda. 
Then I plugged an external Drive (named "Platte") to it, opened a terminal and typed in:
```
sudo dd if=/dev/sda of=/media/Platte/MeinImage.img
```

This gives me a 40GB image.
after that, I converted the image using
```
sudo qemu-img convert -O qcow /media/Platte/MyImage.img /media/Platte/MyQEMUImage.img
```

If I now try to boot from the image using
```
qemu -hda /media/Platte/MyQEMUImage.img
``` 
or
```
qemu -hda /media/Platte/MyImage.img
``` 
it says:
```
Cannot boot from device, (error 0004)
```

Does anyone know how to fix that?
Or does anyone know an alternative way to clone a windwos-hdd for qemu?

---

### Post by BbUiDgZ on 2010-12-30
I use [THIS]("http://ping.windowsdream.com/") to image and deploy windows systems at work

---

