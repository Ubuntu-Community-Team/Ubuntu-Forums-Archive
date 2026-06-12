---
title: "USB not recognized by VirtualBox"
date: 2009-05-05
forum: Virtualisation
---

### Post by kakarotman on 2009-05-05
I installed windows xp on virtual box and it does not recognize any sort of usb connection so if someone could give me a step by step instructions to make it work that would be awsome.

---

### Post by DGortze380 on 2009-05-05
> **kakarotman said:**
> I installed windows xp on virtual box and it does not recognize any sort of usb connection so if someone could give me a step by step instructions to make it work that would be awsome.

Plug in the USB Device
In the Settings -> USB Menu for your VM
Add a Filter for your USB Device
Unmount the device from the Host, don't remove it
Start the VM, and Active the USB Device Via the Menu at the top of the VM Window

---

### Post by dcstar on 2009-05-05
> **kakarotman said:**
> I installed windows xp on virtual box and it does not recognize any sort of usb connection so if someone could give me a step by step instructions to make it work that would be awsome.

Step by step instructions - along with many other Virtualization things - are already in the Virtualization forum.

---

### Post by bodhi.zazen on 2009-05-05
> **dcstar said:**
> Step by step instructions - along with many other Virtualization things - are already in the Virtualization forum.

Indeed ;)

If you are having difficulty, please tell us what version of VirtualBox you are using (PUEL ? OSE?) and what yoou have done to investigate the "problem".

---

### Post by kakarotman on 2009-05-05
I am using ose.

What do you mean by "add a filter for your usb device"?

---

### Post by bodhi.zazen on 2009-05-05
USB devices work with the PUEL edition. 

With OSE you can use a network share protocol (samba) or install the PUEL edition or use KVM.

---

