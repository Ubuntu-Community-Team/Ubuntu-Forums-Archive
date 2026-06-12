---
title: "Installing Ubuntu as a persistent os within virtualbox on a USB"
date: 2018-04-28
forum: Virtualisation
---

### Post by frank72 on 2018-04-28
Hello guys I'm really hoping someone here can help. I've been trying to accomplish this for a few days but cant overcome this last hurdle...

I'm trying to run a guest operating system from within a Ubuntu persistent usb using virtualbox that is also persistent. I realize this sounds  redundant and useless but theres a reason behind the madness. 

I've successfully created a persistent ubuntu usb using mkusb. (for anyone struggling with persistent configurations using mkusb a straight install with persistence works fine but you cant add persistence to the boot menu because that partition is read only. however hitting the " e " button at the boot menu allows u to insert the word persistent into the boot command  just before the --- with a space before it.

Anyway, Whenever I try to install a os (ubuntu debian, etc... It hangs at a certain point.
There is plenty of room allocated and I've followed numerous tutorials along the way but all to no avail.
I can run these os from usb within virtualbox but haven&#8217;t yet  been able to create a persistent one....

Anyone out there have any ideas?

Thanx guys

EDDIT:ADDED: I can run appliances like .ova persistently no problem...

---

### Post by C.S.Cameron on 2018-04-29
For mkusb, partition 2 is the boot partition and contains grub.cfg which contains the "persistent" command. Mkusb makes a great persistent flash drive.
Just spec persistent when creating the drive.

---

