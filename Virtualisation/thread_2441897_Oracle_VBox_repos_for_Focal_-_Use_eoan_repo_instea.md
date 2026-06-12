---
title: "Oracle VBox repos for Focal - Use eoan repo instead."
date: 2020-04-27
forum: Virtualisation
---

### Post by ajgreeny on 2020-04-27
I have been trying to add the VBox repos from Oracle as shown in the info at ***Debian-based Linux distributions*** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).

Currently there are no repos for focal so it is necessary at the moment to add the line for 19.10 to your sources.list file , ie, ***deb [arch=amd64] [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) eoan contrib***, using ***eoan*** instead of **_focal_**.

It is working just as it should for the time being in 20.04, and I will upgrade the repo information as soon as Oracle add a repo for focal.

---

### Post by kneutron on 2020-06-25
--Note the Virtualbox repo for focal / 20.04 is usable now.

---

