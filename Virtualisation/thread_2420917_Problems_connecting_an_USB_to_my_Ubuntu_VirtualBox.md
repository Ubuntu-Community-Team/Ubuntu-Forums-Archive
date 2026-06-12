---
title: "Problems connecting an USB to my Ubuntu VirtualBox"
date: 2019-06-13
forum: Virtualisation
---

### Post by maalfonso on 2019-06-13
Hello,

First of all, I have to say I am new in the Ubuntu world. 

I have installed a Virtual machine with Ubuntu using VirtualBOX. Everything works fine except when I try to connect a USB devide in my virtual machine.

When I click in the USB icon in the bottom right part of the ubuntu desktop I can find the usb devices connected to my computer (see attached picture). However, when I click in any of them, they don't connect to my cirtual machine, so I can't use them. In addition, no error is displayed in the virtual machine.

On the other hand, the mouse and the keyboard work fine in the virtual machine and they are connected to the same USB hub than the rest of devices.

I try to change the USB port, to include the devices in the virtual machine configuration, etc. but nothing worked. If someone would have a solution to my problem, it would be awsome because I have no more ideas.

Thank you very much in advance,

---

### Post by ajgreeny on 2019-06-13
Have you installed the guest additions package which will probably help with USB connections?

You can get the package from [https://download.virtualbox.org/virtualbox/6.0.8/Oracle_VM_VirtualBox_Extension_Pack-6.0.8.vbox-extpack](https://download.virtualbox.org/virtualbox/6.0.8/Oracle_VM_VirtualBox_Extension_Pack-6.0.8.vbox-extpack) butthis assumes you have the latest VBox version; if you have a different version you MUST use the guest additions package for that version.

In my VBox VM Settings the list of USB devices  shows a tick box against each one in order to connect or disconnect the device but you do not show that in your screenshot; does that show on your VM?

---

### Post by SeijiSensei on 2019-06-13
USB technologies have proprietary features that make it impossible to distribute open-source drivers to use them in a virtual environment. That's why you need to install the extension pack.

---

### Post by ajgreeny on 2019-06-13
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by maalfonso on 2019-06-13
Thank you for your answer Ajgreeny.

Yes, I have installed the guest additions package, and its version is the same than the VirtualBOX software (6.0.8).

I  only have checkboxes in the VirtualBOX administrator page (USB tab),  but in the Ubuntu virtual machine, there are no checkboxes.

Moreover,  when I connect the virtual machine and try to connect any USB device,  no error appears and this usb device disappears from the device manager  in Windows. It is like the virtual machine tries to connect the USB  devices but it is not able. 
In this state I can't use the USB device neither in the virtual machine nor in Windows until I switch off the virtual machine. 

Any other idea?

Thank you,

---

### Post by ajgreeny on 2019-06-13
In the VBox manager for that VM what setting do you have it set to? I always use USB2 and have found that USB3 always fails; I've no Idea why and it doesn't really matter as I have no USB3 devices to attach.

---

### Post by maalfonso on 2019-06-14
Hi Ajgreeny,
Thank you for your answer.
I tried with the 3 USB controllers: 1.1, 2.0 and 3.0 and it doen't work with any of them.

---

