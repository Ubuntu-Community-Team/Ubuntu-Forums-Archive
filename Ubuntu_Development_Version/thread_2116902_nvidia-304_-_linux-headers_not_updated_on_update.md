---
title: "nvidia-304 - linux-headers not updated on update"
date: 2013-02-17
forum: Ubuntu Development Version
---

### Post by Cheltspy on 2013-02-17
Linux headers are not being installed on update.

So nvidia-304 fails on the install because the the new headers are not installed.

My current work around is after update and before restart.

apt-get install linux-headers-[new kernel]

apt-get remove nvidia-304

apt-get install nvidia-304

---

### Post by Kow on 2013-02-17
Do you have linux-headers-generic installed?

Using the development repositories, it's possible your local copy of the repos had the new linux-image-generic but linux-headers-generic had yet to be updated. One of the perks of using devel. :)

---

