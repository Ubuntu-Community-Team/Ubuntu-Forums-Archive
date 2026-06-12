---
title: "Touchpad: Synaptics driver is not installed (or is not used)"
date: 2016-08-17
forum: Ubuntu Studio
---

### Post by zangetsu94 on 2016-08-17
On my Asus PC, with Kubuntu 14.04,  I can't configure the touchpad because of this message: "*Touchpad: Synaptics driver is not installed (or is not used)*"

Here's a picture:
[http://i67.tinypic.com/339sv8w.png](http://i67.tinypic.com/339sv8w.png)
What will I do with this driver?

---

### Post by zangetsu94 on 2016-08-20
I solved updating kernel to 4.4 version:
```
sudo apt-get install  linux-generic-lts-xenial
```
After a reboot, if thouchpad still doesn't work, you should activate that with this command:
```
synclient TouchpadOff=0
sudo reboot
```

---

