---
title: "Checking driver"
date: 2014-07-15
forum: Ubuntu Studio
---

### Post by alan33 on 2014-07-15
After installing the drivers for a satellite tuner card I placed this code ```
dmesg | grep frontend
``` into the terminal but nothing happens it did work in 12.04 but not now in 14.04 is there another way to run this line in Ubuntu Studio 14.04

---

### Post by ubudog on 2014-07-15
Do these commands help?
```
sudo lshw
sudo lsmod
```

---

### Post by alan33 on 2014-07-16
Thanks but no they only show pc spec thanks
Regards Alan

---

### Post by ubudog on 2014-07-16
Which satellite tuner card are you installing?

---

