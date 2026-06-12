---
title: "Mount partition as VirtualBox virtual hard disk"
date: 2011-10-05
forum: Virtualisation
---

### Post by solid.aqua on 2011-10-05
Hi, I am new here. I searched the forum before posting that, and I not really sure that the answer isn't here somewere. If this has been reposted/answered elsewere, this thread can be deleted.
**My question.** 
Suppose I have a PC with dualboot ubuntu and Windows 7. Is it possible, when in ubuntu, to "mount" the partition of Windows 7 as the Virtual hard disk that VirtualBox needs, so I can access my Windows 7 workspace without restarting?
If this is possible, how would the Windows OS react, when on reboot, it realizes that changes have been made on the drive by something other than itself?
The question originates from this dilemma; I want to be able to test simple things such as apps or other stuff on windows without rebooting, but I also want to be able to run some games and DAWs on Windows, which is quite impossible, or so I read, through Virtual machines.
The alternative is that I have two instances of Windows 7, one regular and one virtual, but this seems like a hassle. As a secondary question, are there alternatives to dual-booting?
Thanks a lot.

---

### Post by lcman on 2011-10-06
> **solid.aqua said:**
> Hi, I am new here. I searched the forum before posting that, and I not really sure that the answer isn't here somewere. If this has been reposted/answered elsewere, this thread can be deleted.
**My question.** 
Suppose I have a PC with dualboot ubuntu and Windows 7. Is it possible, when in ubuntu, to "mount" the partition of Windows 7 as the Virtual hard disk that VirtualBox needs, so I can access my Windows 7 workspace without restarting?
If this is possible, how would the Windows OS react, when on reboot, it realizes that changes have been made on the drive by something other than itself?
The question originates from this dilemma; I want to be able to test simple things such as apps or other stuff on windows without rebooting, but I also want to be able to run some games and DAWs on Windows, which is quite impossible, or so I read, through Virtual machines.
The alternative is that I have two instances of Windows 7, one regular and one virtual, but this seems like a hassle. As a secondary question, are there alternatives to dual-booting?
Thanks a lot.

Windows kernel isn't very dynamic, that is, once you install it on one type of hardware, you can't freely move it to other hardware. Unlike linux of course!

However, it is possible to turn your windows installation into a virtual machine by tweaking a little bit. However, it is not guaranteed to work and can break the windows kernel, so, make a backup first.

Here's a tutorial:
```
https://www.virtualbox.org/wiki/Migrate_Windows
```

---

### Post by haqking on 2011-10-06
> **solid.aqua said:**
> Hi, I am new here. I searched the forum before posting that, and I not really sure that the answer isn't here somewere. If this has been reposted/answered elsewere, this thread can be deleted.
**My question.** 
Suppose I have a PC with dualboot ubuntu and Windows 7. Is it possible, when in ubuntu, to "mount" the partition of Windows 7 as the Virtual hard disk that VirtualBox needs, so I can access my Windows 7 workspace without restarting?
If this is possible, how would the Windows OS react, when on reboot, it realizes that changes have been made on the drive by something other than itself?
The question originates from this dilemma; I want to be able to test simple things such as apps or other stuff on windows without rebooting, but I also want to be able to run some games and DAWs on Windows, which is quite impossible, or so I read, through Virtual machines.
The alternative is that I have two instances of Windows 7, one regular and one virtual, but this seems like a hassle. As a secondary question, are there alternatives to dual-booting?
Thanks a lot.

It is possible but not recommended.

I would recommend cloning your partition using clonezilla and then cloning it back into a virtual machine instead.

Alot safer and you also have a backup of your partition at the same time ;-)

The alternative to dual booting is virtualisation, or using Wine,crossover etc to run .exe.  I personally prefer virtualisation.

---

### Post by solid.aqua on 2011-10-06
> **haqking said:**
> It is possible but not recommended.

I would recommend cloning your partition using clonezilla and then cloning it back into a virtual machine instead.

Alot safer and you also have a backup of your partition at the same time ;-)

The alternative to dual booting is virtualisation, or using Wine,crossover etc to run .exe.  I personally prefer virtualisation.

How is it possible?
And if I have two instances of windows, what happens with their licences?

---

### Post by haqking on 2011-10-06
> **solid.aqua said:**
> How is it possible?
And if I have two instances of windows, what happens with their licences?

HOWTO: [https://forums.virtualbox.org/viewtopic.php?t=9697](https://forums.virtualbox.org/viewtopic.php?t=9697)
[http://lifehacker.com/278015/turn-a-windows-partition-into-a-virtual-machine](http://lifehacker.com/278015/turn-a-windows-partition-into-a-virtual-machine)
[http://www.rajatarya.com/website/taming-windows-virtualbox-vm](http://www.rajatarya.com/website/taming-windows-virtualbox-vm)

Your VM would be a backup of your installation however you may need to reactivate using the menu provided

---

### Post by solid.aqua on 2011-10-06
> **haqking said:**
> HOWTO: [https://forums.virtualbox.org/viewtopic.php?t=9697](https://forums.virtualbox.org/viewtopic.php?t=9697)
[http://lifehacker.com/278015/turn-a-windows-partition-into-a-virtual-machine](http://lifehacker.com/278015/turn-a-windows-partition-into-a-virtual-machine)
[http://www.rajatarya.com/website/taming-windows-virtualbox-vm](http://www.rajatarya.com/website/taming-windows-virtualbox-vm)

Your VM would be a backup of your installation however you may need to reactivate using the menu provided

That's what I was looking for. Thanks a lot.

---

