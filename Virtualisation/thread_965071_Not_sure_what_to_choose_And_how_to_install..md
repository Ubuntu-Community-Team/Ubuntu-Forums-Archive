---
title: "Not sure what to choose And how to install."
date: 2008-10-31
forum: Virtualisation
---

### Post by kiloraw on 2008-10-31
Hello I am new to Ubuntu, but love it!! You can thank yourselfs (ubuntu community) and Vista for making me stick with open source. 
My problem is I need Windows for school since only certain software will run under xp. I will not reinstall Vista, so I well virtualize. But which virtual software should I use? Virtual box, Vmware workstation(already have license for), VMware Server(do I have to pay for this?). Then I see all these problems with Vmware, with the any any updates and so fourth. I all need is a really good tutorial that shows each command I need to put into the terminal, including any other install's for the software that is recommend for me. I know their is plenty of links, for this but I am afraid of which one to try. ANy help is great

---

### Post by H-N7 on 2008-10-31
I'd recommend VirtualBox , great performance.
You can install the Open Source Edition directly from Synaptic (search for virtualbox by name), or download the .deb package from their website. (The proprietary version have some features that I don't need like USB support and such..).

You'll just need to type one or two commands for it to work. One for setting the VirtualBox kernel module[1], and the other for adding the current user to the vboxusers group. (VirtualBox will complain and give u the commands needed anyway :) ).

After that, everything is straight forward - I think- , creating the new machine, new disk image, then installing the OS which is the same as installing it on a real machine.

----Optional----
The last step after installing Windows inside VirtualBox is Installing VirtualBox Additions from the "Device" menu, this will provide more seamless integration with your mouse and better resolution for the OS inside the Virtual Machine.
----/Optional----

---

### Post by kiloraw on 2008-10-31
Thanks for the reply, but is Virtual box as stable as VMware? ANd can I hook up peripherals through usb and they work fine? ex: blackberry, external harddrives?

---

### Post by levelup on 2008-10-31
is really useful for me

---

### Post by H-N7 on 2008-10-31
I didn't try VMWare, but VirtualBox is stable and fast.
I didn't try the USB support too, but I guess it should work fine with almost no effort (like other VBox features). You can try VirtualBox and then remove it if it doesn't work for you, nothing to lose here except time for installing Windows inside the Virtual Machine.

---

### Post by nyp4life on 2008-11-04
I haven't tried either.. also new to linux, but apparently you can flash firmware to Motorola phones using RSD Lite (windows only app) running in VirtualBox. So I'm guessing if you can install the required USB drivers and flash firmware to USB connected phone, you can pretty much do anything with USB? I'm going to try my luck setting it up now.

---

