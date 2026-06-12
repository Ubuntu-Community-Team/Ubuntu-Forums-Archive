---
title: "iPhone USB Support in VirtualBox 4"
date: 2011-01-16
forum: Virtualisation
---

### Post by ironicsky on 2011-01-16
Hi All, I am running Ubuntu 10.10 64 bit with VirtualBox 4.0.0 r69151 as my host system.

My guest system is a Windows 7 64-bit with the Guest Add'ons installed.

I am having difficulties getting my iPhone 3GS iOS 4.x (Jailbroken) to work inside the virtual environment.

My user on my computer "orion" has been added to the vboxusers group, and I have created a USB Filter with the following information:

Enable USB Controller: Yes
Enable USB 2.0 (EHCI) Controller: Yes

Filter Name: Apple Inc. iPhone [0001]
Vendor ID: 05ac
Product ID: BLANK
Revision: BLANK
Manufacturer: BLANK
Product: BLANK
SERIAL NO: BLANK
Port: BLANK
Remote: NO

I read on another forum it is best to leave everything blank except the Vendor ID so that multiple iPhones/iPods can be synced through based on different product ID's and serial #'s.

I have also added the following line to etc/fstab in hopes of it working

none            /proc/bus/usb   usbfs   devgif=123,devmod664    0       0
ID 123 is the ID of the vboxuser group

In the device menu under USB my iPhone is check marked.

Windows detects that a USB device is being plugged in and unplugged, and in the Device Manager i have an "Apple Mobile Device Driver", which unfortunately is failing to load. (Yellow Warning Symbol).

I have attempted to uninstall and reinstall the latest 64-bit version of iTunes from the Apple website, but nothing I do seems to allow the device to successfully connect to windows.

Has anyone gotten this to work?

ironicsky

---

### Post by ironicsky on 2011-01-16
I resolved it. After reading the Virtual Box 4.0 help doc's, it turns out you need an expansion pack for USB 2.0 to work, which is really, really stupid considering... Anyway, I installed the extension pack and everything is fine :-)


> **ironicsky said:**
> Hi All, I am running Ubuntu 10.10 64 bit with VirtualBox 4.0.0 r69151 as my host system.

My guest system is a Windows 7 64-bit with the Guest Add'ons installed.

I am having difficulties getting my iPhone 3GS iOS 4.x (Jailbroken) to work inside the virtual environment.

My user on my computer "orion" has been added to the vboxusers group, and I have created a USB Filter with the following information:

Enable USB Controller: Yes
Enable USB 2.0 (EHCI) Controller: Yes

Filter Name: Apple Inc. iPhone [0001]
Vendor ID: 05ac
Product ID: BLANK
Revision: BLANK
Manufacturer: BLANK
Product: BLANK
SERIAL NO: BLANK
Port: BLANK
Remote: NO

I read on another forum it is best to leave everything blank except the Vendor ID so that multiple iPhones/iPods can be synced through based on different product ID's and serial #'s.

I have also added the following line to etc/fstab in hopes of it working

none            /proc/bus/usb   usbfs   devgif=123,devmod664    0       0
ID 123 is the ID of the vboxuser group

In the device menu under USB my iPhone is check marked.

Windows detects that a USB device is being plugged in and unplugged, and in the Device Manager i have an "Apple Mobile Device Driver", which unfortunately is failing to load. (Yellow Warning Symbol).

I have attempted to uninstall and reinstall the latest 64-bit version of iTunes from the Apple website, but nothing I do seems to allow the device to successfully connect to windows.

Has anyone gotten this to work?

ironicsky

---

### Post by ironicsky on 2011-01-16
I resolved it. After reading the Virtual Box 4.0 help doc's, it turns out you need an expansion pack for USB 2.0 to work, which is really, really stupid considering... Anyway, I installed the extension pack and everything is fine :-)


> **ironicsky said:**
> Hi All, I am running Ubuntu 10.10 64 bit with VirtualBox 4.0.0 r69151 as my host system.

My guest system is a Windows 7 64-bit with the Guest Add'ons installed.

I am having difficulties getting my iPhone 3GS iOS 4.x (Jailbroken) to work inside the virtual environment.

My user on my computer "orion" has been added to the vboxusers group, and I have created a USB Filter with the following information:

Enable USB Controller: Yes
Enable USB 2.0 (EHCI) Controller: Yes

Filter Name: Apple Inc. iPhone [0001]
Vendor ID: 05ac
Product ID: BLANK
Revision: BLANK
Manufacturer: BLANK
Product: BLANK
SERIAL NO: BLANK
Port: BLANK
Remote: NO

I read on another forum it is best to leave everything blank except the Vendor ID so that multiple iPhones/iPods can be synced through based on different product ID's and serial #'s.

I have also added the following line to etc/fstab in hopes of it working

none            /proc/bus/usb   usbfs   devgif=123,devmod664    0       0
ID 123 is the ID of the vboxuser group

In the device menu under USB my iPhone is check marked.

Windows detects that a USB device is being plugged in and unplugged, and in the Device Manager i have an "Apple Mobile Device Driver", which unfortunately is failing to load. (Yellow Warning Symbol).

I have attempted to uninstall and reinstall the latest 64-bit version of iTunes from the Apple website, but nothing I do seems to allow the device to successfully connect to windows.

Has anyone gotten this to work?

ironicsky

---

### Post by gianluca.pettinello on 2011-03-06
Thanks a lot worked also for me!

---

### Post by DoctorVell on 2012-05-26
Where do I find the expansion pack for this support?  I want to hook up my iPhone 4 and sync it up :)

---

### Post by Habitual on 2012-05-26
> **DoctorVell said:**
> Where do I find the expansion pack for this support?  I want to hook up my iPhone 4 and sync it up :)

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by DoctorVell on 2012-05-27
> **Habitual said:**
> [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

I found it, thank-you very much!

---

### Post by Habitual on 2012-05-28
Glad to be of help!

---

### Post by jimbob80 on 2012-09-30
Hello,

I have done everything mentioned here so far:

I am running Windows 7 64bit within Virtualbox. I have downloaded and installed the extension pack, added a usb filter for iPhone in VB, iPhone is now seen and installed within Windows. I can see it and open the photos etc.

However, iTunes cannot see the iPhone.

Any ideas?

---

