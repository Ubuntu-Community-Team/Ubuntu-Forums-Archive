---
title: "install ubuntu 8.04 server in VirtualBox"
date: 2008-07-14
forum: Virtualisation
---

### Post by bogdanbiv on 2008-07-14
1) Host Operating system:
KUbuntu Hardy 8.04, KDE 3.5.9, 
32bit edition (I think it's 32 bit)

Kernel:
$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

2) VirtualBox 1.6.2 downloaded from Sun Microsystems

3) Guest Operating system:
Ubuntu 8.04 Server 32 bit edition

I installed Ubuntu guest with no trouble, but when I rebooted the virtual machine I got the message in the screenshot:
"This kernel requires the following features not present on the CPU
0:6
Unable to boot - please use a kernel that is appropiate for your CPU"

---

### Post by prshah on 2008-07-14
> **bogdanbiv said:**
> 

"This kernel requires the following features not present on the CPU
0:6
Unable to boot - please use a kernel that is appropiate for your CPU"

I have the same problem; I suspect that it's due to PAE support, which VirtualBox lacks (or used to) but VMWare has.

I was informed that PAE support is now available in VirtualBox as well, but I still face this problem. 

In the meantime, you can recover from this situation by booting into recovery mode (press ESC during GRUB countdown) and then installing the generic kernel.

---

### Post by bodhi.zazen on 2008-07-14
Yes, and you can also consider installing JEOS

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

To be honest, I am not sure if it works with virtualBox or not, but it is a very nice virtual appliance.

[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)

---

### Post by bogdanbiv on 2008-07-15
PAE is as I remember related to 64bit PCs and Operating systems

The Host OS is generic, 32bit: 2.6.24-19-generic
Guest OS (Ubuntu 8.04 Server 32 bit edition) has the 2.6.24-16-server kernel.
As far as I understand you suggest trying to replace the guest kernel with 2.6.24-16-generic? Am I correct?

UPDATE: the guest machine does not boot even in recovery mode - same error. This looks pretty bad - others may have trouble with it too.


Thanks! I'll try my luck with JeOS too. 

I'll come back to post my results with both suggestions.

---

### Post by bodhi.zazen on 2008-07-15
No, PAE is for 32 bit CPU, it allows them to access > 4 Gb RAM.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

And, yes you need to install the generic kernel or JEOS.

---

### Post by caco on 2008-07-24
Hello, I had the same problem with Hardy server guestOS on a 32-bit Hardy desktop hostOS. I am running Virtualbox 1.6.2

All you need to do is enable the PAE support for the virtual machine. That is what I did, so simple. No big download of a new kernel, OK?

ps Info or help was from [http://sazwqa.wordpress.com/2008/06/11/installing-ubuntu-804-server-on-virtualbox/](http://sazwqa.wordpress.com/2008/06/11/installing-ubuntu-804-server-on-virtualbox/)
Compliment to them:)

---

### Post by jtesolin on 2008-07-24
> **caco said:**
> ps Info or help was from [http://sazwqa.wordpress.com/2008/06/11/installing-ubuntu-804-server-on-virtualbox/](http://sazwqa.wordpress.com/2008/06/11/installing-ubuntu-804-server-on-virtualbox/)
Compliment to them:)

Excellent! Thanks! Worked like a charm!

---

### Post by prshah on 2008-07-24
> **caco said:**
>  I am running Virtualbox 1.6.2


Virtual Box OSE 1.5x from the repositories does not have this option. Anyone have any suggestions as to whether I should switch to the non-OSE version? The term "free for personal use" is rather vague...

---

### Post by caco on 2008-07-25
I suggest you get the Sun xVM 1.6.2 version, the one you presently have don't have that feature

---

