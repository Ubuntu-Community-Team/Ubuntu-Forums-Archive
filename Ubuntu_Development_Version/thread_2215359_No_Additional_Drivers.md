---
title: "No Additional Drivers"
date: 2014-04-06
forum: Ubuntu Development Version
---

### Post by wallacegalloway on 2014-04-06
I am running a Nvidia GTX 750 Ti video card, but when I click on Additional drivers is says none are available. I understood that Ubuntu 14.04 has the new nvidia-331.38 drivers in the repos.

[http://news.softpedia.com/news/Ubuntu-14-04-Repositories-Now-Have-the-Latest-NVIDIA-331-38-Driver-422426.shtml](http://news.softpedia.com/news/Ubuntu-14-04-Repositories-Now-Have-the-Latest-NVIDIA-331-38-Driver-422426.shtml)

---

### Post by cariboo on 2014-04-06
Open System Settings -> Software & Updates, and make sure all the repositories are enabled, except for Proposed, you should be prompted to run an update, then the drivers will be available.

---

### Post by grahammechanical on 2014-04-06
On my Trusty Tahr Additional Drivers offers me Nvidia 331.38 and Nvidia 331.38-updates. Are you online when you open Additional Drivers? It takes a several seconds for the utility to search for the drivers.

---

### Post by wallacegalloway on 2014-04-06
Yup to both posters. All I get is "No Additional Drivers Available".

---

### Post by buzzingrobot on 2014-04-06
Nvidia's site says support for the GTX 750ti was added in 334.21.

---

### Post by wallacegalloway on 2014-04-06
Ah...I don't see the 334.21 drivers in the repos only earlier versions. Guess I'll have to wait.

---

### Post by Yellow Pasque on 2014-04-06
You may have to use xorg-edgers PPA, because Canonical is not planning to offer nvidia 334 package in Trusty: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753)

---

