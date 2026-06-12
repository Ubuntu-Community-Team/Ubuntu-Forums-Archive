---
title: "Kernel Specifics"
date: 2015-09-21
forum: Ubuntu Phone and Tablet
---

### Post by ahmed-guellil on 2015-09-21
Hi,

In order to help an Android developer porting his application to Ubuntu Touch, I need some information about the kernel used.

However, I haven't got the chance or time or money to buy a Ubuntu Phone, so it would be great if anyone could give me the following details:
- the device they use
- the output of **# find /sys**
- the output of **# cat /proc/version**

For those who want to know, the application is called [DriveDroid]("https://play.google.com/store/apps/details?id=com.softwarebakery.drivedroid&hl=fr") and tries to gain access to the *USB Mass Storage* mode, so you can use your smartphone as if it was a USB key, thus permitting to launch live OSes at startup (for example).

Thanks :)

---

### Post by grahammechanical on 2015-09-22
Ubuntu Phone is at present based upon the Ubuntu 15.04 code base and 15.04 uses the Linux 3.19 kernel series. There are rumours that Ubuntu Phone will skip the upgrade to the 15.10 code base and be re-based on the 16.04 code when it is released. I am not sure if this rumour is accurate. I doubt it. 

Ubuntu 15.10 will use the Linux 4.2 series. And at some point Ubuntu Phone will have to be re-based to 15.10 and then to 16.04. Whether all this will be passed on to the user or not, only time will tell.

Do not assume that Ubuntu Phone follows the same folder and file system as desktop Ubuntu. I do not think that it does. I know that Ubuntu Personal does not. I advise your friend to do his development work on Ubuntu and install the Ubuntu SDK and the Ubuntu emulator.

[https://developer.ubuntu.com/en/start/ubuntu-sdk/](https://developer.ubuntu.com/en/start/ubuntu-sdk/)

[URL="https://developer.ubuntu.com/en/apps/sdk/tutorials/using-the-ubuntu-emulator/"]https://developer.ubuntu.com/en/apps/sdk/tutorials/using-the-ubuntu-emulator/

[/URL]

---

### Post by handaxe on 2015-09-23
The skipping of 15.10 is more than a rumor but a stated intent. There remains discussion of the implications and way forward. The source here is the ubuntu-phone mailing list.

---

### Post by ahmed-guellil on 2015-09-23
Thanks for your input. I'll inform the developer as soon as possible.

---

### Post by frozencow2 on 2015-10-01
It isn't really about the filesystem or directory structure that is used. The functionality that we're after is the USB-gadget functionality that resides in the Linux/Android kernel. It is used in the kernel of a client-side USB device (like a phone) to emulate/simulate various types of USB devices (like MTP and USB Mass Storage). USB Mass Storage has the ability to make the phone look like a CD-rom drive or USB thumbdrive, in turn allowing people to boot a Linux LiveCD from their phone onto a PC the phone is connected to.

The functionality has no dependencies on the actual distribution itself. I understand that to develop application for Ubuntu that Ubuntu is preferred to develop in, but I just need to know whether the USB-gadget and USB Mass Storage functionality is actually in the kernel that you're using on Ubuntu Phone.

Is the kernel that is used on the Ubuntu Phone based on the kernel from Android or is it based on the Ubuntu Desktop kernel?

---

