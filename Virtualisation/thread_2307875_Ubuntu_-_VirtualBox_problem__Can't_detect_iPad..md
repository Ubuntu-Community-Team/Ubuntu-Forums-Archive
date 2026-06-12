---
title: "Ubuntu - VirtualBox problem // Can't detect iPad."
date: 2015-12-29
forum: Virtualisation
---

### Post by robertt3 on 2015-12-29
IPad Air (WifI)
I've managed to download Windows 8.iso & run it on VirtualBox after a long time of trying. Anyway, I've set virtualisation & all that up and I want to connect an iPad to use it on VirtualBox but I can't get it work.
ive installed the extensions pack

thanks

---

### Post by slickymaster on 2015-12-29
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by ajgreeny on 2015-12-29
How does the iPad connect to your host; USB?  I have no apple hardware so I'm a true apple-virgin as far as connections of this sort are concerned.  I do, however, use WinXP in VBox simply to update a satnav device and I have to go through a USB connection procedure each time in order to remove it from the host OS and connect it to the guest.

Try going to the Devices menu in your Win7 guest's VBox menubar and activate the specific USB connection for the iPad.

If it connects by other than USB I'm afraid I have no clue.

---

### Post by robertt3 on 2015-12-29
It connects via USB port.
ive tried with the menu bar but it doesn't find it.

---

### Post by MAFoElffen on 2015-12-29
Of course this needs to be in current versions of virtualbox, but:
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

As an explanation, you need to add yourself to the "vboxusers" group on the Linux host machine, before your can configure usbdevices within virtualbox itself.
```

sudo adduser <username> vboxusers
# OR #
sudo usermod -a -G vboxusers <username>

```
Note-- While substituting <username> with your own username...

Then logout / log back in to pick up the changes. Confirm, check to make sure your are added via:
```

groups <username>

```
Look for vboxusers listed in the groups you have membership to... 

Plug your target device in the first time, previous to restarting your VM... From a terminal session on your host, ensure your host sees your target usb device:
```

sudo lsusb

```
Then start VirtualBox and setup USB in your VBox settings for that VM...

After configuring USB for your VM ... Confirm by opening a terminal in your VM and using:
```

VBoxManage list usbhost | more

```
and look for your device listed in the output as a device.

---

### Post by robertt3 on 2015-12-30
Thanks for the post but I'm stuck after sudo lsusb..
Here's what terminal repeats;
Bus 002 Device 007: ID 05ac:12ab Apple, Inc. iPad 4/Mini1
Bus 002 Device 004: ID 046d:c31f Logitech, Inc. 
Bus 002 Device 003: ID 1d57:fa60 Xenta 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 004: ID 0408:3008 Quanta Computer, Inc. 
Bus 001 Device 003: ID 04f2:b1e7 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm not sure what to do next as the VM can't find any USB device. Thanks.

---

### Post by ajgreeny on 2015-12-30
Have you definitely installed the VBox guest additions in the Win7 guest OS as well as the extensions in VBox itself?

---

