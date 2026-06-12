---
title: "convert a vmware .vmdk file to an .iso?"
date: 2008-10-02
forum: Virtualisation
---

### Post by N00b-un-2 on 2008-10-02
I have both VirtualBox and VMWare on my Ubuntu Hardy install.  Without saying anything incriminating, let's just say for example that I have a copy of Windows XP installed via VirtualBox and it works great.  I also have *another* OS on my computer that I have the .vmdk image file for.  I'm wondering if there is some way to convert either the .vmdk to an .iso, or if it's possible to batch out the entire virtual machine to an .iso that's bootable in Virtualbox.  I'm not a big fan of VMWare, and I really prefer to use VirtualBox.
As far as *which* operating system I'm referring to, let's just say that it's not Windows and it's not a Linux distro either, and it's not technically supposed to be possible to install it on anything but the brand of computer it came on.  And let's just say that the build model name is a type of large feline animal.  PM me if you'd like me to clarify any further... or tell you how.

---

### Post by chungy on 2008-10-02
First off, ".iso" usually refers to CD images, and what you're asking for simply isn't the way to go.

Secondly, VirtualBox supports VMDK images itself (and now, it supports VirtualPC's VHD images too).

---

### Post by N00b-un-2 on 2008-10-02
I tried to mount the .vmdk file and it didn't work.  I just got a "Fatal Error, no bootable media!" message and it doesn't boot.

---

### Post by Morten ML on 2009-03-29
Don't know if this is still relavant but i have an answer for why the vmdk image wont boot on virtualbox:
First of all the info is from this site so dont thank me:
[http://dietrichschroff.blogspot.com/2008/10/using-vmware-images-with-virtualbox.html](http://dietrichschroff.blogspot.com/2008/10/using-vmware-images-with-virtualbox.html)

basically it says that virtualbox uses IDE hardrives or something like that and that Vmware uses scsi... in the link there is a describtion of how to get your vmdk to work with virtualbox, but it requires that the vmdk file can be modified (by vmwareserver first)

---

### Post by alonswartz on 2010-02-11
If you're still interested in converting a virtual disk (VMDK or VDI) to an ISO you can distribute, take a look at [http://www.turnkeylinux.org/blog/convert-vm-iso]("http://www.turnkeylinux.org/blog/convert-vm-iso")

Cheers,
Alon Swartz

---

### Post by 2614154 on 2010-03-12
You can use vmdk file, like, for example one that you can obtain with windows xp compatibility mode from windows 7. Once you localize the file all you need to do is to change/transfer rights from system to your account.(system does have rights, not inherit from anything) 
 
You can do it by right-click on proprieties file and than modify advanced permissions if i remember. Once it's done you will be able to move and launch the file with virtualbox. As windows xp compatibility mode come with a licence key, it provide a perfect system for making test/ sandbox programs.

---

