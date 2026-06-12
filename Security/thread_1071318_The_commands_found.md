---
title: "The commands found"
date: 2009-02-16
forum: Security
---

### Post by nitingarghere on 2009-02-16
The commands found in the wireless-tools package do not support WPA encryption. You need to add the wpa_supplicant application to connect using the commands. You then can only connect to WPA connections that are pre-configured in your wpa_supplicant.conf file.

---

### Post by bodhi.zazen on 2009-02-16
Yes that is true. This is how linux works, applications tend to be modular, one task per application rather then a single monolithic approach.

Exceptions occur most often with the GUI applications (gnome, kde, network manager) which are front ends ...

---

