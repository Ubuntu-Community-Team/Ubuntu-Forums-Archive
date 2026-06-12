---
title: "(XEN) Not enough memory to relocate the dom0 kernel image"
date: 2012-08-22
forum: Virtualisation
---

### Post by cihantunc on 2012-08-22
Hi all! 

I have installed XEN on the system based on the following link: 

[https://help.ubuntu.com/community/XenProposed](https://help.ubuntu.com/community/XenProposed) 

However, when I boot the XEN kernel, I get "(XEN) Not enough memory to relocate the dom0 kernel image" and the system stalls. I'm attaching the screen. And, I have 24GB memory so I believe that there is something wrong. Any ideas?

---

### Post by Dy1anW on 2012-08-25
> **cihantunc said:**
> Hi all! 

I have installed XEN on the system based on the following link: 

[https://help.ubuntu.com/community/XenProposed](https://help.ubuntu.com/community/XenProposed) 

However, when I boot the XEN kernel, I get "(XEN) Not enough memory to relocate the dom0 kernel image" and the system stalls. I'm attaching the screen. And, I have 24GB memory so I believe that there is something wrong. Any ideas?

Interesting. I followed the same page as well and I couldn't get much further than the reboot stage. At that point, sometimes Xen will boot, sometimes it won't and sometimes when it does boot I find out that xend isn't even running. On the two occasions when it did boot and xend was running, I couldn't get the network up and running.

I've wondered if there's a problem with the stock kernel, so will try and compile it from source later on.

---

### Post by cihhan on 2012-08-25
I don't think that the problems I'm facing are because of the settings the webpage is giving. It is more likely there is something wrong with the XEN packages.

---

### Post by Dy1anW on 2012-08-26
Just an update; I compiled a custom configured 3.6.0-rc3 kernel (previously using 3.2.0-29; is that the kernel you're having problems with as well?) and xend seems to be running fine... well, as far as I can tell. Still working through the bridging right now, but otherwise so far so good. I'm using the stock Xen hypervisor (4.1.2) since, for some unknown reason, 4.1.3 seems to stall when downloading from git during 'make'.

---

### Post by cihhan on 2012-08-27
I have not compiled the kernel myself. I have been using the provided xen hypervisor and tools from apt-get. What is your system?

---

### Post by Dy1anW on 2012-08-29
> **cihhan said:**
> What is your system?
'tis an i7 based laptop, 16G RAM, Nvidia GT 650M... which is completely useless in Ubuntu as it uses Optimus (damn you Nvidia!). Bumblebee makes no difference, but am keeping my hopes up for later releases or proprietary drivers.

Update: Got Bumblebee working. Woo! Look at that baby fly!

---

