---
title: "Wacom Bamboo Connect not recognized by 12.04"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fragos on 2012-04-01
The latest incarnation of the Wacom Bamboo Connect isn't recognized by 12.04. The System Settings -- Wacom Graphics Tablet said there was no tablet present despite it being pluged into a USB port. Apparently this newer device isn't supported by the Wacom driver included with 12.04. The solution to this problem is to add the following repository and install the updated driver:

sudo apt-add-repository ppa:lekensteyn/wacom-tablet
sudo apt-get update
sudo apt-get install wacom-dkms

xserver-xorg-input-wacom is also required but I believe it's already installed with 12.04. Lastly I restarted my system.

---

### Post by remake3000 on 2012-04-03
Awesome!

Thanks, **fragos**. Now my bamboo pen CTL-470 working.

---

