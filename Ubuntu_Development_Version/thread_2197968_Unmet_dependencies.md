---
title: "Unmet dependencies"
date: 2014-01-06
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2014-01-06
I was trying to upgrade from saucy to trusty(amd 64 bit) when my upgrade hit errors. It showed 14 broken packages first. Most of them were resolved using synaptic. But a particular one i'm unable to solve. Tried apt-get -f install and dpkg --configure -a but they continue to show same error. The error is given below:

[HTML]

libqt5sensors5-dev: Depends: libqt5sensors5 (= 5.1.1+dfsg-2ubuntu3) but 5.1.1+dfsg-2ubuntu3 is installedqtsensors5-dev: Depends: libqt5sensors5 (= 5.0~git20130507-0ubuntu3) but 5.1.1+dfsg-2ubuntu3 is installed
[/HTML]

Please help. A little urgent. Have to finish upgrade by tonight.

---

### Post by d-cosner on 2014-01-06
There was some problems yesterday with some packages. Try the upgrade again and see it it is able to complete this time.

---

### Post by krishnan t s on 2014-01-06
Managed to solve it an hour after posting here :) Net stopped working after that. I removed the package in question and upgrade finished successfully. Its still showing as 13.10 in About this computer but lsb_release -a shows it correctly as trusty. Hope it gets fixed soon :)
Thanks and have a great day ahead :)

---

### Post by grahammechanical on 2014-01-07
Logos and labels do not get changed until much later in the development cycle. I have been running Trusty Tahr since the first week after the release of Saucy Salamander and the login screen is still saying 13.10 as is the Details Overview page. But Grub knows that it is 14.04 (development branch). This is just the way things are during the development cycle. 

Regards.

---

