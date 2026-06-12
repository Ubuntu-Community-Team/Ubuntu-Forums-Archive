---
title: "Nothing in  /sys/class/udc/"
date: 2018-09-03
forum: Ubuntu, Linux and OS Chat
---

### Post by ranchu-panchu on 2018-09-03
Hello,

I try to add gadget configfs as described in:
[https://www.kernel.org/doc/Documentation/usb/gadget_configfs.txt](https://www.kernel.org/doc/Documentation/usb/gadget_configfs.txt)
Yet, I find nothing in /sys/class/udc:

user@user-VirtualBox:~/tegra$ ls /sys/class/udc/ -al
total 0
drwxr-xr-x  2 root root 0 Sep  3 00:30 .
drwxr-xr-x 58 root root 0 Sep  3 00:30 ..

I also don't have dwc2, but dwc3:
user@user-VirtualBox:~/tegra$ lsmod | grep dw
dwc3                   90112  0 
ulpi                   16384  1 dwc3
udc_core               24576  2 dwc3,libcomposite
user@user-VirtualBox:~/tegra$ 

Kernel is 4.4.50.

Thank you for any idea,
ranran

---

