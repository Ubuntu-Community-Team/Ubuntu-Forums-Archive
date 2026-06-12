---
title: "Is it at all possible to do this?"
date: 2006-11-17
forum: The Cafe
---

### Post by PrimoTurbo on 2006-11-17
I'm sure many people here dual boot between Ubuntu & Windows XP, let's say you wanted to use something in Windows for whatever reason. You have two solutions, install Windows in a virtual machine or boot into Windows.

However, since you already have Windows on a seperate partition/drive would it not then be possible to some how emulate the existing Windows XP?

You would then be able to use Windows XP, save space as you don't need to use VM, have a familar setup, save time booting into Windows.

Has anyone done anything like this?

---

### Post by hizaguchi on 2006-11-17
You can do the opposite with coLinux.  It lets you run the 2 systems together with full functionality of both (requring a little tinkering), but you have to start out with Windows so you can't just be using it when you need it.

---

### Post by PrimoTurbo on 2006-11-17
I have heard about CoLinux before but it's not what I mean because I would like to use Windows quickly under certain situations. Especially if I could manage to run Photoshop CS2.

---

### Post by mips on 2006-11-17
I'm not sure about this but I think you can make an image of your windows partition and load it as a vmware image.

I'm taking a stab at it, I have never done this and would not know how to do it.

Have a look at VMWare Server.

Found this, 
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

---

### Post by zachtib on 2006-11-17
> **PrimoTurbo said:**
> I'm sure many people here dual boot between Ubuntu & Windows XP, let's say you wanted to use something in Windows for whatever reason. You have two solutions, install Windows in a virtual machine or boot into Windows.

However, since you already have Windows on a seperate partition/drive would it not then be possible to some how emulate the existing Windows XP?

You would then be able to use Windows XP, save space as you don't need to use VM, have a familar setup, save time booting into Windows.

Has anyone done anything like this?

vmware allows you to pick a directory to use as a disk rather than a disk image, so in theory, you could mount your windows partition under /mnt/windows and point your virtual machine's harddrive to /mnt/windows as well and accomplish exactly what you were asking.

The last time I checked, this functionality was labeled something like "for advanced users" or somesuch, so be careful with what you do.  I'd also imagine that Windows may have to be on a fat32 drive (which I always do anyways on the rare occasion that I dual boot), as I'm not sure if VMware is writing to the partition directly, or passing the read/writes through the main OS (Linux)

---

### Post by adam.tropics on 2006-11-17
You can use VMware with a physical partition, ie your windows install, but it can cause all sorts of drama, to do with hardware profiles. The point being your Windows install upon starting, would expect to find a certain hardware set of resources, not find them, since they are obviously at that point being shared, and give up. If you google, there are ways around it, but to be honest, it's really not worth the drama. If you need windows stuff, and are stuck with a single computer, dual boot.

---

