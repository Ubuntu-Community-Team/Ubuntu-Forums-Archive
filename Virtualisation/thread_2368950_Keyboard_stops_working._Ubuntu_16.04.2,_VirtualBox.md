---
title: "Keyboard stops working. Ubuntu 16.04.2, VirtualBox"
date: 2017-08-17
forum: Virtualisation
---

### Post by pavlo.m on 2017-08-17
I have Ubuntu 16.04.2 guest running inside of VirtualBox 5.1.26

My hardware is Dell Laptop and I use additional keyboard and mouse with it (They are very usual with USB connection).
**Dell laptop Inspiron 15 7000**. [http://www.dell.com/en-us/member/shop/p](http://www.dell.com/en-us/member/shop/p) ... /fncwf512s. I ugraded RAM only so now it is 32GB.
Keyboard shown in lsusb -v as:
[B]Bus 001 Device 004: ID 1a2c:2124 China Resource Semico Co., Ltd 
[/B]
I usually work over RDP (VirtualBox RDP Server + Windows 7 mstsc.exe RDP client) with this Ubuntu guest.

The issue is keyboard stops work in Ubuntu guest. This mean I can press any key without effect. Mouse works fine and I able to send the shutdown command to within Ubuntu GUI. Also I can use screen keyboard. Problem persists until Ubuntu guest restart. This never happen immediately after Ubuntu start, but can happen after a few hours randomly.

 When keyboard stops work in RDP session I tried to show VM on host PC and keyboard not works there either. I tried to manually attach USB keyboard connected to my Host in VirtualBox (menu Devices - USB - China resource Semico Co., Ltd USB keyboard. ) and see USB attached keyboard starts working, but the laptop native keyboard still not works.

What else I tried:

[LIST]
[*]Turn off usb controller in VirtualBox, but this not help. 
[*]Solution from here:  [https://askubuntu.com/questions/945245/keyboard-stops-working-ubuntu-16-04-2-virtualbox](https://askubuntu.com/questions/945245/keyboard-stops-working-ubuntu-16-04-2-virtualbox). I put echo -1 > /sys/module/usbcore/parameters/autosuspend to rc.local but it not works either. 
[*]I asked on VirtualBox forum, but it looks they do not have any more ideas about this [https://forums.virtualbox.org/viewtopic.php?f=6&t=84202](https://forums.virtualbox.org/viewtopic.php?f=6&t=84202) 
[/LIST]

Please help to find what the problem is and how to solve it? Is it possible to remount keyboard while in RDP session?

---

### Post by deadflowr on 2017-08-17
*Thread moved to **Virtualization ***

---

### Post by ajgreeny on 2017-08-17
If you move out of fullscreen in the guest which you may have to set somehow without using the keyboard, and I'm not sure how you do that, you may find that the keyboard is not selected in the Devices ->USB menu.

---

### Post by pavlo.m on 2017-08-21
Once after fresh reboot keyboard works fine, but in Devices -> USB there is no any devices selected. All other things you mentioned I already did and described results in my initial post.

---

