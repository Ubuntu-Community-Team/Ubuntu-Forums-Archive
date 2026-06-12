---
title: "VirtualBox 3.2.0 on Netbook Remix 10.04"
date: 2010-09-06
forum: Ubuntu Moblin Remix
---

### Post by MNez on 2010-09-06
There is no possibility to use USB devices on Virtual OS. for example, on my virtual Windows 7.

Previously I used only Windows version of VirtualBox and there were a menu item to connect USB device to virtual OS. Here, on Linux version there is nothing like this.

What should I do?..

Thanks.

---

### Post by hsoulen on 2010-09-10
> **MNez said:**
> There is no possibility to use USB devices on Virtual OS. for example, on my virtual Windows 7.

Previously I used only Windows version of VirtualBox and there were a menu item to connect USB device to virtual OS. Here, on Linux version there is nothing like this.

What should I do?..

Thanks.

You will probably find more assistance with this issue in the VBox forums but lets see if this will help:


[LIST=1]
[*]Do you have guest additions installed in the Guest OS (Windows 7 in this case)?
[*]Have you added USB support in the Machine Settings for that guest in VBox?
[*]Have you edited permissions in Linux for access to USB devices? This one gets missed a bunch as it is not required for VBox Windows Hosts. Check this link for some details on how to do this: [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)
[/LIST]
Good luck!

Hank

---

### Post by cariboo on 2010-09-12
IF you use the version of virtualbox from [here]("http://www.virtualbox.org/") and install the guest additions, you will be able to use the usb ports.

---

